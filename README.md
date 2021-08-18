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