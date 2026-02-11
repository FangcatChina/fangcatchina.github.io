---
title: 'Python库的创建'
date: 2021-03-01 20:11:50
tags: [Python]
published: true
cover: /post-images/python-package.webp
---
# 概要
最近突发奇想，想用Python做一个库发到Pypi上，就到网上找了一篇教程，下面跟大家分享一下（转载，有较大的改动，原文在文末）
## 准备工作
必须安装Python3，并确保可以使用pip工具！CMD中执行：
``` 
pip install --user --upgrade setuptools wheel
pip install --user --upgrade twine
 ```
## 注册Pypi账号
[http://pypi.org](http://pypi.org)
## 编写Python库程序（单独文件夹中）
不再赘述
## 打包并上传
在文件夹下创建setup.py，并写入以下代码</p>

```
import setuptools

with open("README.md", "r") as fh:
  long_description = fh.read()

setuptools.setup(
  name="库名",
  version="版本",
  author="作者",
  author_email="邮箱",
  description="简介",
  long_description=long_description,
  long_description_content_type="text/markdown",
  url="github开源地址",
  packages=setuptools.find_packages(),
  classifiers=[
  "Programming Language :: Python :: 3",  #Python版本
  "License :: OSI Approved :: MIT License",  #开源许可
  "Operating System :: OS Independent",  #系统要求
  ],
)
```
创建README.md，写入项目详细信息（Markdown格式），创建licence.md，写入开源许可证内容
CMD cd到库文件夹，输入以下指令（注意，最后一步会要求输入Pypi账号密码）：
```
python setup.py sdist bdist_wheel
python twine upload dist/*
```
## 测试安装库
CMD输入指令
```
pip install 库名
```
如果安装成功了，就说明我们的库上传成功了
原文：[https://zhuanlan.zhihu.com/p/60836179](https://zhuanlan.zhihu.com/p/60836179)