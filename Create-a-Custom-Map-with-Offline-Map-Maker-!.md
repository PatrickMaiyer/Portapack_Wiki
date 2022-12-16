This is guide to create a custom map for your PortaPack and NOT a custom map with special details. 

## Who is this for?
This may be useful to you if you find your area/region to be small or unclear.

## Steps to create this custom map using Offline Map Maker :
1. Download Offline Map Maker via it's official website: https://www.allmapsoft.com/omm/index.html or by clicking this [link](https://www.allmapsoft.com/omm/download/omm_setup.exe)
2. After running the install you would do the following:

![image](https://user-images.githubusercontent.com/120348698/207945316-083ba213-07fa-49a4-8ba5-7e9283fbb758.png)

 1. Select a Maps type in the left tree
 2. Enter a task name, such like "newtask.omm".
 3. Define the zoom level scope. (Since we want the best clarity we would go with the highest zoom which is 13 in the free version, paid is 19. But 
    please note that higher zoom means bigger file size) 
 4. directly input 4 parameters (Left Longitude, Right Longitude, Top Latitude, Bottom Latitude) to define the area scope of images that you want to 
    download See [here](https://www.allmapsoft.com/omm/support.htm#kml)  for uploading a KML file type)
 5.  Select a path to save the project and downloaded images.
 6. Then click button "Start".

### Combine Downloaded Tiles/Images
![image](https://user-images.githubusercontent.com/120348698/207948724-23ef82f4-f9a1-4505-a35e-4c11f209a34a.png)

 7. After having a successful download, you would want to navigate to "Tools"-->"Map Combiner" where you would be greeted by a similar image:
![image](https://user-images.githubusercontent.com/120348698/207950077-4bc2ef6a-676c-4943-80fd-799c7fd15cf0.png)
     1. Open the location of where your file was downloaded (Ensure "Create a JPEG file" is checked and your selected zoom should appear by default if 
        not, do select).
     2. Then click "Combine" 

For a more detailed set of instructions vest the official [website](https://www.allmapsoft.com/omm/support.htm)

## Lastly
Upon the successful downloading and combining of your custom map refer to the following steps:
 1. Rename your combined image to world_map.jpg
 2. Place the input map in: sdcard/ADSB/world_map.jpg 
 3. Then run firmware/tools/generate_world_map.bin.py. Where your map will be generated on: sdcard/ADSB/world_map.bin  
 4. Place the generated .bin file in the respective folder of your SD Card (ADSB/world_map.bin)

## Keynotes 
* Ensure you have Python installed (I have Python 3.10)
* And the package "Pillow" installed (`pip install Pillow`)

## Coding 
To see your actual custom map, you need to do a change/edit of code. This change would occur in line 197 of file ui_geomap.cpp which is located at /firmware/application/ui/ or [here](https://github.com/eried/portapack-mayhem/blob/f161e85f960cff0c166173f4f7a4244b8c625375/firmware/application/ui/ui_geomap.cpp#L197) for ease of reference. The function that's being changed is `void GeoMap::move(const float lon, const float lat)`. 

What I replaced this function with is as follow: 

`
void GeoMap::move(const float lon, const float lat) {

	lon_ = lon;
	lat_ = lat;
	
	// Enter Map Coordinates Accordingly
	double mapLeftLon = 79.14; 
	double mapRightLon = 81.89;

	double mapLonDelta = mapRightLon - mapLeftLon;

	double mapBottomLat = 5.86; 

	double mapBottomLatDegree = mapBottomLat * pi / 180;

	Rect map_rect = screen_rect();
	
	// Using WGS 84/Pseudo-Mercator projection
	// x_pos = map_width * (lon_+180)/360  - (map_rect.width() / 2); 
	x_pos = (lon_ - mapLeftLon) * (map_width / mapLonDelta) - (map_rect.width() / 2);

	// Latitude calculation based on https://stackoverflow.com/a/10401734/2278659
	// double map_bottom = sin(-85.05 * pi / 180); // Map bitmap only goes from about -85 to 85 lat
	// double lat_rad = sin(lat * pi / 180);
	double lat_rad = lat_ * pi / 180;
	// double map_world_lon = map_width / (2 * pi);
	double map_world_lon = ((map_width / mapLonDelta) * 360) / (2 * pi); 
    // double map_offset = (map_world_lon / 2 * log((1 + map_bottom) / (1 - map_bottom)));
	double map_offset = (map_world_lon / 2 * log((1 + sin(mapBottomLatDegree)) / (1 - sin(mapBottomLatDegree))));
	// y_pos = map_height - ((map_world_lon / 2 * log((1 + lat_rad) / (1 - lat_rad))) - map_offset) - 128; // Offset added for the GUI
	y_pos = map_height - ((map_world_lon / 2 * log((1 + sin(lat_rad)) / (1 - sin (lat_rad)))) - map_offset); // Offset added for the GUI

	// Cap position
	if (x_pos > (map_width - map_rect.width()))
		x_pos = map_width - map_rect.width();
	if (y_pos > (map_height + map_rect.height()))
		y_pos = map_height - map_rect.height();
}`

What ever code is commented out was the original code. I tried my best to make this plug and go but I'm certain that, that will not be the case for some. In my testing with this code that I've uploaded here, It seems that my projections are off by 2-300 ft. Which is not bad since I couldn't even differentiate if the calculations were even off at the beginning.

## Breakdown of Code
I also tried my best to make the code input variables self explanatory. But for those who are new and those who willing to give this code a shot, all that is required of you is to:
1. Enter your mapLeftLon, which is your "Left Longitude" 
2. Enter your mapRightLon, which is your "Right Longitude"
3. And enter your mapBottomLat, which is your "Bottom Latitude"
These values are the ones you entered / KML uploaded at step 4 at section "Steps to create this custom map using Offline Map Maker". Also Note if your KML file has a lot of decimal points you should enter those exactly since I never tested a round off value but that doesn't mean you should too. 