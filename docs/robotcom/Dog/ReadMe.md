# 简单介绍

## 套件说明
本赛项使用套件为[宇树科技](https://www.unitree.com)开发的四足仿生机器人，型号为A1和Go1。
其中社团中主要使用的版本为A1

## 开发涉及内容

### 运动控制（C++/Python）

- 在开发过程中，我们使用由宇树科技提供的`unitree_legged_sdk`固件进行高层命令开发。
  - 具体使用请参考：[Github仓库](https://github.com/unitreerobotics/unitree_legged_sdk)

- 在开发中使用`C++`作为开发语言
  - PS：Go1官方支持`Python`作为开发语言。
  - PPS：社团内部有一份自行打包的`Python SDK`，请酌情使用。

注意！！！ A1仅支持`3.3.4`版本一下的`unitree_legged_sdk`

### 视觉识别

- A1上提供的摄像头为`Intel RealSense D435i`深度摄像头，一般是使用