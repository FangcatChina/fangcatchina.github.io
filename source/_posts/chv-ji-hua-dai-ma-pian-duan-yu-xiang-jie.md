---
title: 'Chv计划代码片段与详解'
date: 2021-03-02 19:41:07
tags: []
published: false
hideInList: true
feature: 
isTop: false
---

# 本文章已失效！！  Chv计划已经取消
## 什么是Chv计划？
Chv计划是我为了使用户更容易地自己创建应用（无需再创作，未来实现程序保存功能）而编写的语言。只有在Chiver与FCXOS中使用，暂时还未开放使用（三月下旬开启内测）。
## Chv计划预API
### 1.output
`output [内容]`
输出指定内容。
### 2.ask
`ask [问题]`
询问用户问题，返回值存入`get`。
### 1-1 代码示例
```
output Hello,Chvlang!
ask What's your name?
output get
```
### 3.getout分隔符
`getout`
完成循环或选择片段（相当于Python中的缩进）。
### 4.if
`if [条件]`
如果条件成立，执行下面的代码（被'getout'分割）。
### 3-4 代码示例
```
ask Enter-1
if get = 1
output You-entered-1
getout
output OK
```
这段代码表示如果获得的答复是1，那么输出You-entered-1，否则不输出，不管是否输入了1，最后输出OK。