# Linux 开发环境配置(x86)
---
## 1. 通用部分
### 1.1 C/C++
输入以下命令安装c++编译器
```shell
sudo apt install build-essential
```
验证是否安装成功
```shell
g++ --version
```
### 1.2 Cmake
输入以下命令安装cmake
```shell
sudo apt install cmake
```
验证是否安装成功
```shell
cmake -version
```
### 1.3 Git
输入以下命令安装git
```shell
sudo apt install git
```
验证是否安装成功
```shell
git --version
```
---
## 2.x86
---
## 3.arm64

---

## 4.ros2
###  4.1安装ros2
输入以下命令安装ros2
```shell
wget http://fishros.com/install -O fishros && . fishros
```
验证是否安装成功
```shell
echo $ROS_DISTRO
```
若返回值为`foxy` `humble` `jazzy`等则安装成功

### 4.2安装ROS开发必要的工具
mrpt2
```shell
sudo apt install ros-$ROS_DISTRO-mrpt2 -y
```
transformers3d
```shell    
sudo apt install ros-$ROS_DISTRO-tf-transformations
sudo pip3 install transforms3d
```
rqt所有组件
```shell
sudo apt install ros-$ROS_DISTRO-rqt-*
```
机器人信息发布
```shell
sudo apt install ros-$ROS_DISTRO-robot-state-publisher
```
关节信息发布
```shell
sudo apt install ros-$ROS_DISTRO-joint-state-publisher
```
xacro
```shell
sudo apt install ros-$ROS_DISTRO-xacro
```
gazebo
```shell
sudo apt install ros-$ROS_DISTRO-gazebo-*
```
gazebo_ros
```shell
sudo apt install ros-$ROS_DISTRO-gazebo-ros-*
```
需要在每次打开终端时运行以下命令
```shell 
source /usr/share/gazebo/setup.bash
```