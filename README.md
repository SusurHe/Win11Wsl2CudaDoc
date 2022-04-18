Win11 + WSL2 + cuda + TensorFlow的深度学习开发环境的搭建
===

## 前言

前段时间升级了windows台式机，由于双系统实在过于麻烦，而且现在wsl2已经很成熟了， 可以带来比较好的windows上的开发体验， 但是在环境准备过程中还是有不少坑的， 更具网上的资料和官方文档整理一下, 该文档仅代表win11的环境，win10是否适用不清楚

## 系统环境

- 硬件
  - 12th Gen Intel(R) Core(TM) i7-12700KF
  - 32G 3600
  - RTX3070ti
- 系统
  - Windows11 21H2
  - WSL2
  - Ubuntu2004

## WSL2 Install

1. 开启Windows功能： 系统设置 -> 应用 -> 可选功能 -> 最下边的 「更多 Windows 功能」 -> 找到并勾选 「Hyper-V」和「适用于 Linux 的 Windows 子系统」-> 点击确定
   
 ``` sh
 # 命令行开启虚拟化(如果下面安装过程中报错的话)
 bcdedit /set hypervisorlaunchtype auto
 ```  

***WRAN: 重启电脑***

![图 1](images/fb61fec2769e8dfbd477f0033282bdad83d16436866f0ff128cde8db96fac49c.png)

1. 配置和安装wsl2和ubuntu

``` sh
# Wran: 以管理员身份运行terminal
# 1. 设置版本为wsl2
wsl --set-default-version 2
# 更新wsl
wsl --update
# 查看可安装的Linux版本
wsl --list online
# 安装Ubuntu20.04
wsl --install -d Ubuntu-20.04
```
3. 安装完成后会自动启动Ubuntu, 然后按照提示配置基本信息
   
## Cuda Install

  *首先在windows上去官网下载并安装(更新)显卡驱动*
  
  windows上显卡驱动安装成功以后wsl2下的ubuntu可以使用`nvidia-smi`查看gpu的运行状态(以管理员启动terminal)
![图 2](images/84ce32d94db59993e6ef1e89eb93025aeeefe541d2dcdbb070659df31b1a6cfe.png)  

### 安装Cuda

1. 官方cuda包安装