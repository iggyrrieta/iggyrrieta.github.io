---
title: 'Jetson - Compile RealSense cameras'
date: 2020-06-14
permalink: /posts/2020/06/Jetson-Compile-realsense-cameras/
tags:
  - Intel
  - RealSense
  - ARM
  - Jetson


---



![](/iggyrrieta.github.io/images/jetson-realsense-compile/intelcameras.png)




First of all, check the intel realsense documentation: https://dev.intelrealsense.com/docs/compiling-librealsense-for-linux-ubuntu-guide

> I followed most of the steps but I had to change some to make my cameras D435 and T265 work properly



**¡WARNING!**: Switch the cameras off before compiling the realsense libraries.



1. Dependencies

   ```bash
   sudo apt-get install git libssl-dev libusb-1.0-0-dev pkg-config libgtk-3-dev
   ```

   ```bash
   sudo apt-get install libglfw3-dev libgl1-mesa-dev libglu1-mesa-dev
   ```

   

2. Clone the following repository to get all the libraries needed

   ```bash
   git clone https://github.com/ageve/librealsense
   ```

   ```bash
   cd librealsense
   ```

3. Checkout version 2.35.2 (last version at June 22, 2020) :
   
   > There is a bug that make the compilation fail, follow this ticket to solve it:
   > 
   > https://github.com/IntelRealSense/librealsense/issues/6573#issuecomment-643725732
   
   Checkout version 2.35.2:
   
   ```bash
   git checkout v2.35.2
   ```
   
4. Rules

   ```bash
   sudo cp config/99-realsense-libusb.rules /etc/udev/rules.d/
   ```

   ```bash
   sudo udevadm control --reload-rules && udevadm trigger
   ```

5. Create `build`  folder and open it

   ```bash
   mkdir build && cd build
   ```

6. Compile using CMAKE

   Be sure to write the following inside  `~/.bashrc` :

   ```bash
   #=============
   # CUDA
   #=============
   export CUDACXX=/usr/local/cuda-10.0/bin/nvcc
   export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/cuda/lib64
   export PATH=${PATH}:/usr/local/cuda/bin
   ```

   > In my case I am using cuda-10.0, change this with your installed version.

   
   
    Compile:
   
   ```bash
   cmake ../ -DFORCE_LIBUVC:bool=true -DFORCE_RSUSB_BACKEND:bool=true -DCMAKE_BUILD_TYPE=Release -DBUILD_WITH_CUDA:bool=true -DBUILD_PYTHON_BINDINGS=bool:true
   ```


7. Install

   If this is not the first time you install it:

   ```bash
   sudo make uninstall && make clean && make -j4 && sudo make install
   ```

   If it is the first time:

   ```bash
   sudo make clean && make -j4 && sudo make install
   ```

8. To use this libraries with ROS2:
   
   ```bash
   sudo ln -s /usr/local/lib/librealsense2.so.2.35 /usr/lib/aarch64-linux-gnu/librealsense2.so
   ```
   
9. Test
   
   ```bash
   realsense-viewer
   ```

