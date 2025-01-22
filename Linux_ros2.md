# ros2初步

--- 

## 1.环境配置
### 1.1 安装ROS2

输入以下命令安装ros2
```shell
wget http://fishros.com/install -O fishros && . fishros
```
验证是否安装成功
```shell
echo $ROS_DISTRO
```
若返回值为`foxy` `humble` `jazzy`等则安装成功

### 1.2安装ROS开发必要的工具
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
ros2_control
```shell
sudo apt install ros-$ROS_DISTRO-ros2-control
```
ros2_controllers
```shell
sudo apt install ros-$ROS_DISTRO-ros2-controllers
```
gazebo_ros2_control
```shell
sudo apt install ros-$ROS_DISTRO-gazebo-ros2-control
```

一键安装全部：
```shell
sudo apt install ros-$ROS_DISTRO-tf-transformations ros-$ROS_DISTRO-rqt-* ros-$ROS_DISTRO-robot-state-publisher ros-$ROS_DISTRO-joint-state-publisher ros-$ROS_DISTRO-xacro ros-$ROS_DISTRO-gazebo-* ros-$ROS_DISTRO-ros2-control ros-$ROS_DISTRO-ros2-controllers -y
```
## 3.ROS2常用命令

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
---
## 4.ROS2常用工具
### ROS2 Control
以下是 **ROS 2 control** 每个命令的示例代码块，供你参考使用：  

 1. `list_controller_types`
    列出可用控制器类型及其基类：  
    ```bash
    ros2 control list_controller_types
    ```
 2. `list_controllers`
    列出当前加载的控制器及其状态：  
    ```bash
    ros2 control list_controllers
    ```
 3. `list_hardware_components`
    列出可用硬件组件：  
    ```bash
    ros2 control list_hardware_components
    ```
 4. `list_hardware_interfaces`
    列出可用的指令接口和状态接口：  
    ```bash
    ros2 control list_hardware_interfaces
    ```
5. `load_controller`
    加载指定的控制器：  
    ```bash
    ros2 control load_controller <controller_name>
    ```
    **示例**：加载名为 `joint_trajectory_controller` 的控制器：  
    ```bash
    ros2 control load_controller joint_trajectory_controller
    ```
6. `reload_controller_libraries`
    重新加载控制器库：  
    ```bash
    ros2 control reload_controller_libraries
    ```
7. `set_controller_state`
    设置控制器的状态（如 `active` 或 `inactive`）：  
    ```bash
    ros2 control set_controller_state <controller_name> <state>
    ```
    **示例**：将控制器 `joint_trajectory_controller` 设置为 `active` 状态：  
    ```bash
    ros2 control set_controller_state joint_trajectory_controller active
    ```
8. `set_hardware_component_state`
    设置硬件组件的状态：  
    ```bash
    ros2 control set_hardware_component_state <hardware_component_name> <state>
    ```
    **示例**：将硬件组件 `robot_arm` 设置为 `active` 状态：  
    ```bash
    ros2 control set_hardware_component_state robot_arm active
    ```
9. `switch_controllers`
    启动和停止指定控制器，实现控制器切换：  
    ```bash
    ros2 control switch_controllers --start-controllers <controller_name> --stop-controllers <controller_name> [--strict] [--timeout <seconds>]
    ```
    **示例**：启动 `joint_trajectory_controller`，停止 `position_controller`：  
    ```bash
    ros2 control switch_controllers --start-controllers joint_trajectory_controller --stop-controllers position_controller
    ```
10. `unload_controller`
    卸载指定控制器：  
    ```bash
    ros2 control unload_controller <controller_name>
    ```
    **示例**：卸载名为 `joint_trajectory_controller` 的控制器：  
    ```bash
    ros2 control unload_controller joint_trajectory_controller
    ```

11. `view_controller_chains`
    生成链式控制器图表并保存为 PDF 文件：  
    ```bash
    ros2 control view_controller_chains
    ```
    **输出**：图表会保存到 `/tmp/controller_diagram.gv.pdf`。

    每个命令均可通过追加 `-h` 获取详细帮助，例如：  
    ```bash
    ros2 control switch_controllers -h
    ```

### moveit2

官方文档链接：[moveit2](https://moveit.picknik.ai/humble/index.html)


如果你在虚拟机环境输入以下命令出现了错误：
```shell
sudo rosdep init
```
可以尝试以下命令：
进入/etc文件夹
```shell
cd /etc
```
修改hosts文件
```shell
sudo gedit hosts
```
在末尾添加以下内容
```shell
151.101.84.133 raw.githubusercontent.com
```
启动moveit2 assistant
```shell
ros2 run moveit_setup_assistant moveit_setup_assistant
```
moveit2 源码编译
```shell
cd ~/ws_moveit2
colcon build --mixin release --parallel-workers 1
```

