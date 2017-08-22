[Ubuntu 16.04: Tensorflow 1.2, keras, opencv3, python3, cuda8 and cudnn5.1](https://medium.com/@vivek.yadav/deep-learning-setup-for-ubuntu-16-04-tensorflow-1-2-keras-opencv3-python3-cuda8-and-cudnn5-1-324438dd46f0)
---

Second Trial of Yadav's tutorial to install  Tensorflow on ubuntu 22 August 2017.


#

```
sugo apt-get update
sudo apt-get upgrade  
```


# Prepare computer
```
$ sudo apt-get install build-essential cmake g++ gfortran
[sudo] password for miguel-admin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
g++ is already the newest version (4:5.3.1-1ubuntu1).
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  cmake-data gfortran-5 libgfortran-5-dev libgfortran3 libjsoncpp1
Suggested packages:
  codeblocks eclipse ninja-build gfortran-multilib gfortran-doc gfortran-5-multilib gfortran-5-doc libgfortran3-dbg
The following NEW packages will be installed
  cmake cmake-data gfortran gfortran-5 libgfortran-5-dev libgfortran3 libjsoncpp1
0 to upgrade, 7 to newly install, 0 to remove and 0 not to upgrade.
Need to get 12.4 MB of archives.
After this operation, 47.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y




$ sudo apt-get install git pkg-config python-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version (0.29.1-0ubuntu1).
git is already the newest version (1:2.7.4-0ubuntu1.1).
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libexpat1-dev libpython-dev libpython2.7-dev python2.7-dev
The following NEW packages will be installed
  libexpat1-dev libpython-dev libpython2.7-dev python-dev python2.7-dev
0 to upgrade, 5 to newly install, 0 to remove and 0 not to upgrade.
Need to get 28.2 MB of archives.
After this operation, 42.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y




$ sudo apt-get install software-properties-common wget
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wget is already the newest version (1.17.1-1ubuntu1.2).
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libcairo-perl libglib-perl libgtk2-perl libpango-perl python3-software-properties software-properties-gtk
Suggested packages:
  libfont-freetype-perl libgtk2-perl-doc
The following NEW packages will be installed
  libcairo-perl libglib-perl libgtk2-perl libpango-perl
The following packages will be upgraded:
  python3-software-properties software-properties-common software-properties-gtk
3 to upgrade, 4 to newly install, 0 to remove and 29 not to upgrade.
Need to get 1,180 kB of archives.
After this operation, 4,802 kB of additional disk space will be used.
Do you want to continue? [Y/n]



$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  snap-confine
0 to upgrade, 0 to newly install, 1 to remove and 29 not to upgrade.
After this operation, 55.3 kB disk space will be freed.
Do you want to continue? [Y/n] Y


$ sudo rm -rf /var/lib/apt/lists/*
```


# Install NVIDIA drivers

```
$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
```

ISSUE #1 did not allow the computer to reboot for which, I will try to use the  



However, I will try `nvidia-375`
[ref](https://askubuntu.com/questions/836386/ubuntu-16-04-nvidia-drivers-dont-work-for-gtx-960m)





Next step is to add proprietary repository of nvidia drivers.

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```


```
$ sudo apt-get install nvidia-375
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libcuda1-375 libjansson4 libllvm4.0 libvdpau1 libxnvctrl0 mesa-vdpau-drivers nvidia-opencl-icd-375 nvidia-prime nvidia-settings ocl-icd-libopencl1
  screen-resolution-extra vdpau-driver-all xserver-xorg-legacy
Suggested packages:
  bumblebee libvdpau-va-gl1 nvidia-vdpau-driver nvidia-legacy-340xx-vdpau-driver
The following NEW packages will be installed
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libcuda1-375 libjansson4 libllvm4.0 libvdpau1 libxnvctrl0 mesa-vdpau-drivers nvidia-375 nvidia-opencl-icd-375 nvidia-prime nvidia-settings ocl-icd-libopencl1
  screen-resolution-extra vdpau-driver-all xserver-xorg-legacy
0 to upgrade, 18 to newly install, 0 to remove and 29 not to upgrade.
Need to get 92.6 MB of archives.
After this operation, 419 MB of additional disk space will be used.
Do you want to continue? [Y/n]

```



Once nvidia driver is installed, restart the computer.


.
.
.



You can verify the driver using the following command.
```
cat /proc/driver/nvidia/version

```



# ISSUES #1 No rebooting after installing sudo apt-get install nvidia-340

Considering that the current machine has the following GPU

01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)

I decided to install:

https://launchpad.net/%7Egraphics-drivers/+archive/ubuntu/ppa
For G8x, G9x and GT2xx GPUs use `nvidia-340` (340.102)

Unfortunatelly, after rebooting the machine. some issues with the GPU did not allow
the machine to reboot

two possible solutions


i) After rebooting I couldn't get past the login screen. The solution that worked for me was to disable secure boot.
ii) I believe another version of nvidia drive should be installed

sudo apt-get install nvidia-361
https://askubuntu.com/questions/735572/how-to-install-nvidia-geforce-gtx-960-driver/735580
or
sudo apt-get install nvidia-364
https://askubuntu.com/questions/768959/ubuntu-16-04-nvidia-drivers-for-geforce-gtx-960m
or
 the `nvidia-375` (375.66)  as  it is the current long-lived branch release:
