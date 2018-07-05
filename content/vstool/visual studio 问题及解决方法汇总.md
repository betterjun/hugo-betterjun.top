+++
title = "visual studio编译错误解决"
draft = false
date = "2018-07-05T10:27:49+08:00"
tags = ["visual studio", "vs编译错误", "grpc"]
categories = ["学习总结"]
+++


## 1. vs express 2017打开sln工程文件，所有项目加载失败，不能编译。

### 表现：

`
使用grpc，通过cmake生成的vs工程文件，vs express 2017打开后，全都是加载失败，报下面的错误

D:\code\grpc\grpc\bin-x86\ALL_BUILD.vcxproj : error  : 无法读取项目文件ALL_BUILD.vcxproj”。
D:\code\grpc\grpc\bin-x86\ALL_BUILD.vcxproj(52,5): 未找到导入的项目D:\code\grpc\grpc\bin\ALL_BUILD.dir\nasm.props”。请确认 <Import> 声明中路径正确，且磁盘上存在该文件。
D:\code\grpc\grpc\bin-x86\INSTALL.vcxproj : error  : 无法读取项目文件INSTALL.vcxproj”。
D:\code\grpc\grpc\bin-x86\INSTALL.vcxproj(52,5): 未找到导入的项目D:\code\grpc\grpc\bin\INSTALL.dir\nasm.props”。请确认 <Import> 声明中的径正确，且磁盘上存在该文件。
`

### 解决方法：

将项目文件打开，找到对应的行，把xml文件中的import一行删除掉，保存重新编译，就可以解决。


## 2. git clone/checkout的文件报编译错误。

### 表现：

其他同事正常编译通过的代码，git提交后，在另一台机器再clone或checkout，就会报各种编译错误，全为语法错误，都是windows机器。分析错误原因，猜测可能是有中文注释，编码问题，有特殊字符导致的。将部分中文删除后，能消除部分编译错误。后来发现，**上一行为中文注释，下一行是代码，就容易报错误，在注释的结尾，增加一行空格，再编译，也可以消除报的错误。** 后来再和正常编译的机器上，比较代码，发现**编译正常那边是回车换行分割，编译错误的是换行分割**。基本确定是vs对不同行分隔符的处理有有问题。


### 解决方法：

后来重装git，发现git对文本文件换行有个设置选项，是否转换换行符，具体如下图
![git换行符转换](../git_line_ending_conversion.png)

windows上建议选择上图的第一种。命令行执行 git config -l 也可以查看当前设置，如下
>`core.autocrlf=true`

通过命令行或者tortorisegit等gui工具也可以重新设置此参数。

