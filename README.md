# OpenCV-aarch64
This is a guide to natively install OpenCV on aarch64/arm64 devices

#### Pre-requisites ####
Your aarch64 device should have Ubuntu/Debian/Armbian OS flashed on it.

#### Steps ####

 1. Install dependencies 
 
 ```bash
 sudo apt-get install python3-dev python3-pip python3-numpy

sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev  libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libdc1394-22-dev protobuf-compiler libgflags-dev libgoogle-glog-dev libblas-dev libhdf5-serial-dev liblmdb-dev libleveldb-dev liblapack-dev libsnappy-dev libprotobuf-dev libopenblas-dev libgtk2.0-dev libboost-dev libboost-all-dev libeigen3-dev libatlas-base-dev libne10-10 libne10-dev

pip3 install neon

sudo apt-get install libneon27-dev

sudo apt-get install libneon27-gnutls-dev
```

 2. Download Source 
 
 ```bash
 cd ~/

wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.4.0.zip
unzip opencv-3.4.0.zip

wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.4.0.zip
unzip opencv_contrib-3.4.0.zip
```

3. Configuring OpenCV using cmake:

Put your username in place of [username] below for the path to opencv_contrib/modules

```bash
cd ~/opencv-3.4.0

mkdir build

cd build

cmake -D CMAKE_BUILD_TYPE=RELEASE -D ENABLE_NEON=ON -D ENABLE_TBB=ON -D ENABLE_IPP=ON -D ENABLE_VFVP3=ON -D WITH_OPENMP=ON -D WITH_CSTRIPES=ON -D WITH_OPENCL=ON -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/root/[username]/opencv_contrib-3.4.0/modules/ ..
```
4. Compilation: 

```bash
make

sudo make install
```

5. Testing: 

```bash
python3
>>import cv2
>>
```

```
