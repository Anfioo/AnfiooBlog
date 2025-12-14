---
title: Docker操作-镜像操作
published: 2024-04-01
description: "Docker镜像操作-保存、打包为tar、加载tar镜像"
tags: ["Docker","Linux"]
category: Shell
draft: false
---

# Docker 镜像：保存、打包为tar、加载tar镜像
本文主要介绍Docker镜像的保存、打包为tar文件以及从tar文件加载镜像的完整操作流程，方便在不同服务器间迁移镜像，或留存已配置好环境的镜像供后续使用。

## 一、保存Docker镜像
保存镜像的核心目的是将现有容器的状态固化为新镜像，可用于跨服务器部署，或留存已安装依赖、配置好环境的容器，避免重复配置。

### 1.1 查看目标容器ID
首先需要找到要保存的容器对应的ID，执行以下命令列出所有容器：
```bash
docker ps -a
```
该命令会输出所有容器的信息，重点记录目标容器的ID（如示例中的`7ca736d99653`）。

### 1.2 执行镜像保存操作
#### 精简版（仅核心参数）
直接通过容器ID生成新镜像，格式为：`docker commit 容器ID 新镜像名称:版本标签`
```bash
docker commit 7ca736d99653 yolov5:v6.2
```
说明：`yolov5`为镜像仓库名（可自定义），`v6.2`为版本标签（可自定义）。

#### 详细版（含提交信息）
添加提交人、提交说明等信息，便于镜像管理，格式为：`docker commit -a "提交人" -m "提交说明" 容器ID 新镜像名称:版本标签`
```bash
docker commit -a "xiaoming" -m "Update target detection model" 7ca736d99653 yolov5:v6.2
```

### 1.3 验证镜像保存结果
执行以下命令查看本地所有镜像，确认新保存的镜像是否存在：
```bash
docker images
```
若输出结果中能看到`yolov5:v6.2`，则说明镜像保存成功。

## 二、将镜像打包为tar文件
使用`save`命令将已保存的镜像打包为tar格式文件，方便传输和备份，格式为：`docker save -o 输出的tar文件名 镜像名称:版本标签`
```bash
docker save -o yolov5-v6.2.tar yolov5:v6.2
```
执行完成后，当前目录会生成`yolov5-v6.2.tar`文件，即镜像的打包文件。

## 三、从tar文件加载镜像
将打包好的tar文件传输到目标服务器后，使用`load`命令加载镜像，格式为：`docker load -i 待加载的tar文件名`
```bash
docker load -i yolov5-v6.2.tar
```

### 验证加载结果
执行以下命令查看镜像列表，确认加载的镜像是否存在：
```bash
docker images
```
若能看到`yolov5:v6.2`镜像，则说明加载成功。