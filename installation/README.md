A References for TensorFlow(TF) Installation
---

These are some of the tutorials for the installation of TF with GPU on Ubuntu 16.04.
I have ordered them from the most recent day of the post to the current time (27 July 2017).

The first thing to consider is that dependecies can vary according to the hardware
availability and the user's requirements.  Therefore, without doing any installation,
I can forsee a problem with the versions of python, the version of the libraries for NVIDIA drivers
 as well as the tensorflow versions. These are some resources where I tried to get
 a bit of advices and put it together a set of common commmands for my particupar
 hardware availablity.

# Machine

## ID

```
OS: Ubuntu 16.04 x64
USER: map479-DQ57TM
Link encap:Ethernet  HWaddr 70:71:bc:0c:1e:ed  
inet addr:147.188.136.231
```

### GPU

```
$ lspci -v
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. GM206 [GeForce GTX 960]
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	Expansion ROM at fb000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau

```


### CPU
```
$  lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 30
Model name:            Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz
Stepping:              5
CPU MHz:               2661.000
CPU max MHz:           2661.0000
CPU min MHz:           1197.0000
BogoMIPS:              5319.96
Virtualisation:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
NUMA node0 CPU(s):     0-3
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida
map479@map479-DQ57TM:~$

```

### Memory

```
$ cat /proc/meminfo
MemTotal:        3976668 kB
MemFree:          350380 kB
MemAvailable:    1549888 kB
Buffers:          172964 kB
Cached:          1100120 kB
SwapCached:         4080 kB
Active:          2059564 kB
Inactive:        1169200 kB
```



# Tuorials for TensorFlow(TF) Installation on Ubuntu 16.04


## [Ubuntu 16.04: Tensorflow 1.2, keras, opencv3, python3, cuda8 and cudnn5.1](https://medium.com/@vivek.yadav/deep-learning-setup-for-ubuntu-16-04-tensorflow-1-2-keras-opencv3-python3-cuda8-and-cudnn5-1-324438dd46f0)
Vivek Yadav, Jun 22 2017


Some Yadav's advices

* "_secure boot needs to be disabled from bios before taking any of these steps_"
[How to Enable or Disable Secure Boot Bios](https://www.youtube.com/watch?v=AMc15OcRfug)
* "_never to install ROS on deep learning computer directly. Sticking to VM, or a dedicated computer is the best._"


~~Step 1: Install google chrome~~  
Step 2. Update OS, install cmake, fortran, g++ etc.  
Step 3: Install NVIDIA drivers  
Step 4: Cuda-8 installation  
Step 5: cuDNN 5.1  
Step 6: Install python stuff  
Step 7: Install openBLAS from its repository  
Step 8: Install tensorflow  
Step 9: Install keras  
Step 10: Install opencv  
Step 10: Virtual environments  




## [Tensorflow-GPU-ubuntu16.04](https://gist.github.com/unsalted/294c7b128ac37ef70df5bbc1528effa9)
unsalted Last active 22 days ago (seen on 27 July 2017)
General setup
* Update nvidia key for cuda8.0
* Install CUDNN 5.0
* Conda env setup
* Activate


## [VIDEO: How to Install TensorFlow on Ubuntu 17.04 16.04](https://www.youtube.com/watch?v=FuRSeRe88sw)
Published on May 23, 2017

Command Summary:
```

How to Install TensorFlow on Ubuntu 17.04 16.04
1) Install pip and virtualenv.
$ sudo apt-get install python-pip python-dev python-virtualenv
2) Create a virtualenv environment.
$ virtualenv --system-site-packages myvenv
3)Activate the virtualenv environment
$ source myvenv/bin/activate
4) Install TensorFlow in the active virtualenv environment
$ pip install --upgrade tensorflow
5) Test
$ python
import tensorflow
Machine Learning
```



## [Installing TensorFlow for CPU and GPU on Ubuntu 16.04](https://www.howtoforge.com/tutorial/installing-tensorflow-neural-network-software-for-cpu-and-gpu-on-ubuntu-16-04/)
Akshay Pai, May 02, 2017

General setup
* 1 Install CUDA
* 2 Install the CuDNN library
* 3 Add the installation location to Bashrc file
* 4 Install TensorFlow with GPU support





## [Installing CUDA TK 8 and Tensorflow on a Clean Ubuntu 16.04 Install](http://queirozf.com/entries/installing-cuda-tk-and-tensorflow-on-a-clean-ubuntu-16-04-install)
26 Apr 2017

Download the driver  
Download the CUDA Toolkit  
Install the driver you downloaded on the first step  
Install the CUDA toolkit  
Test the installation  

Install cuDNN  
Install native linear algebra libraries  
Install python stuff  

Install Tensorflow 1.0 into a virtualenv  



## [VIDEO: Build Tensorflow From Source in Ubuntu 16.04](https://www.youtube.com/watch?v=VebcaH_gb0c)


Published on Mar 3, 2017

Command Summary:
```
sudo apt-get install python3-numpy python3-dev python3-pip python3-wheel
cd tensorflow
git pull
./configure
bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package
bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
pip install /tmp/tensorflow_pkg/tensorflow-1.0.0-cp35-cp35m-linux_x86_64.whl
```




## [Getting Tensorflow to work with GPU NVidia GTX 1080 on Ubuntu 16.04 LTS](http://abhay.harpale.net/blog/machine-learning/deep-learning/getting-tensorflow-to-work-with-gpu-nvidia-gtx-1080-on-ubuntu-16-04-lts/)
LipingY, January 19, 2017


Step 1: Install NVidia Cuda Toolkit  
Step 2: Install NVidia CuDNN  
Step 3: Install Tensorflow dependencies  
Step 4. Configure and build tensorflow  




## [Install TensorFlow for Python 2.7 and Python 3.5 on the same machine (Ubuntu 16.04)](http://deeplearning.lipingyang.org/2017/01/19/install-tensorflow-for-python-2-7-and-3-5-on-one-machine/)
LipingY, January 19, 2017


Install pip and Virtualenv:    
Create a Virtualenv environment in the directory for python 3     
Activate the virtual environment:    
Install TensorFlow in the virtualenv for python 3:    



## [Install GPU TensorFlow from Source on Ubuntu Server 16.04 LTS](http://deeplearning.lipingyang.org/2017/01/18/install-gpu-tensorflow-ubuntu-16-04/)
By LipingY on January 18, 2017

General Setup
* 1: Install Required Packages
* 2: Update & Install NVIDIA Drivers
* 3: Install NVIDIA CUDA Toolkit 8.0
* 4: Install NVIDIA cuDNN
* 5: Install Bazel
* 6: Clone TensorFlow
* 7: Configure TensorFlow Installation
* 8: Build TensorFlow
* 9:Build & Install Pip Package
* 10: Test Your Installation




## [install-gpu-tensorflow-from-sources-w-ubuntu-16-04-and-cuda-8-0/](https://alliseesolutions.wordpress.com/2016/09/08/install-gpu-tensorflow-from-sources-w-ubuntu-16-04-and-cuda-8-0/)
Justin,September 8 2016

General setup
* Install Required Packages
* Update & Install Nvidia Drivers
* Install Nvidia Toolkit 8.0 & CudNN
* Install Bazel
* Clone Tensorflow
* Configure TensorFlow Installation
* Build TensorFlow
* Build & Install Pip Package
* Test Your Installation
