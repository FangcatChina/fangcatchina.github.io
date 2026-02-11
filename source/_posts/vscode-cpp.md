---
title: '如何在Visual Studio Code中配置C/C++开发环境'
date: 2022-04-12 09:01:15
tags: [C++,Visual Studio Code]
published: true
cover: /post-images/vscode-cpp.jpeg
---
# 概述
之前用的IDE是Dev-C++，感觉界面比较难看，所以就想在VSCode里配置一个C++开发环境。
# 准备
TDM-GCC编译器（啥版本都行）
# 开始
## 下载扩展
在VSCode扩展市场中下载下列扩展
|扩展名称|作者|作用|
|---------|-----|----|
C/C++|Microsoft|语法高亮、代码提示等基础功能
C/C++ Extension Pack|Microsoft|开发工具包
C/C++ Compile Run|danielpinto8zz6|编译运行
> 官方扩展配置太复杂，所以选用了更简单的扩展
## 开始配置
打开设置，分别找到扩展>Compile Run Configuration，在C-Compiler中填入C语言编译器（编译器路径/bin/gcc.exe），在Cpp-Compiler中填入C++编译器（编译器路径/bin/g++.exe），其他的可以默认，有特殊需求的话可以看一看扩展信息（C/C++ Compile Run的）
## 测试
我们写个简单的程序测试一下
```
#include <bits/stdc++.h>
using namespace std;
int main(){
    cout << "Hello,world!";
    return 0;
}
```
按下**F6或F7**进行编译
```
Hello,world!
```
好耶ヾ(✿ﾟ▽ﾟ)ノ！

