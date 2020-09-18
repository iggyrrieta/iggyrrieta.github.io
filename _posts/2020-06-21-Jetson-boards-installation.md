---
title: 'Jetson boards - Install basics'
date: 2020-06-21
permalink: /posts/2020/06/Jetson-boards-install-basics/
tags:
  - Jetson Nano
  - Jetson TX2
  - Installation


---



![](/iggyrrieta.github.io/images/jetson-boards-install-basics/jetson.png)



**NVIDIA** is nowadays one of the top companies creating IA machines and graphical components. At NVIDIA they have a family of IA boards named Jetson. 

-  Jetson Nano          ~ $99
- Jetson TX2              ~ from $419
- Jetson Xavier NX    ~ from $329
- Jetson AGX Xavier  ~ from $729

This boards have different hardware capabilities but all are focused on the same area of work. This is basically IA, computer vision and Deep learning.



**I've tested the Jetson Nano and Jetson TX2**. These are the steps I followed to get both boards up and running: 

> 
>
> **WARNING:** To get the OS in your Jetson you can use a SDK manager or use a SD card with an image flashed, take in consideration that if you pick the SDK manager option you are going to use only the space available in the board (in the case of Jetson Nano it is not enough so better take the SD card option)

1. Flash the OS

   **OPTION1:** Download SDK manager in your personal computer

   ```bash
   https://developer.nvidia.com/jetpack-43-archive
   ```

   First you need to connect the USB cable from the Jetson to your computer. Select the version you like to flash (I used the 4.3). During the installation you must connect to the Jetson when the SDK manager ask for it. Follow all the steps to install Ubuntu in the Jetson, the SDK manager will guide you. Finally if it fails to install the CUDA and IA tools, don't worry we can install it later on. **From now on you can work directly on your Jetson board.**

   ![](/iggyrrieta.github.io/images/jetson-boards-install-basics/sdkmanager.png)

   

   **OPTION2:** SD Card

   follow [this](https://developer.nvidia.com/embedded/learn/get-started-jetson-nano-devkit#write) instructions

   ![](/iggyrrieta.github.io/images/jetson-boards-install-basics/fetcher.png)

   

2. If the installation didn't installed the IA tools, then install them this way:

   ```bash
   sudo apt update
   ```

   ```bash
   sudo apt-get install nvidia-jetpack
   ```

3. Install **PIP**

   ```bash
   sudo apt-get install python-pip
   ```

4. Install **jtop** to monitor your Jetson

   ```bash
   sudo -H pip install -U jetson-stats
   ```

   To run jtop from terminal: 

   ```bash
   sudo jtop
   ```

5. CPU & GPU 

   | Mode | Mode Name      | Denver 2 | Frequency | ARM A57 | Frequency | GPU Frequency |
   | ---- | -------------- | -------- | --------- | ------- | --------- | ------------- |
   | 0    | Max-N          | 2        | 2.0 GHz   | 4       | 2.0 GHz   | 1.30 Ghz      |
   | 1    | Max-Q          | 0        |           | 4       | 1.2 Ghz   | 0.85 Ghz      |
   | 2    | Max-P Core-All | 2        | 1.4 GHz   | 4       | 1.4 GHz   | 1.12 Ghz      |
   | 3    | Max-P ARM      | 0        |           | 4       | 2.0 GHz   | 1.12 Ghz      |
   | 4    | Max-P Denver   | 1        | 2.0 GHz   | 1       | 2.0 GHz   | 1.12 Ghz      |

   To select one mode you can change it on the top bar menu or using the terminal:

   ```bash
   sudo nvpmodel -m [mode]
   ```

   Where mode is the Mode number 

   ```bash
   sudo nvpmodel -m 0
   ```

   Check mode:

   ```bash
   sudo nvpmodel -q 
   ```

   