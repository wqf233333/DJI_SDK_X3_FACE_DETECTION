#DJI Onboard SDK ROS Packages

----

##Introduction

This is a ROS package for DJI OnBoard SDK.

It helps users handle the following commands and actions.

* The activation
* The flight control obtainment
* The flight control release
* The take off procedure
* The landing procedure
* The go home procedure
* The Gimbal control
* The attitude control
* The photo taking procedure
* The start/stop video recording procedure
* Local navigation (fly into a certain (X,Y,Z))
* GPS navigation (fly into a certain GPS coordinate)
* Waypoint navigation (fly through a series of GPS coordinates)


##How to use
1. Install and configure your hardware correctly.
2. Enter the following info into `dji_sdk/launch/sdk_manifold.launch`.
	* APP ID
	* APP Level
	* Communication Key
	* Uart Device Name
	* Baudrate
3. Use `roslaunch dji_sdk sdk_manifold.launch` to start the core node.
4. Use'sudo -s'and then use'rosrun dji_sdk_read_cam dji_sdk_read_cam'

##System Structure
* [dji_sdk](dji_sdk): the core package handling the communication with Matrice 100, which provides a h
* [dji_sdk_manifold_read_cam](dji_sdk_manifold_read_cam): a X3 video decoding package for Manifold,there is a face detection demo.

![image](dji_sdk_doc/structure.jpg)
[click to see fullsize image](https://raw.githubusercontent.com/dji-sdk/Onboard-SDK-ROS/2.3/dji_sdk_doc/structure.jpg)

##System Environment
The below environment has been tested.
* Operating System: Ubuntu 14.04, Manifold
* ROS version: ROS Indigo

---

#DJI Onboard SDK ROS例程

##简介

此ROS例程实现了以下功能：

* 激活 Matrice100 （以下简称M100）
* 获取 M100 控制权
* 释放 M100 控制权
* 向 M100 发送起飞指令
* 向 M100 发送降落指令
* 向 M100 发送返航指令
* 对 M100 进行姿态控制
* 对 M100 进行云台角度控制
* 向 M100 发送相机控制指令
* 控制 M100 进行 (x,y,z) 坐标导航
* 控制 M100 进行 GPS 坐标导航
* 控制 M100 进行航点飞行任务
* 通过 WebSocket 向 M100 发送网页地图生成的航点指令
* 通过 MAVLink 和 QGroundControl 控制 M100

##如何使用

1. 按照文档配置好 M100 
2. 将激活信息输入至launch file：`dji_sdk/launch/sdk_manifold.launch`
	* APP ID （在官网注册key后得到）
	* API Level （key对应的 API 权限等级）
	* Communication Key（在官网注册key后得到）
	* Uart Device Name（串口设备名称）
	* Baudrate（比特率）
3. 运行 `roslaunch dji_sdk sdk_manifold.launch` 来启动核心包。
4. 在'sudo -s'下运行'rosrun dji_sdk_read_cam dji_sdk_read_cam'

##系统架构
* [dji_sdk](dji_sdk): 核心 ROS 包，处理所有与 M100 的串口通信并提供了 `dji_drone.h`的头文件供开发者引用。
* [dji_sdk_manifold_read_cam](dji_sdk_manifold_read_cam): Manifold专用 ROS 包，对禅思 X3 云台的视频信息进行解码输出视频流。运行简单的opencv人脸识别库，并控制云台的姿态，使检测到的人脸位于画面的中心.
* [dji_sdk_doc](dji_sdk_doc): 所有的文档与图片信息。

![image](dji_sdk_doc/structure.jpg)
[点击查看大图](https://raw.githubusercontent.com/dji-sdk/Onboard-SDK-ROS/2.3/dji_sdk_doc/structure.jpg)

#系统环境
此 ROS 包在如下系统中进行测试；
* 操作系统：Ubuntu 14.04， DJI Manifold
* ROS 版本：ROS Indigo
