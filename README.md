# RRBot - A double inverted pendulum based on ROS Noetic.

## What is this repo about?

I love ROS, a.k.a the Robot Operating system. The reusable modules available within this framework are ones to dies for. I mean the navigation stack, the localization stack, the manipulation stack, it's unbelievable. I don't know what I'd do without this framework. Don't forget the wide community of ROS users.

However, ROS tutorials tend to be old, usually targeted at ROS kinetic. Most of the tutorials I've used so far tend not to work with the latest versions, in this case melodic and noetic. This repo contains code for rrbot but based on noetic. It's adapted from the official rrbot tutorial page.

## RRBot

RRBot, or ''Revolute-Revolute Manipulator Robot'', is a simple 3-linkage, 2-joint arm that we will use to demonstrate various features of Gazebo and URDFs. It essentially a double inverted pendulum and demonstrates some fun control concepts within a simulator.

![rrbot rviz](https://github.com/lyleokoth/rrbot/blob/main/resources/images/rrbot_rviz.png)

## The Setup

To get rrbot, clone the [RRBot github repo](https://github.com/lyleokoth/rrbot), and build the workspace.

```
git clone https://github.com/lyleokoth/rrbot
cd rrbot
catkin_make
source devel/setup.bash
```

## Run

To display rrbot in rviz:

```
source devel/setup.bash
roslaunch bot_control bot_control.launch
```

![rrbot rviz](https://github.com/lyleokoth/rrbot/blob/main/resources/images/rrbot_rviz.png)

You should also be able to play with the slider bars in the Joint State Publisher window to move the two joints.

It is important that while converting your robot to work in Gazebo, you don't break Rviz or other ROS-application functionality, so its nice to occasionally test your robot in Rviz to make sure everything still works.

The gazebo_ros_control tutorial will explain how to use Rviz to monitor the state of your simulated robot by publishing /joint_states directly from Gazebo. In the previous example, the RRBot in Rviz is getting its /joint_states from a fake joint_states_publisher node (the window with the slider bars).

## RRBot Workspace 

The workspace contains two packages:

- ### rrbot_description
    - contains the files necessary to display the rrbot. It is mainly used to showcase the robots appearnce in rviz and later, gazebo.
- ### rrbot_control
    - rrbot_control contains the files used to control the rrbot.

## Examine the RRBot URDF

The rest of this tutorial will refer to various aspects of the RRBot URDF. Go ahead and view the [rrbot.xacro](https://github.com/lyleokoth/rrbot/blob/main/src/rrbot_description/urdf/rrbot.xacro) file now:

```
rosed rrbot_description rrbot.xacro
```

Note that we are using Xacro to make some of the link and joint calculations easier. We are also including six additional files:
- [rrbot_properties.xacro](https://github.com/lyleokoth/rrbot/blob/main/src/rrbot_description/urdf/rrbot_properties.xacro) 
    - Contains the rrbot physical properties such as link dimensions and masses
- macros.xacro
    - Contains macros that are mainly used to calculate the link inertias
- materials.xacro
    - Contains the materials used in visualizing the links in rviz.
- gazebo_properties.xacro
    - This contains the link physical properties used in visualizing the robot in gazebo, such as color.
- gazebo_phyisics.xacro
    - This contains link properties used by gazebo to properly simulate the robot, such as friction.
- gazebo_plugins.xacro
    - This contains the plugins that are used to in gazebo to simulate various sensors and actuators e.g lidar and camera.