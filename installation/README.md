A References for TensorFlow(TF) Installation
---

These are some of the tutorials for the installation of TF with GPU on Ubuntu 16.04
that I found in a quick google search (see the list below). However,
the dependecies can vary according to the hardware availability and the user's requirements.
Without doing any installation, I can forsee a problem with the versions of python,
the version of the libraries for NVIDIA drivers as well as the tensorflow versions.
With this in mind, I believe that for the TF installation is required to have a
clean Ubuntu 16.06 x64 installation.


machine
```
OS: Ubuntu 16.04 x64
USER: map479-DQ57TM
Link encap:Ethernet  HWaddr 70:71:bc:0c:1e:ed  
inet addr:147.188.136.231
```

# Tuorials for TensorFlow(TF) Installation on Ubuntu 16.04

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



Exrta [Install TensorFlow for Python 2.7 and Python 3.5 on the same machine (Ubuntu 16.04)](http://deeplearning.lipingyang.org/2017/01/19/install-tensorflow-for-python-2-7-and-3-5-on-one-machine/)



## [Getting Tensorflow to work with GPU NVidia GTX 1080 on Ubuntu 16.04 LTS](http://abhay.harpale.net/blog/machine-learning/deep-learning/getting-tensorflow-to-work-with-gpu-nvidia-gtx-1080-on-ubuntu-16-04-lts/)

Step 1: Install NVidia Cuda Toolkit  
Step 2: Install NVidia CuDNN  
Step 3: Install Tensorflow dependencies  
Step 4. Configure and build tensorflow  

## [Installing CUDA TK 8 and Tensorflow on a Clean Ubuntu 16.04 Install](http://queirozf.com/entries/installing-cuda-tk-and-tensorflow-on-a-clean-ubuntu-16-04-install)

Download the driver  
Download the CUDA Toolkit  
Install the driver you downloaded on the first step  
Install the CUDA toolkit  
Test the installation  

Install cuDNN  
Install native linear algebra libraries  
Install python stuff  

Install Tensorflow 1.0 into a virtualenv  



## [Installing TensorFlow for CPU and GPU on Ubuntu 16.04](https://www.howtoforge.com/tutorial/installing-tensorflow-neural-network-software-for-cpu-and-gpu-on-ubuntu-16-04/)

General setup
* 1 Install CUDA
* 2 Install the CuDNN library
* 3 Add the installation location to Bashrc file
* 4 Install TensorFlow with GPU support



## [Tensorflow-GPU-ubuntu16.04](https://gist.github.com/unsalted/294c7b128ac37ef70df5bbc1528effa9)

General setup
* Update nvidia key for cuda8.0
* Install CUDNN 5.0
* Conda env setup
* Activate



## [install-gpu-tensorflow-from-sources-w-ubuntu-16-04-and-cuda-8-0/](https://alliseesolutions.wordpress.com/2016/09/08/install-gpu-tensorflow-from-sources-w-ubuntu-16-04-and-cuda-8-0/)


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



# How to use TF (Tutorials)

https://www.oreilly.com/learning/dive-into-tensorflow-with-linux  
https://petewarden.com/2016/02/28/tensorflow-for-poets/
