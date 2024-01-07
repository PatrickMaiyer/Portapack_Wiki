For this we are using clang format version 13. All the config for this is in the .clang-format file. Your IDE should automatically pick up on this when you format your code.

## VS Code
Make sure you have C/C++ extension by Microsoft installed and it should automatically pick up your .clang-format file. If not, you can go to the extension settings and specify the location under the `Clang_format_style` setting

## CLI
To format using CLI, make sure you have clang-format-13 installed

```
wget https://apt.llvm.org/llvm.sh
chmod +x llvm.sh
sudo ./llvm.sh 13
sudo apt install clang-format-13
```

Then you can run
```
find firmware/common firmware/baseband firmware/application -iname '*.h' -o -iname '*.hpp' -o -iname '*.cpp' -o -iname '*.c' | xargs clang-format-13 -style=file -i
```
or individually:
```
find firmware/common -iname '*.h' -o -iname '*.hpp' -o -iname '*.cpp' -o -iname '*.c' | xargs clang-format-13 -style=file -i
find firmware/baseband -iname '*.h' -o -iname '*.hpp' -o -iname '*.cpp' -o -iname '*.c' | xargs clang-format-13 -style=file -i
find firmware/application -iname '*.h' -o -iname '*.hpp' -o -iname '*.cpp' -o -iname '*.c' | xargs clang-format-13 -style=file -i
```



## CLion
CLion has built in clang-format, just press Ctrl + Shift + L (Windows and Linux) to format the code with ``.clang-format`` configure file within project directory. If you have clang-tidy or so enabled, you need to disable them.    
Note: KDE default keymap is Alt + Shift + L