# Workflows of Vision Group

视觉组培训

[TOC]



## 任务 

工作内容

1.负责拥有发射机构兵种自动瞄准功能的研发与调试；

2.负责工程、飞镖、雷达、击打能量机关的算法研发与调试；

3.负责哨兵全自动机器人的算法研发，包括但不限于建图、定位、导航、自主决策等；

4.与电控协作进行电控-视觉联调

5.进行工业相机方案设计、选型、测试与性能评估。



其中最主要的工作就是自动识别装甲板，实现自瞄——真实的物理外挂。





视觉组的门槛最高，需要学习的东西有很多，在三个组别中上手难度最大



## 前置知识&技能

### 最最最基本的技能

- 学会科学上网

- 熟练使用百度、Google，关键字

- 善用ChatGPT、Claude等AI

- 学会使用GitHub

- 学会看官方文档、学会啃英文文档

- 提问的艺术

  ![1690222367111](md_pic/1690222367111.png)



[betaseeker/How-To-Ask-Questions: 群里提问的艺术 (github.com)](https://github.com/betaseeker/How-To-Ask-Questions)



### 数学基础

​	高数、线性代数、概率论、大学物理



常用标准坐标系的定义

`右手系`  规定x轴朝前，y轴朝左，z轴朝上

<img src="./md_pic/1684006551242.png" width="200" height="200" alt="右手系" align=center />



`旋转角`

<img src="./md_pic/1684008264802.png" width="200" height="200" alt="旋转角" align=center />

`正向判断方法`：从坐标轴（旋转轴）正向看向原点，逆时针方向为旋转轴正方向

如：yaw轴 z轴为转轴 从z轴正向看向原点，逆时针方向为pitch轴正方向

<div>
<img src="./md_pic/欧拉角2.gif" width="200" height="200" alt="偏航角" align=center />
<img src="./md_pic/欧拉角3.gif" width="200" height="200" alt="俯仰角" align=center />
<img src="./md_pic/欧拉角4.gif" width="200" height="200" alt="翻滚角" align=center />
</div>
   `偏航角(yaw) 绕z轴旋转`                         `俯仰角(pitch) 绕y轴旋转`                    `翻滚角(roll) 绕x轴旋转`



[REP 103 -- Standard Units of Measure and Coordinate Conventions (ROS.org)](https://www.ros.org/reps/rep-0103.html)



### 机器人项目的基本框架

机械、电控、视觉、操作手是如何串联起来的？

![1690604497313](md_pic/1690604497313.png)




### 电控知识

* 串口通信，用于NUC（上位机、机载电脑）与C板（下位机、STM32）通信
* 电机转轴、坐标系
* 弹道解算（另开篇幅讲解）

更详细的知识讲解在电控培训





### 编程/开发基础

`Linux`

* Ubuntu （20.04  22.04）

  * 双系统（Windows+Linux）

  * 虚拟机（VMware） 比较方便

  * `WSL2`     **方便**

    ​	WSL（Windows Subsystem for Linux），它可以让你能够在Windows系统下直接使用开发环境，免去了双系统频繁开关机切换系统的麻烦，相比虚拟机，WSL 占用资源更少，更加流畅，可以对 Windows 文件系统下的文件直接进行读写，文件传输更方便，但是由于没有自带图形化面，全命令行操作，有一定使用门槛，之前没有接触过Linux的同学建议先对实机有一定认知后再进行尝试。 

  * 虚拟机 推荐用VMware

  

* 对Linux有一定了解，基本熟悉Linux常用的命令。
  * 目录操作 cd ls mkdir rm mv cp find pwd
  * 文件操作 touch rm vi/vim/gedit/nano cat
  * 权限 sudo chmod
* ...

- [40个最常用的Linux命令行大全 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/420247468)



`C++`

* C++是目前视觉代码中最主要使用的编程语言

学习要求

- 了解C++编译及运行的基本原理，在自己电脑上配置好能够编译运行C++程序的开发环境，直接使用**IDE**（集成式开发环境）如Visual Studio、CLion等进行开发，或使用VScode等**编辑器**配合编译 器进行编译均可（推荐直接在ubuntu下使用vscode+cmake）。 
- 学习C++数据类型，基本语法语句
- C++11与C++14的特性
- 熟练掌握类

几个推荐的学习网站

[C++ 教程 | 菜鸟教程 (runoob.com)](https://www.runoob.com/cplusplus/cpp-tutorial.html)

[cppreference.com](https://zh.cppreference.com/w/首页)





`CMake`

* CMake是一款开源、跨平台的项目构建工具。用来组织和管理代码，简化在配置复杂项目时的工作。

* [CMake官方文档 CMake Tutorial — CMake 3.17.5 Documentation](https://cmake.org/cmake/help/v3.17/guide/tutorial/)

  [Introduction - 《CMake菜谱（CMake Cookbook中文版）》 - 书栈网 · BookStack](https://www.bookstack.cn/read/CMake-Cookbook/README.md)

  [CMake examples](https://github.com/ttroy50/cmake-examples)

`Python`

* 方便快捷的编程语言，在视觉组中常被用于写launch文件（用于快捷启动多个节点）、炼丹（如数字识别）

`OpenCV`

* OpenCV是一个基于Apache2.0许可（开源）发行的跨平台计算机视觉和机器学习软件库，实现了图像处理和计算机视觉方面的很多通用算法。
* 用于视觉自瞄目标识别的基本工具

`ROS2`

* ROS是一套开源的软件**框架**和工具集，用来帮助开发人员建立机器人应用程序，它提供了硬件抽象、设备驱动、函数库、可视化工具、消息传递和软件包管理等诸多功能，ROS2是ROS的新版本，有较大的变化，主要是通信框架上的变更。 

  目前我们使用ROS2作为通信框架galactic，完成tutorials部分的学习即可对ROS2的使用有一个大概的了解和掌握 

  [ROS 2 Documentation — ROS 2 Documentation: Humble documentation](https://docs.ros.org/en/humble/)

  主要看C++部分即可，Python部分作为了解

  每个例程都要认真学习

  学习过程：

  - 对Linux有一定了解，基本熟悉Linux常用的命令
- OpenCV图像处理基础、CMake基础
  - 在自己的Ubuntu系统中完成ROS2 Humble桌面版的安装（对应官方教程的**Installation**）安装时应该要挂上科学上网的工具，开启TUN模式（Clash -> TUN Mode ）
  - 把**Tutorials**的教程过一遍，熟悉ROS2的各种概念，自己上机试验，这一部分耗时最长
  - 最后就是完成视觉识别的题目

`Git`

* Git是一款免费、开源的分布式版本控制系统。我们使用Git对项目进行版本控制、多人协作，从而提高管理效率。

* 搭配Github使用

* 

  [git 简明指南 (runoob.com)](https://www.runoob.com/manual/git-guide/)

  [Git 教程 | 菜鸟教程 (runoob.com)](https://www.runoob.com/git/git-tutorial.html)

  [Git官方教程](https://git-scm.com/book/zh/v2)

  

`Docker`     像`轻量级虚拟机`

* Docker 是一个开源的应用容器引擎，基于 Golang 语言开发，可以让开发者打包他们的应用以及依赖包到一个轻量级、可移植的容器中，然后发布到任何流行的 Linux 服务器。容器是一个沙箱机制，相互之间不会有影响（类似于我们手机上运行的 app），并且容器开销是很低的。
  　　Docker 是一个供开发人员和系统管理员构建、运行和与容器共享应用程序的平台。使用容器部署应用程序称为容器化。
* Docker在容器的基础上，进行了进一步的封装，从文件系统、网络互联到进程隔离等等，极大的简化了容器的创建和维护。使得Docker技术比虚拟机技术更为轻便、快捷。
  Docker和传统虚拟化方式的不同之处。传统虚拟机技术是虚拟出一套硬件后，在其上运行一个完整操作系统，在该系统上再运行所需应用进程；而容器内的应用进程直接运行于宿主的内核，容器内没有自己的内核，而且也没有进行硬件虚拟。因此容器要比传统虚拟机更为轻便。

自行摸索

可以尝试部署一下自己的网盘：[Docker部署nextcloud及其使用方法 - CodeAlan - 博客园 (cnblogs.com)](https://www.cnblogs.com/codealan/p/17556552.html)

跨平台

`深度学习、强化学习等`

炼丹，雷达兵种的关键算法。



`SLAM`

Simultaneous Localization and Mapping，同步定位与建图。SLAM问题可以描述为: 机器人在未知环境中从一个未知位置开始移动,在移动过程中根据位置估计和地图进行自身定位,同时在自身定位的基础上建造增量式地图，实现机器人的自主定位和导航。

是实现哨兵机器人的关键算法。

SLAM又分为激光SLAM、视觉SLAM和多传感器融合SLAM



复现经典的SLAM算法

激光SLAM：gmapping、cartographer等

视觉SLAM：ORB-SLAM2、VINS-Mono、VINS-Fusion

二者结合：LIMO（LiDAR-Monocular Visual Odometry）、VLOAM（Visual-lidar Odometry and Mapping: Low-drift, Robust, and Fast）




### 网络知识

科学上网（直播讲解）

什么是局域网、网关、IP地址

[IP 基础知识全家桶 | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/network/4_ip/ip_base.html#前菜-ip-基本认识)

[ping 的工作原理 | 小林coding (xiaolincoding.com)](https://xiaolincoding.com/network/4_ip/ping.html#ip协议的助手-icmp-协议)



下面内容自行了解：

OpenWrt、Padavan操作系统

实验室网络环境搭建



### 相机

基本知识

​	`相机`是机器人的眼睛。和人眼的成像原理一样，相机通过`镜头`汇聚光束使他们聚集在一块半导体感光元件上（相当于视网膜）从而产生可供读取的数据。随后图像随着数据线传如miniPC等运算平台（视网膜刺激视神经传到神经冲动到大脑）。时下的感光单元主要分为两种：**CMOS**和**CCD**

​	`镜头`就像人的晶状体，不同的是，人的晶状体是可以改变焦距但像距固定，而一般使用的工业相机和USB相机配套的镜头**是定焦但可以调节像距的**。不过在小孔成像模型中，我们把透镜看作被压缩成一个点的大小，因此在这种情况下我们认为**焦距和像距等同**

​	镜头是一块凸透镜，在他的两边各有一个焦点，焦点即所有平行进入透镜的光线的汇聚点。不同焦距的镜头其视距和视野范围不同，一般来说，`视距大（看的远）的镜头，其视野范围小（可视角小）；而视距短（看的近些）的镜头，视野范围大`

​	在比赛中，我们一般给步兵机器人配置广角镜头（适用**近战**，可视角广）或是**6mm**的镜头（中庸的选择，**兼顾长短**）。打击能量机关的步兵机器人会选择8mm、12mm的**长焦镜头**来获得更好的远距离成像效果。哨兵机器人可能会配置两个相机，分别搭载广角镜头和中短焦镜头，广角用于“广撒网”，对敌方目标进行大致的定位，之后交由另外一个相机进行精确的定位。

​	由于凸透镜**本身的性质**和镜头制造的**工艺**问题，使得光线在通过镜头时无法保持物体在空间中原本的位置关系而发生**畸变**，好在这些畸变都能够通过数学建模并由反向解算而得到还原。这需要我们通过**相机标定**来去除这种畸变以便还原图像中物体的真实位置。畸变主要分为切向畸变和桶型畸变，我们可以利用标定板和畸变的数学关系来进行相机标定



相机成像原理（小孔成像模型）

<img src="./md_pic/8f4d23a0d7ac4c7dbcbc104e422e7429.png" width="70%" height="70%" alt="小孔成像模型" align=center />



[计算机视觉之相机成像几何模型（原理）与相机标定内参和外参 几何成像模型](https://blog.csdn.net/Mr____Cheng/article/details/105270124)

[相机成像原理](https://blog.csdn.net/weixin_34910922/article/details/121618548)



相机标定

为什么标定？

​	获取相机内参，即获取现实物理世界与相机像素点的映射关系



制作标定板

​	**标定板**主要的作用是为校正镜头畸变、确定物理尺寸和像素间的换算关系，以及确定空间物体表面某点的三维几何位置与其在图像中对应点之间的相互关系

<img src="./md_pic/1684044498841.png" width="70%" height="70%" alt="标定板" align=center />



[ROS2单目相机标定教程 ](https://zhuanlan.zhihu.com/p/488925991)



## 运行环境



### 网络环境

`局域网`

<img src="./md_pic/1684012535618.png" width="400" height="200" alt="右手系" align=center />

获取NUC IP的方法：

* 用HDMI线插显示器，打开终端

  ```shell
  ifconfig   --Linux
  ipconfig   --Windows
  ```

* 进入Vanguard网关192.168.1.1 查看主机对应IP





启动方法有3种：

* 用HDMI线插显示器
* 利用SSH连接
* 利用VS Code连接（本质还是SSH）

`SSH`

在 Linux 系统上 SSH 是非常常用的工具，通过 SSH Client 我们可以连接到运行了 SSH Server 的远程机器上。SSH Client 的基本使用方法是：

```shell
ssh user@remote -p port
```

- user 是你在远程机器上的用户名，如果不指定的话默认为当前用户
- remote 是远程机器的地址，可以是 IP，域名，或者是后面会提到的别名
- port 是 SSH Server 监听的端口，如果不指定的话就为默认值 22

步兵NUC连接方法（在Windows cmd下）：

```shell
#输入
ssh fate@192.168.1.113
#输入密码fate  输入密码时看不见
fate@192.168.1.113's password:
fate
```

成功进入NUC的终端，纯命令行操作



### Ubuntu 20.04

* Docker
* ROS2 Humble



Docker默认已运行

进入Docker容器

```shell
docker exec -it vg_vision_container /bin/zsh
#如果卡住 Ctrl + C 就可以进去了
```



启动自瞄

```shell
ros2 launch rm_vision_bringup vision_bringup.launch.py
```



启动foxglove bridge

``` shell
ros2 launch foxglove_bridge foxglove_bridge_launch.xml
```



打开Foxglove Studio

Foxglove Studio是基于Web技术开发的全平台通用的可视化利器。我们可以很方便地、直观地看到数据并进行开发与调试。

`打开连接`->`修改localhost为NUC IP`








X11转发（WSL+SSH图像化页面显示）

自行了解


TODO 部署指南





Written by 龚易乾