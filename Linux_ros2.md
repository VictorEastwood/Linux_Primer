# ros2初步
## 1. 安装ros2
输入以下命令安装ros2
```shell
wget http://fishros.com/install -O fishros && . fishros
```
验证是否安装成功
```shell
echo $ROS_DISTRO
```
若返回值为`foxy` `humble` `jazzy`等则安装成功

## 2. 安装ROS开发必要的工具
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
(需要在每次打开终端时运行以下命令)
```shell 
source /usr/share/gazebo/setup.bash
```

## 3. ROS2常用命令
### 3.1 ros2 节点相关
查看所有节点
```shell
ros2 node list
```
查看节点信息
```shell
ros2 node info /node_name
```
### 3.2 ros2 话题相关
查看所有话题
```shell
ros2 topic list
```
查看话题信息
```shell
ros2 topic info /topic_name
```
### 3.3 ros2 服务相关
查看所有服务
```shell
ros2 service list
```
查看服务信息
```shell
ros2 service info /service_name
```
### 3.4 ros2 参数相关
查看所有参数
```shell
ros2 param list
```
查看参数信息
```shell
ros2 param get /param_name
```
### 3.5 运行ros2程序
运行节点
```shell
ros2 run package_name executable_name
```
运行launch文件
```shell
ros2 launch package_name launch_file_name
```

