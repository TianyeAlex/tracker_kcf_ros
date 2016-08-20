# tracker_ws
基于ros下应用深度相机的kcf追踪算法实现

#开发环境：

Ubuntu 14.04 + ros indigo

#传感器：

深度相机（Xtion pro live）

#实验平台：

Aiibot



#运行：

1.首先启动ros环境：

$roscore

2.运行ros打开深度相机的节点，发出可播放深度图像和rgb图像的topic：

$roslaunch openni_launch openni.launch

3.查看ros的topic列表中是否有深度图像和rgb图像的topic：

$rostopic list

4.编译：

$catkin_make

5.运行：

$rosrun track_pkg kcf_node


