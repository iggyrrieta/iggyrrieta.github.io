---
title: 'My own ROS joystick'
date: 2020-04-20
permalink: /posts/2020/04/my-own-ros-joystick/
tags:
  - ROS
  - QT

---



![](/iggyrrieta.github.io/images/ros-joystick/rosjoystick1.png)

When running a map using ROS for the first time, you are in a position where you need to move your robot around that map. There are some packages already implemented that publish velocity data to the **/cmd_vel** topic. Probably you already heard about the **teleop_twist_keyboard**, made by Graylin Trevor Jay and published on ros.org [here](https://wiki.ros.org/teleop_twist_keyboard)

The teleop_twist_keyboard works on terminal and reads input from the keyboard. Those inputs are then published to Twist. 

Using the teleop_twist_keyboard, this post shows how to create your own ros joystick using a QT GUI. QT is a very famous multiplatform framework used to create modern UIs & applications for multiple screens. 

If you know about ROS you probably know about **rVIz**. This tool is now based in QT framework and can be used as a library to create your own "rViz interface" to manage your roborts, all using QT. 

So, it looks like a good idea to start using QT for our ros interfaces.



## Requirements



- **ROS** (I am using Melodic)
- **QT Creator** (configured to be called from terminall)
- **C++ dependencies**
  - QT Create
  - QT build



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

This command will create a QT Gui that connects to a ROS master and publish a topic which is printed using a log. The code created can be removed or changed, **what we want is just the architecture created**. 

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



## Code

Once you have a package created with a ROS-QT architecture, you can apply all modifications you need.

Check my **ros_joystick** repository  [here](https://github.com/iggyrrieta/ros_joystick).

This is my project tree:

![](/iggyrrieta.github.io/images/ros-joystick/projectTREE.png)

Take in consideration that changes must be reflected in **packages.xml** and **CMakeLists.txt**

![](/iggyrrieta.github.io/images/ros-joystick/ros_joystick_test.png)



## TO DO

The right side of the ros_joystick is useless. It can be used to create or navigate the robot to an specific location.
