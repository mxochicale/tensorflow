[Ubuntu 16.04: Tensorflow 1.2, keras, opencv3, python3, cuda8 and cudnn5.1](https://medium.com/@vivek.yadav/deep-learning-setup-for-ubuntu-16-04-tensorflow-1-2-keras-opencv3-python3-cuda8-and-cudnn5-1-324438dd46f0)
---

I am following Vivek Yadav, Jun 22 2017 tutorial.

## comments

add install to

and E: Unable to locate package autoremove



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




sudo apt-get install software-properties-common wget

sudo rm -rf /var/lib/apt/lists/*
```


# Install NVIDIA drivers

```
$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
```

https://launchpad.net/%7Egraphics-drivers/+archive/ubuntu/ppa
For G8x, G9x and GT2xx GPUs use `nvidia-340` (340.102)



```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
```


```
$ sudo apt-get install nvidia-340
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  snap-confine
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libcuda1-340 libjansson4 libvdpau1 libxnvctrl0 mesa-vdpau-drivers nvidia-opencl-icd-340 nvidia-prime nvidia-settings ocl-icd-libopencl1 screen-resolution-extra vdpau-driver-all
Suggested packages:
  bumblebee libvdpau-va-gl1 nvidia-vdpau-driver nvidia-legacy-340xx-vdpau-driver
The following NEW packages will be installed
  bbswitch-dkms dkms lib32gcc1 libc6-i386 libcuda1-340 libjansson4 libvdpau1 libxnvctrl0 mesa-vdpau-drivers nvidia-340 nvidia-opencl-icd-340 nvidia-prime nvidia-settings ocl-icd-libopencl1 screen-resolution-extra
  vdpau-driver-all
0 to upgrade, 16 to newly install, 0 to remove and 0 not to upgrade.
Need to get 74.5 MB of archives.
After this operation, 364 MB of additional disk space will be used.
Do you want to continue? [Y/n]

```


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




.
.
.



Once nvidia driver is installed, restart the computer. You can verify the driver using the following command.
```
cat /proc/driver/nvidia/version

```
