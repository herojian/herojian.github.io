---
layout:     post
title:      "Maven的几个要素"
subtitle:   "ONOS开发过程中的归纳笔记"
date:       2018-06-24
author:     "Ljan"
header-img: "img/post-bg-js-module.jpg"
tags:
    - Maven
---

最近使用ONOS，各个组件以Maven项目的形式管理，在此整理了几个基本的Maven要素
Maven是一个Java项目管理工具，主要用于项目构建、依赖管理、项目信息管理。

## 仓库
**中央仓库 + 镜像仓库 + 本地仓库**

远程中央仓库是保存所有项目的依赖库的默认位置[http://search.maven.org/]。远程仓库位于国外，访问速度较慢，可以到国内的镜像仓库下载相关依赖[maven阿里云中央仓库http://maven.aliyun.com/nexus/content/groups/public/]。

### POM文件和文件结构
* src/main/java/ 源文件目录
* src/main/test/  测试文件目录，里面的文件不会被打包 
* pom.xml 依赖关系、构建、属性等信息

### 坐标和依赖

* 坐标 (groupId/artifactId/version) 表示包在本地仓库中的位置（目录）
gourpId 公司域名反写+项目名，如 com.herojian.l3networking

artifactId 项目名-模块名，如 l3networking-l3route

version 版本号，SNAPSHOT表示不稳定的快照版本

* \<dependences\>...\<\/dependences\>
Maven项目依赖的包的位置，由(groupId/artifactId/version)元组构成

\<scope\>...\<\/scope\> 依赖范围，有测试、编译、运行三种

### 生命周期和插件
maven项目的三个周期：clean+default+site
* 插件目标
* 缺省插件
* 生命周期绑定

### 聚合与继承
* dependencesManagement
* parent
* module

