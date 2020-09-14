---
title: 'Using QT for ROS applications'
date: 2020-04-20
permalink: /posts/2020/04/Using-QT-for-ROS/
tags:
  - ROS
  - QT

---



To install QT Creator and get it autoconfigured to be used from the terminal, install the following:

```bash
sudo apt-get install qtcreator
```

If it works, you can now call it from terminal using:

```bash
qtcreator
```



To install l C++ dependencies to use QT with ROS, install the following:

```bash
sudo apt-get install ros-melodic-qt-create 
```

```bash
sudo apt-get install ros-melodic-qt-build
```



## Create a package based in QT

The easiest way to start building a QT Gui  with ROS is using the  **qt_create** package. Reference [here](https://wiki.ros.org/qt_create).

To use this package, go to your ros workspace and run the following using a terminal:

```bash
catkin_create_qt_pkg ros_joystick
```

In this case **ros_joystick** is the name of the package. 

This command will create a QT Gui that connects to a ROS master and implement a talker/listener chat. The code created can be removed or changed, **what we want is just the architecture created**. 

![](/iggyrrieta.github.io/images/ros-joystick/qtros.png)



First thing to do when creating a package this way is to build it. So go to you ros workspace and run:

```bash
catkin build
```

This way you'll have now a build folder with your new package, this build folder will be used in QT to reference  your package.

To work with it you **MUST** open QT from terminal (be sure the package has been build). Go to your ROS workspace and call it using this:

```bash
qtcreator
```

From qtcreator, do the following:

1. **Open new**

2. Go to **your package folder** and select the **CMakeLists.txt**

3. Select **Configure Project**

   ![](/iggyrrieta.github.io/images/ros-joystick/qtbuild.png)

4. If it fails building, go to **PROJECTS section** on left panel

5. Change the build directory, select the location where your package is build (inside your catkin workspace in folder build)

   ![](/iggyrrieta.github.io/images/ros-joystick/qtbuild2.png)

6. If it still fails, close QT creator and open it again from terminal

