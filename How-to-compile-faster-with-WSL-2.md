_**Note: This is for Windows only**_

The steps on the [Compile-firmware](https://github.com/eried/portapack-mayhem/wiki/Compile-firmware#step-3-prepare-the-docker-container) page work fine for compiling, but you may find it takes around 35 minutes each time.
In this guide I will show you how to get that time down to 2 seconds - 1 minute depending on your hardware.



**Step 1)** Download Ubuntu from the windows store
![image](https://user-images.githubusercontent.com/4393979/159869511-93a97a3c-ca7b-46a7-b3f9-447561b1ebc9.png)

**Step 2)** once its opened open up a windows terminal and run ```wsl -l -v```
![image](https://user-images.githubusercontent.com/4393979/159869583-e649c494-c1e0-4e34-a5b1-c428cb4db763.png)

check it says version 2

If it does not, then run: ```wsl --set-default-version 2``` followed by running ```wsl --set-version Ubuntu 2```

**Step 3)** Once that is done, open the Ubuntu app again (make sure you have set it up so you get to the console in it)

**Step 4)** Go to docker on windows and go to settings -> resources -> WSL Integration

**Step 5)** Toggle Ubuntu on (if its not there, click refresh)

**Step 6)** Open up your windows file explorer ang in the address bar go to ``\\wsl$\``

**Step 7)** navigate to Ubuntu/home/{username}/

**Step 8)** copy your portapack-mayhem folder into your dir above

**Step 9)** Confirm your Ubuntu WSL instance can see it by going  ```cd ~/portapack-mayhem```

**Step 10)** If its there then you are good to go. Time to run docker ```docker run -it -v ~/portapack-mayhem:/havoc portapack-dev```

**Step 11)** Profit! It should be compiling super fast now!

You can then set a network share up to your ```\\wsl$\Ubuntu\home\{username}\portapack-mayhem``` folder and continue to edit the files from within windows.

## Errors While Compiling?
If there were errors in the compiling aspect you can follow these steps.

After Step 5 do this:

**Step 5.1)** Open Ubuntu 

![image](https://user-images.githubusercontent.com/120348698/208135792-cb7ce5a0-69d8-4f7f-badf-e85e23e7979b.png)

**Step 5.2)**  Do a sudo git clone --recurse-submodules `sudo git clone --recurse-submodules https://github.com/eried/portapack-mayhem.git`

![image](https://user-images.githubusercontent.com/120348698/208136532-cf06e226-adac-4f3e-a88a-fae287f82b7c.png)

**Step 5.3)** Give permission for the portapack-mayhem directory to your user
1. Run command `whoami`
2. Run command `sudo chown -R my_user:my_usergroup /home/{username}/portapack-mayhem` (Note: Replace "my_user:my_usergroup" with the return from `"whoami"`)

![image](https://user-images.githubusercontent.com/120348698/208140076-18e8fa05-e461-4e75-a41e-e49998cb0ee5.png)

**Step 5.4)** Create "build" folder
1. Run command `cd portapack-mayhem` 
2. Run command `ls` (Note how there's no build folder)
3. Run command `mkdir build`
4. Run command `ls` (Note how a build folder is present)

![image](https://user-images.githubusercontent.com/120348698/208140822-8b8885f0-4e5e-43e5-a58b-608a2748134f.png)

## Prerequisites for Compiling 
**Step 5.5)** Prevent `'python/r' not found` error
1. Run command `git config --global core.autocrlf false`.

Or omit the `false` to see it's status.

![image](https://user-images.githubusercontent.com/120348698/208141889-dc6c3624-421d-46f3-83b4-30dffcd8c638.png)

## Compile
**Step 5.6)** 

1. Run command `docker build -t portapack-dev -f dockerfile-nogit .`
2. Run command `docker run -it -v ~/portapack-mayhem:/havoc portapack-dev`

![image](https://user-images.githubusercontent.com/120348698/208147260-a4f1c98a-4881-493a-8f17-1942353bb826.png)

![image](https://user-images.githubusercontent.com/120348698/208147358-85442b57-a2de-47e3-8d0e-23dd1df352f1.png)

### Duration of the first compiling / building phase
On my system it took 8 minutes, and 43 seconds to complete, this would vary based on your system's hardware and configurations 

![image](https://user-images.githubusercontent.com/120348698/208148594-9014ef39-4afe-4b75-866d-24a448797802.png)

### Duration of the second compiling / building phase
On the second compile, I made changes on the "ui_geomap.cpp" & "ui_geomap.hpp". These were no more that 25 lines of changes made collectively. And this was compiled in 3 seconds on my system.  

![image](https://user-images.githubusercontent.com/120348698/208150352-6bf5d73b-8329-4421-b783-796a2d36f359.png)
