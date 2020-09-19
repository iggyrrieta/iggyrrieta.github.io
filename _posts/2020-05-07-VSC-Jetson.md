---
title: 'Visual Studio Code for Jetson'
date: 2020-09-05
permalink: /posts/2020/05/Visual-Studio-Code-for-Jetson/
tags:
  - Jetson
  - Visual Studio Code


---



![](/iggyrrieta.github.io/images/Visual-Studio-Code-Jetson/code.png)



Visual Studio Code is my favorite IDE to work with, unfortunately it doesnt work with ARM architectures such as the Jetson boards...but we are lucky it is possible to install it.

First of all, open a terminal and go to de directory where you want to install VSC, then do the following:

1. Install the rep keys and setup

   ```bash
   wget -O script.deb.sh https://packagecloud.io/install/repositories/headmelted/codebuilds/script.deb.sh 
   ```

2. Sudo chmod +x script.deb.sh

   ```bash
   sudo bash script.deb.sh
   ```

3. Run the installation script

   ```bash
   wget -O vscodeInstall.sh https://code.headmelted.com/installers/apt.sh
   ```

4. Sudo chmod +x vscodeInstall.sh

   ```bash
   sudo bash vscodeInstall.sh
   ```

   

Now you can start VSC by calling `code-oss` within a terminal.

![](/iggyrrieta.github.io/images/Visual-Studio-Code-Jetson/codeoss.png)



Check next post to know **how to code remotely using VSC** 