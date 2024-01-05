## About

Reading and writing to the SD card is a great way for your application to save progress or reference data that might be to too large to fit in the firmware. Below are examples on how to interface with the SD card using the Mayhem code base.

## File Class

Most of the heavy lifting for working with files on the SD Card is done by the [File](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/file.cpp) class. This helper class which simplifies the `FatFs - Generic FAT file system module` which can found at [`firmware/chibios-portapack/ext/fatfs/src/ff.c`](https://github.com/eried/portapack-mayhem/blob/next/firmware/chibios-portapack/ext/fatfs/src/ff.c). This wiki will go over some examples on how to read and write files to the SD card.

Continuing with the [Create a Simple App](Create-a-simple-app) the code bellow will outline what is required to manipulate the file system. The first thing you'll need to do is include the File class and SD Card helper functions to your application's hpp file. 

#### ui_newapp.hpp
```
// Add these to include File Class and SD Card helper functions.
#include "file.hpp" 
#include "sd_card.hpp"
```

### Check SD Card

Before reading and writing from the SD Card it's ideal to do a quick check to see if the SD card is mounted. There is error handing working in the background that keeps things from crashing however this will give people a better idea if there's a problem or not. The function below dose a quick check to see if the SD Card is showing a status of "Mounted". This will return true if sd_card::status() returns "Mounted" or false if sd_card::status() returns any other status. SD Card statuses are defined in [firmware/application/sd_card.hpp](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/sd_card.hpp).    


#### ui_newapp.cpp
```
// Checks SD Card, returns true if Mounted, false if otherwise
bool NewAppView::check_sd_card() {
    return (sd_card::status() == sd_card::Status::Mounted) ? true : false; 
}
```

Below is a quick example on how this error check could be used. 
#### ui_newapp.cpp
```
// Check SD Card
if(check_sd_card()) {                                       // Check to see if SD Card is mounted
    // Logic if SD Card is mounted 
} else {                                                    // Else, check_sd_card() returned false 
    // Logic if SD Card is NOT mounted
}
```

### List Directory Contents

To make things easier to use we're going to use a method from [firmware/application/apps/ui_fileman.cpp](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/apps/ui_fileman.cpp) to list the contents of the SD Card. First thing we'll need to do is create a Struct that outlines the pertinent information of files and directories. Each struct will include the file path, size, and if the item is a directory or not.  

#### ui_newapp.hpp
```
// Struct that outlines file information
struct file_entry {
    std::filesystem::path entry_path { };
    uint32_t size { };
    bool is_directory { };
};
```

Below is an function that will return a [Vector](https://www.geeksforgeeks.org/vector-in-cpp-stl/) (simmer to a list) of `file_entry` Struts. The input for this function needs a `std::filesystem::path` which can be `UTF-16 string literal`. The root of the SD Card is `u""` and any directory beyond that is `u"DIRECTORY/SUB_DIRECTORY"`. 

This function will also place any directories at the front of the Vector and files in the back. This will also skip any files that are hidden as in anything with a `.` in front of the file name.     

#### ui_newapp.cpp
```
// Lists all files and directories in path
std::vector<file_entry> NewAppView::list_dir(const std::filesystem::path& path) {

    // Files and directories list
    std::vector<file_entry> entry_list { };

    // For each entry in the file system's directory
    // Adds files in directories into entry_list{} 
    // Directories are inserted in front of files
    for (const auto& entry : std::filesystem::directory_iterator(path, u"*")) {

        // Dose not add directorys or files starting with '.' (hidden / tmp)
        if (entry.path().string().length() && entry.path().filename().string()[0] != '.') {

            // If file 
            if (std::filesystem::is_regular_file(entry.status())) {
                entry_list.push_back({ entry.path(), (uint32_t)entry.size(), false });

            // Else If directory    
            } else if (std::filesystem::is_directory(entry.status())) {
                entry_list.insert(entry_list.begin(), { entry.path(), 0, true });
            
            // Other
            } else {
                continue;
            }
        }

    }
    return entry_list;
}
```

### Create Directory

To create a directory we can use the `make_new_directory()` function from [File](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/file.cpp). The helper function below will return true if `make_new_directory()` succeeds (Success from `make_new_directory()` returns a 0, other values means failure) and takes two variable inputs for file path and directory name. Again the input for the file path is a `std::filesystem::path` which can be `UTF-16 string literal`. The root of the SD Card is `u""` and any directory beyond that is `u"DIRECTORY/SUB_DIRECTORY"`.      

#### ui_newapp.cpp
```
// Creates dir, returns true if successful 
bool NewAppView::create_dir(const std::filesystem::path& path, std::string name) {  // make_new_directory() returns 0 for success
    return !(make_new_directory(path.string() + "/" + name));                       // and other values means failure. Not operation  
}                                                                                   // will return true only when 0 is returned. 
```

Below is an example on how the `create_dir()` function can be used with basic error handling.  

#### ui_newapp.cpp
```
// New directory
if(check_sd_card()) {                     // Check to see if SD Card is mounted
    if(create_dir(u"", "NEW_DIR")) {      // New dir in root of SD Card, returns true if successful
        // Logic if new dir succeeded 
    } else {
        // Logic else new dir failed
    } 
} else {                                  // Else, check_sd_card() returned false
    // Logic else SD Card is NOT mounted
}
```  

### Create File

To create a file we can use the `create()` function from [File](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/file.cpp) class. The helper function below will return true if `create()` succeeds (Success from `create()` returns a 0, other values means failure) and takes two variable inputs for file path and directory name. Again the input for the file path is a `std::filesystem::path` which can be `UTF-16 string literal`. The root of the SD Card is `u""` and any directory beyond that is `u"DIRECTORY/SUB_DIRECTORY"`.  

#### ui_newapp.cpp
```
bool NewAppView::create_file(const std::filesystem::path& path, std::string name) {
    File file = { };                                                                // Create File object
    Optional<File::Error> sucess = file.create(path.string() + "/" + name);         // Create File
    return !(sucess.is_valid());                                                    // 0 is success
}
```

Below is an example on how the `create_file()` function can be used with basic error handling.  

#### ui_newapp.cpp
```
// New file
if(check_sd_card()) {                       // Check to see if SD Card is mounted
    if(create_file(u"", "NEW_FILE.txt")) {  // New file in root of SD Card, returns true if successful
        // Logic if new file succeeded 
    } else {
        // Logic else new file failed
    } 
} else {                                    // Else, check_sd_card() returned false
    // Logic else SD Card is NOT mounted
}
```

## A word about reading and writing

In both mode a hardware limit is preventing any buffered read higher than blocks of 512 to be read or write

**!! While you can and will do buffered read/write, the size of the buffer must not be higher than 512 !!**

See the [related issue discussion](https://github.com/eried/portapack-mayhem/issues/1103)


### Read File   

To read to a file the `read_file()` function from the [File](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/file.cpp) class can be used. The helper function below will return true if the class object `File` opens the file successfully. Success from this open function will have a `is_valid()` function which will return a 0, other values means failure. Inputs for file path and directory name. Again the input for the file path is a `std::filesystem::path` which can be `UTF-16 string literal`. The root of the SD Card is `u""` and any directory beyond that is `u"DIRECTORY/SUB_DIRECTORY"` 

**Note: The below sample code dose not handle large files, memory management needs to be implemented.**

#### ui_newapp.cpp
```
std::string NewAppView::read_file(const std::filesystem::path& path, std::string name) { // Read file
    std::string return_string = "";                                                      // String to be returned
    File file;                                                                           // Create File object
    auto success = file.open(path.string() + "/" + name);                                // Open file to write

    if(!success.is_valid()) {                                                            // 0 is success
        char one_char[1];                                                                // Read file char by char
        for(size_t pointer = 0; pointer < file.size() ; pointer++) {                     // Example won't work for large files
            file.seek(pointer);                                                          // Sets file to next pointer
            file.read(one_char, 1);                                                      // sets char to one_char[]
            return_string += one_char[0];				                 // Add it to the return_string               
        }
    } else {
        return "0";                                                                      // Basic error handling
    }
    return return_string;
}
```

#### ui_newapp.cpp
```
if(check_sd_card()) {                                        // Check to see if SD Card is mounted
    std::string data = "";                                   // Create output string
    data = read_file(u"", "NEWER_FILE.TXT");                 // read_file()
    if(data != "0") {                                        // Success is anything but 0
        // Logic if data is present
    } else {
        // Logic if there's no data
    }
} else {                                                     // Else, check_sd_card() returned false
    // Logic else SD Card is NOT mounted
}
```

### Write File  

To write to a file the `write_line()` or `write()` function from the [File](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/file.cpp) class can be used. The helper function below will return true if the class object `File` appends to the target file successfully. Success from this append function will have a `is_valid()` function which will return a 0, other values means failure. Inputs for file path and directory name. Again the input for the file path is a `std::filesystem::path` which can be `UTF-16 string literal`. The root of the SD Card is `u""` and any directory beyond that is `u"DIRECTORY/SUB_DIRECTORY"`

#### ui_newapp.cpp
```
bool NewAppView::write_file(const std::filesystem::path& path, std::string name, std::string data) {
    File file;                                                                     // Create File object
    auto sucess = file.append(path.string() + "/" + name);                         // Open file
    if(!sucess.is_valid()) {                                                       // 0 is success
        file.write_line(data);
        return true;
    } else {
        return false;
    }
}
```

#### ui_newapp.cpp
```
if(check_sd_card()) {                                        // Check to see if SD Card is mounted
    std::string data = "Your mother was a hamster!";
    if(write_file(u"", "NEWER_FILE.TXT", data)) {            // Success is anything but 0
        // Logic if write was successful 
    } else {
        // Logic if write failed
    }
} else {                                                     // Else, check_sd_card() returned false
    // Logic else SD Card is NOT mounted
}
```

### Rename File or Directory

To rename a file or directory the `rename_file()` function from [File](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/file.cpp) can be used. The helper function below will return true if `rename_file()` succeeds (Success from `rename_file()` returns a 0, other values means failure) and takes two variable inputs for file path and directory name. Again the input for the file path is a `std::filesystem::path` which can be `UTF-16 string literal`. The root of the SD Card is `u""` and any directory beyond that is `u"DIRECTORY/SUB_DIRECTORY"`

#### ui_newapp.cpp
```
bool NewAppView::rename_dir_or_file(const std::filesystem::path& path, std::string old_name, std::string new_name) {
    return !(rename_file(path.string() + "/" + old_name, new_name));                              // 0 is success
}
```

#### ui_newapp.cpp
```
// Rename directory or file
if(check_sd_card()) {                                       // Check to see if SD Card is mounted
    if(rename_dir_or_file(u"", "NEW_DIR", "NEWER_DIR")) {   // Renames dir or file in root of SD Card, returns true if successful
        // Logic if rename is successful 
    } else {                                                // Else new dir or file renamed failed
        // Logic if rename failed
    }   
} else {                                                    // Else, check_sd_card() returned false
    // Logic else SD Card is NOT mounted
}
```


### Delete File or Directory

To delete a file or directory the `delete_file()` function from [File](https://github.com/eried/portapack-mayhem/blob/next/firmware/application/file.cpp) can be used. The helper function below will return true if `delete_file()` succeeds (Success from `make_new_directory()` returns a 0, other values means failure) and takes two variable inputs for file path and directory name. Again the input for the file path is a `std::filesystem::path` which can be `UTF-16 string literal`. The root of the SD Card is `u""` and any directory beyond that is `u"DIRECTORY/SUB_DIRECTORY"`    

#### ui_newapp.cpp
```
bool NewAppView::delete_dir_or_file(const std::filesystem::path& path, std::string name) {
    return !(delete_file(path.string() + "/" + name));
}
```

Below is an example on how the `delete_dir_or_file()` function can be used with basic error handling. 

#### ui_newapp.cpp
```
if(check_sd_card()) {                                         // Check to see if SD Card is mounted
    if(delete_dir_or_file(u"", "NEW_DIR")) {                  // New dir in root of SD Card
        // Logic if file/dir delete was successful
    } else {
        // Logic if file/dir delete was NOT successful
    }
} else {                                                      // Else, check_sd_card() returned false
    // Logic else SD Card is NOT mounted
}
``` 

## Wrap Up

Below is example demo of all basic CRUD functions for files and directories. 

### ui_newapp.hpp
```
#include "ui.hpp"
#include "ui_widget.hpp"
#include "ui_navigation.hpp"
#include "string_format.hpp"

// Add these to include File Class and SD Card helper functions.
#include "file.hpp" 
#include "sd_card.hpp"

namespace ui
{
    // Struct that outlines file information
    struct file_entry {
        std::filesystem::path entry_path { };
        uint32_t size { };
        bool is_directory { };
    };

    class NewAppView : public View                                // App class declaration
    {
    public:

        // Public declarations
    	void focus() override;                                    // ui::View function override

        NewAppView(NavigationView &nav);                          // App class init function declaration
        std::string title() const override { return "New App"; }; // App title

    private:

        // Function declarations

        // Error check
        bool check_sd_card();

        // DIR CRUD                                            
        bool create_dir(const std::filesystem::path& path, std::string name);
        std::vector<file_entry> list_dir(const std::filesystem::path& path);

        // File CRUD
        bool create_file(const std::filesystem::path& path, std::string name);
        bool rename_dir_or_file(const std::filesystem::path& path, std::string old_name, std::string new_name);
        std::string read_file(const std::filesystem::path& path, std::string name);
        bool write_file(const std::filesystem::path& path, std::string name, std::string data);
        bool delete_dir_or_file(const std::filesystem::path& path, std::string name);


        // Widgets
        Console my_console {
            { 1*8, 1*8, 224, 296 },    // Coordinates are: int:x (px), int:y (px), int:width (px), int:height (px)
        };
    };
} 
```

### ui_newapp.cpp
```
#include "ui_newapp.hpp"
#include "portapack.hpp"
#include <cstring>

using namespace portapack;

namespace ui
{

    void NewAppView::focus() {                               // Default selection to my_console when app starts
	    my_console.focus();
    }
    
    // Checks SD Card, returns true if Mounted, false if otherwise
    bool NewAppView::check_sd_card() {
        return (sd_card::status() == sd_card::Status::Mounted) ? true : false; 
    }

    // Lists all files and directories in path
    std::vector<file_entry> NewAppView::list_dir(const std::filesystem::path& path) {

        // Files and directories list
        std::vector<file_entry> entry_list { };

        // For each entry in the file system's directory
        // Adds files in directorys into entry_list{} 
        // Directorys are inserted infront of files
        for (const auto& entry : std::filesystem::directory_iterator(path, u"*")) {

            // Dose not add directorys or files starting with '.' (hidden / tmp)
            if (entry.path().string().length() && entry.path().filename().string()[0] != '.') {

                // If file 
                if (std::filesystem::is_regular_file(entry.status())) {
                    entry_list.push_back({ entry.path(), (uint32_t)entry.size(), false });

                // Else If directory    
                } else if (std::filesystem::is_directory(entry.status())) {
                    entry_list.insert(entry_list.begin(), { entry.path(), 0, true });
                
                // Other
                } else {
                    continue;
                }
            }

        }
        return entry_list;
    }


    // Creates dir, returns true if successful 
    bool NewAppView::create_dir(const std::filesystem::path& path, std::string name) {  // make_new_directory() returns 0 for success
        return !(make_new_directory(path.string() + "/" + name));                       // and other values means failure. Not operation  
    }                                                                                   // will return true only when 0 is returned. 
                                                                                            

    bool NewAppView::delete_dir_or_file(const std::filesystem::path& path, std::string name) { // Deletes file or dir.
        return !(delete_file(path.string() + "/" + name));                                     // 0 is success.
    }


    bool NewAppView::create_file(const std::filesystem::path& path, std::string name) {
        File file = { };                                                                // Create File object
        Optional<File::Error> sucess = file.create(path.string() + "/" + name);         // Create File
        return !(sucess.is_valid());                                                    // 0 is success
    }


    bool NewAppView::rename_dir_or_file(const std::filesystem::path& path, std::string old_name, std::string new_name) {
        return !(rename_file(path.string() + "/" + old_name, new_name));                              // 0 is success
    }


    std::string NewAppView::read_file(const std::filesystem::path& path, std::string name) { // Read file
        std::string return_string = "";                                                      // String to be returned
        File file;                                                                           // Create File object
        auto sucess = file.open(path.string() + "/" + name);                               // Open file to write

        if(!sucess.is_valid()) {                                                             // 0 is success
            char one_char[1];                                                                // Read file char by char
            for(size_t pointer = 0; pointer < file.size() ; pointer++) {                     // Example won't work for large files
                file.seek(pointer);                                                          // Sets file to next pointer
                file.read(one_char, 1);                                                      // sets char to one_char[]
			    return_string += one_char[0];				                                 // Add it to the return_string               
            }
        } else {
            return "0";                                                                      // Basic error handling
        }
        return return_string;
    }


    bool NewAppView::write_file(const std::filesystem::path& path, std::string name, std::string data) {
        File file;                                                                     // Create File object
        auto success = file.append(path.string() + "/" + name);                        // Open file
        if(!success.is_valid()) {                                                      // 0 is success
            file.write_line(data);
            return true;
        } else {
            return false;
        }
    }


    NewAppView::NewAppView(NavigationView &nav) // Application Main
    {
        add_children({
            &my_console,                        // Add pointers for widgets
        });

        // Enable scrolling
        my_console.enable_scrolling(true);

        // Check SD Card
        if(check_sd_card()) {                                       // Check to see if SD Card is mounted
            my_console.writeln("+ SD Card is Mounted");
        } else {                                                    // Else, check_sd_card() returned false 
            my_console.writeln("- SD Card is NOT Mounted");
        }

        // New directory
        if(check_sd_card()) {                                        // Check to see if SD Card is mounted
            if(create_dir(u"", "NEW_DIR")) {                         // New dir in root of SD Card, returns true if successful
                my_console.writeln("+ New directory created");       // If new dir succeeded 
            } else {
                my_console.writeln("- New directory FAILED");        // Else new dir failed
            } 
        } else {                                                     // Else, check_sd_card() returned false
            my_console.writeln("- New directory FAILED");
        }

        // List Directory
        std::string dir_contents = "";                                   // String var that displays the dir contents
        std::vector<file_entry> files = { };                             // file_entry Vector
        if(check_sd_card()) {                                            // Check to see if SD Card is mounted
            files = list_dir(u"");                                       // dir of SD Card, u"" is root, u"DIRECTORY_NAME" for other directories
                                                                         // Vector has a capacity of 64 objects
            if(files.size()) {                                           // If files are not empty
                dir_contents += "+ dir SD Card: ";
                for (const auto& f : files) {                            // For each f of files
                    dir_contents += f.entry_path.string() + ", ";        // Copy name to dir_contents
                }
            } else {                                                     // Else, files are empty 
                my_console.writeln("- dir SD Card FAILED");              
            }
        } else {                                                         // Else, check_sd_card() returned false
            my_console.writeln("- dir SD Card FAILED");
        }
        //my_console.writeln(dir_contents);                              // Write results to my_console
                                                                         // Write total count to my_console
        my_console.writeln("+ dir SD Card: " + std::to_string(files.size()) + " items"); 

        // Rename directory
        if(check_sd_card()) {                                       // Check to see if SD Card is mounted
            if(rename_dir_or_file(u"", "NEW_DIR", "NEWER_DIR")) {   // Renames dir in root of SD Card, returns true if successful
                my_console.writeln("+ Directory renamed");          // If dir renamed succeeded 
            } else {
                my_console.writeln("- Directory renamed FAILED");   // Else new dir renamed failed
            }   
        } else {                                                    // Else, check_sd_card() returned false
            my_console.writeln("- Directory renamed FAILED");
        }

        // Delete file or directory 
        if(check_sd_card()) {                                         // Check to see if SD Card is mounted
            if(delete_dir_or_file(u"", "NEWER_DIR")) {                // New dir in root of SD Card
                my_console.writeln("+ New directory deleted");
            } else {
                my_console.writeln("- New directory deleted FAILED");
            }
        } else {                                                      // Else, check_sd_card() returned false
            my_console.writeln("- New directory deleted FAILED");
        }

        // New file
        if(check_sd_card()) {                                        // Check to see if SD Card is mounted
            if(create_file(u"", "NEW_FILE.txt")) {                   // New dir in root of SD Card, returns true if successful
                my_console.writeln("+ New file created");            // If new file succeeded 
            } else {
                my_console.writeln("- New file FAILED");             // Else new file failed
            } 
        } else {                                                     // Else, check_sd_card() returned false
            my_console.writeln("- New file FAILED");
        }

        // Rename file
        if(check_sd_card()) {                                               // Check to see if SD Card is mounted
            if(rename_dir_or_file(u"", "NEW_FILE.txt", "NEWER_FILE.TXT")) { // Renames file, returns true if successful
                my_console.writeln("+ File renamed");                       // If file renamed succeeded 
            } else {
                my_console.writeln("- File renamed FAILED");                // Else new file renamed failed
            }   
        } else {                                                            // Else, check_sd_card() returned false
            my_console.writeln("- File renamed FAILED");
        }

        // Write file
        if(check_sd_card()) {                                         // Check to see if SD Card is mounted
            std::string data = "Your mother was a hamster!";
            if(write_file(u"", "NEWER_FILE.TXT", data)) {             // Success is anything but 0
                my_console.writeln("+ Write File");                   // Write data to my_console
            } else {
                my_console.writeln("- Write file FAILED");
            }
        } else {                                                     // Else, check_sd_card() returned false
            my_console.writeln("- Write file FAILED");
        }

        // Read file
        if(check_sd_card()) {                                        // Check to see if SD Card is mounted
            std::string data = "";                                   // Create output string
            data = read_file(u"", "NEWER_FILE.TXT");                 // read_file()
            if(data != "0") {                                        // Success is anything but 0
                my_console.writeln("+ Read file: " + data);          // Write data to my_console
            } else {
                my_console.writeln("- Read file FAILED");
            }
        } else {                                                     // Else, check_sd_card() returned false
            my_console.writeln("- Read file FAILED");
        }

        // Delete file or directory 
        if(check_sd_card()) {                                         // Check to see if SD Card is mounted
            if(delete_dir_or_file(u"", "NEWER_FILE.TXT")) {           // New dir in root of SD Card
                my_console.writeln("+ New file deleted");
            } else {
                my_console.writeln("- New file deleted FAILED");
            }
        } else {                                                      // Else, check_sd_card() returned false
            my_console.writeln("- New file deleted FAILED");
        }

        // Done
        my_console.writeln("+ Demo Complete");

    }
}
```

   