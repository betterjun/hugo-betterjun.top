+++
date = "2017-05-28T23:12:00+08:00"
draft = false
title = "OSG笔记-1-编译安装"
tags = ["osg", "OpenSceneGraph", "编译"]
categories = ["学习总结"]
+++


## 1. 获取

### 1.1. 快速开始

快速开始,对整个流程的介绍，见这里<http://www.openscenegraph.org/index.php/documentation/getting-started>。

### 1.2. 下载

下载源码编译，
<http://www.openscenegraph.org/index.php/download-section/stable-releases>。

### 1.3. 编译

所有平台的编译入口在这里，<http://www.openscenegraph.org/index.php/documentation/platform-specifics>。

windows平台编译方法在这里，<http://www.openscenegraph.org/index.php/documentation/platform-specifics/windows/37-visual-studio>。

### 1.4. 获取样例数据

在后面运行OSG的示例程序时，需要用到样例数据，在这里下载，<http://www.openscenegraph.org/index.php/download-section/data>。

### 1.5. 执行样例程序

执行样例程序，需要设置环境变量OSG_FILE_PATH，具体见，<http://www.openscenegraph.org/index.php/documentation/guides/user-guides/113-running-the-examples>。


## 2. 新建工程编译

官方建议单独新建工程，不要和OSG的工程混在一起。同时将OpenSceneGraph\applications\osgViewer\osgViewer.cpp拷贝添加到新工程中，然后设置编译环境，验证编译通过。

### 2.1. 工程设置

建议设置如下环境变量

>`OSG_ROOT points to the base of the OSG file structure (the directory that contains include, src etc. subdirectories)`
>
>`OSG_BIN_PATH = %OSG_ROOT%\bin`
>
>`OSG_INCLUDE_PATH = %OSG_ROOT%\include`
>
>`OSG_LIB_PATH = %OSG_ROOT%\lib`
>
>`OSG_SAMPLES_PATH = %OSG_ROOT%\share\OpenSceneGraph\bin`
>
>`OSG_FILE_PATH = ???\OpenSceneGraph-Data-X.X`
>
>`Then, add %OSG_BIN_PATH% and %OSG_SAMPLES_PATH% to your PATH environment variable. That way, not only can you run examples easily, but the latest DLLs will always be found. When starting an application, Windows looks for the required DLLs first in the executable's directory, then in the PATH.`

然后再在新建的vs工程目录中，增加如下设置

>`Properties - C/C++ - General - Additional Include Directories = $(OSG_INCLUDE_PATH)`
>
>`Properties - C/C++ - Preprocessor - Preprocessor Definitions = WIN32;_WIN32;NDEBUG`
>
>`Properties - Linker - General - Additional Library Directories = $(OSG_LIB_PATH)`
>
>`Properties - Linker - Input - Additional Dependencies = (any OSG library your project needs - for example: OpenThreads.lib osg.lib osgDB.lib osgFX.lib osgGA.lib osgManipulator.lib osgParticle.lib osgShadow.lib osgSim.lib osgTerrain.lib osgText.lib osgUtil.lib osgViewer.lib)`

debug版本的库，需要在尾部上增加一个d，比如OpenThreadsd.lib osgd.lib osgDBd.lib osgFXd.lib osgGAd.lib osgManipulatord.lib osgParticled.lib osgShadowd.lib osgSimd.lib osgTerraind.lib osgTextd.lib osgUtild.lib osgViewerd.lib。

上面几个设置，我自己采用的是INSTALL工程的输出目录，可以把debug和release自己手动再分开。

### 2.2. 配置选项说明

对“解决方案配置”的选项，Release和MinSizeRel，Release是多线程编译，输出的二进制文件不能做到最小化，MinSizeRel是单线程编译，输出的文件可以做到最小化，但是非常慢。
