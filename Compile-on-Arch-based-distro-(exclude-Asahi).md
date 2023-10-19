_This page not works on Asahi, please make sure you are on x86_64 platform_
---

# 1. Install dependence
``
sudo pacman -S git tar wget dfu-util cmake make python3 bzip2 lz4 curl hackrf python-distutils-extra python-setuptools python-pip python-yaml
``  

_If you use nushell as your default shell, you need to install `libopencm3`package, otherwise it would call it fail. The best solution is don’t use nushell_    

Check the output and make sure the packages listed above were installed correctly.  

# 2. Install ARM `gcc-arm-none-eabi` package from `AUR`

_you can follow the instructions in [Debian based distro page in this wiki](https://github.com/eried/portapack-mayhem/wiki/Compile-firmware#using-arm-on-debian) as well. This doesn’t work before and it turns out that it’s nushell caused the bug. If you don’t use nushell, you are all good with that set up._

_This will automatically add the path of arm toolchain to the ``PATH`` of your default shell (for example: ``bash``, ``zsh``, ``fish``, and ``nushell``)._

1. Go to [the page of `gcc-arm-none-eabi` package in AUR](https://aur.archlinux.org/packages/gcc-arm-none-eabi-bin).  
2. Click `View Changes` to check the commit history of this AUR package.  
3. Click [version 9-2020-q2](https://aur.archlinux.org/cgit/aur.git/commit/?h=gcc-arm-none-eabi-bin&id=11b618acbed084c37cdf1568a1bc2b05152af7e1) to check the specific version of `gcc-arm-none-eabi`, then click `Download` to download the package for ``makepkg``.  
4. Assuming you download the package to `~`.
5. Create a directory to satisfying and checking the package.
`mkdir AUR`  
6. `mv aur-11b618acbed084c37cdf1568a1bc2b05152af7e1.tar.gz ./AUR`  
7. `cd AUR`
8. `tar -xvf aur-11b618acbed084c37cdf1568a1bc2b05152af7e1.tar.gz`  
9. `cd aur-11b618acbed084c37cdf1568a1bc2b05152af7e1`
10. `makepkg`   
>(ARM already fixed this but in case of it happend again we'll leave it here.)    
~~Note that since the SSL certificate of the file this ``makepkg`` pointed to already expired, the `curl` wouldn't download it correctly, thus, you have to add `-k` argument to your `makepkg.conf`:~~  
~~`sudo vim /etc/makepkg.conf`~~    
~~Edit the line~~     
~~`'https::/usr/bin/curl -qgb "" -fLC - --retry 3 --retry-delay 3 -o %o %u'`~~    
~~to~~    
~~`'https::/usr/bin/curl -qgb "" -fLC - --retry 3 --retry-delay 3 -k -o %o %u'`~~    
~~(You may change it back after installing, if you needed)~~    
~~Then `makepkg`, waiting it finished.~~    
11. Install the package with `pacman`:  
`sudo pacman -U gcc-arm-none-eabi-bin-9_2020_q2_update-1-x86_64.pkg.tar.zst` 

# 3. Clone your repo to local and satisfying the sub-module
```
cd ~
git clone https://github.com/eried/portapack-mayhem.git
cd portapack-mayhem  
git submodule update --init --recursive
```

# 4. Give permission to the repo directory in your local and compile it
```
sudo chown -R my_user:my_usergroup ~/portapack-mayhem
cd ~/portapack-mayhem
mkdir build
cd build
cmake ..
make firmware
```  
If you want, use `-j` argument to increase the compile speed, for example `make -j firmware` to auto decide the number of threads to compile, or manually set the thread numbers, for example `make -j4 firmware`

# Notes
1. You cannot directly install `gcc-arm-none-eabi` from AUR using yay or others tool, otherwise the version would be not match.    


2. (ARM already fixed this but in case of it happend again we'll leave it here.)    
 ~~After installing `gcc-arm-none-eabi` you may change the `makepkg.conf` back:~~  
>~~`sudo vim /etc/makepkg.conf`~~    
~~Edit the line~~     
~~`'https::/usr/bin/curl -qgb "" -fLC - --retry 3 --retry-delay 3 -k -o %o %u'`~~    
~~to~~    
~~`'https::/usr/bin/curl -qgb "" -fLC - --retry 3 --retry-delay 3 -o %o %u'`~~    




 