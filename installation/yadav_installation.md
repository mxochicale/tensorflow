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

You can verify the driver using the following command.
```
$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  375.82  Wed Jul 19 21:16:49 PDT 2017
GCC version:  gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4)


```

# Step 4: Cuda-8 installation

https://developer.nvidia.com/cuda-downloads
On the link, you can select your system and download the appropriate package file.

```
$ sudo dpkg -i cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64.deb
$ sudo apt-get update
```

```
$ sudo apt-get install cuda
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ca-certificates-java cuda-8-0 cuda-command-line-tools-8-0 cuda-core-8-0 cuda-cublas-8-0 cuda-cublas-dev-8-0 cuda-cudart-8-0 cuda-cudart-dev-8-0 cuda-cufft-8-0 cuda-cufft-dev-8-0 cuda-curand-8-0
  cuda-curand-dev-8-0 cuda-cusolver-8-0 cuda-cusolver-dev-8-0 cuda-cusparse-8-0 cuda-cusparse-dev-8-0 cuda-demo-suite-8-0 cuda-documentation-8-0 cuda-driver-dev-8-0 cuda-drivers cuda-license-8-0
  cuda-misc-headers-8-0 cuda-npp-8-0 cuda-npp-dev-8-0 cuda-nvgraph-8-0 cuda-nvgraph-dev-8-0 cuda-nvml-dev-8-0 cuda-nvrtc-8-0 cuda-nvrtc-dev-8-0 cuda-runtime-8-0 cuda-samples-8-0 cuda-toolkit-8-0
  cuda-visual-tools-8-0 default-jre default-jre-headless fonts-dejavu-extra freeglut3 freeglut3-dev java-common libdrm-dev libgif7 libgl1-mesa-dev libglu1-mesa-dev libice-dev libpthread-stubs0-dev
  libsm-dev libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev
  libxcb-xfixes0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxi-dev libxmu-dev libxmu-headers libxshmfence-dev libxt-dev libxxf86vm-dev mesa-common-dev nvidia-375-dev
  nvidia-modprobe openjdk-8-jre openjdk-8-jre-headless x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  default-java-plugin libice-doc libsm-doc libxcb-doc libxext-doc libxt-doc icedtea-8-plugin openjdk-8-jre-jamvm fonts-ipafont-gothic fonts-ipafont-mincho fonts-wqy-microhei fonts-wqy-zenhei fonts-indic
The following NEW packages will be installed
  ca-certificates-java cuda cuda-8-0 cuda-command-line-tools-8-0 cuda-core-8-0 cuda-cublas-8-0 cuda-cublas-dev-8-0 cuda-cudart-8-0 cuda-cudart-dev-8-0 cuda-cufft-8-0 cuda-cufft-dev-8-0 cuda-curand-8-0
  cuda-curand-dev-8-0 cuda-cusolver-8-0 cuda-cusolver-dev-8-0 cuda-cusparse-8-0 cuda-cusparse-dev-8-0 cuda-demo-suite-8-0 cuda-documentation-8-0 cuda-driver-dev-8-0 cuda-drivers cuda-license-8-0
  cuda-misc-headers-8-0 cuda-npp-8-0 cuda-npp-dev-8-0 cuda-nvgraph-8-0 cuda-nvgraph-dev-8-0 cuda-nvml-dev-8-0 cuda-nvrtc-8-0 cuda-nvrtc-dev-8-0 cuda-runtime-8-0 cuda-samples-8-0 cuda-toolkit-8-0
  cuda-visual-tools-8-0 default-jre default-jre-headless fonts-dejavu-extra freeglut3 freeglut3-dev java-common libdrm-dev libgif7 libgl1-mesa-dev libglu1-mesa-dev libice-dev libpthread-stubs0-dev
  libsm-dev libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev
  libxcb-xfixes0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxi-dev libxmu-dev libxmu-headers libxshmfence-dev libxt-dev libxxf86vm-dev mesa-common-dev nvidia-375-dev
  nvidia-modprobe openjdk-8-jre openjdk-8-jre-headless x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  x11proto-xf86vidmode-dev xorg-sgml-doctools xtrans-dev
0 to upgrade, 87 to newly install, 0 to remove and 29 not to upgrade.
Need to get 34.2 MB/1,346 MB of archives.
After this operation, 2,215 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```



Next step is to add libraries to .bashrc file,

```
echo 'export PATH=/usr/local/cuda/bin:$PATH' >> ~/.bashrc
echo 'export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```


After sourcing the bashrc file, the CUDA version can be verified using
```
$ nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Tue_Jan_10_13:22:03_CST_2017
Cuda compilation tools, release 8.0, V8.0.61

```

# Step 5: Download cuDNN v6.0 (April 27, 2017), for CUDA 8.0

https://developer.nvidia.com/cudnn
Download cuDNN v6.0 (April 27, 2017), for CUDA 8.0 /cuDNN v6.0 Library for Linux
[Solution](https://github.com/tensorflow/tensorflow/issues/12416)


```
cd ~/Downloads/
tar xvf cudnn*.tgz
cd cuda
sudo cp */*.h /usr/local/cuda/include/
sudo cp */libcudnn* /usr/local/cuda/lib64/
sudo chmod a+r /usr/local/cuda/lib64/libcudnn*
```

# Step 6: Install python stuff


```
sudo apt-get update
sudo apt-get install -y python-numpy python-scipy python-nose python-h5py python-skimage python-matplotlib python-pandas python-sklearn python-sympy
sudo apt-get clean && sudo apt-get autoremove
sudo rm -rf /var/lib/apt/lists/*
```


Next install more python goodies like virtual environment, pip, pip3, jupyter notebook, etc.

```
sudo apt-get update
sudo apt-get install git python-dev python3-dev python-numpy python3-numpy build-essential python-pip python3-pip python-virtualenv swig python-wheel libcurl3-dev
sudo apt-get install -y libfreetype6-dev libpng12-dev
pip3 install -U matplotlib ipython[all] jupyter pandas scikit-image
```


# Step 7: Install openBLAS from its repository

```
mkdir ~/git && cd ~/git
git clone https://github.com/xianyi/OpenBLAS.git && cd OpenBLAS
make FC=gfortran -j16
sudo make PREFIX=/usr/local install
```


# Step 8: Install tensorflow



```
pip3 install --upgrade tensorflow-gpu
```
testing tensor flow
```
python3
>>> import tensorflow as tf
>>> a = tf.constant(5)
>>> b = tf.constant(6)
>>> sess = tf.Session()
>>> sess.run(a+b)

// this should print bunch of messages showing device status etc. // If everything goes well, you should see gpu listed in device

>> sess.close()
```


# Step 9: Install keras


```
pip3 install keras
```

```
python3
>>> import keras
```


# TODO
```
Step 10: Install opencv
Install packages to read different image formats.
Install qt5 for
Install libraries to video format
Install gtk for using GUI
Install libatlas for opencv functions
Install hdf5 library
Clone openCV from repository where opencv is installed with cuda8.
Instal opencv with python 3.

Step 10: Virtual environments
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
