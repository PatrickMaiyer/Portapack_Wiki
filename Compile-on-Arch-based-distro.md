# 1. Install dependence
``
sudo pacman -S git tar wget dfu-util cmake python3 bzip2 lz4 curl hackrf python-distutils-extra python-setuptools python-pip python-yaml
``

Check the output and make sure are the packages listed above were installed correctly.

# 2. Install ARM `gcc-arm-none-eabi` package from `AUR`

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
>Note that since the SSL certificate of the file this ``makepkg`` pointed to already expired, the `curl` wouldn't install it correctly, thus, you have to add `-k` argument to your `makepkg.conf`:  
`sudo vim /etc/makepkg.conf`  
Edit the line   
`'https::/usr/bin/curl -qgb "" -fLC - --retry 3 --retry-delay 3 -o %o %u'`  
to  
`'https::/usr/bin/curl -qgb "" -fLC - --retry 3 --retry-delay 3 -k -o %o %u'`  
(You may change it back after installing, if you needed)  
Then `makepkg`, waiting it finished.  
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
There should be no more bugs anymore. 

# Notes
1. You cannot directly install `gcc-arm-none-eabi` from AUR using yay or others tool, otherwise the version would be not match.  
2. After installing `gcc-arm-none-eabi` you may change the `makepkg.conf` back:
>`sudo vim /etc/makepkg.conf`  
Edit the line   
`'https::/usr/bin/curl -qgb "" -fLC - --retry 3 --retry-delay 3 -k -o %o %u'`  
to  
`'https::/usr/bin/curl -qgb "" -fLC - --retry 3 --retry-delay 3 -o %o %u'`  




 