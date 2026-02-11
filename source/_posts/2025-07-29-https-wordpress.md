---
title: 'Https WordPress建站完全指南'
date: 2025-07-29 08:58:49
tags: [Web]
published: true
cover: /post-images/2025-07-29-https-wordpress.png
---

记录下自己的建站过程

## 1 Requirements & Preparations 

安装apache2,php

<pre class="wp-block-code"><code>sudo apt install apache2 php8.2</code></pre>

访问 服务器ip:80（http），可看到apache2欢迎界面

apache2默认网站目录位于/var/www/html，默认配置文件位于/etc/apache2/sites-enabled下的json文件

## 2 安装WordPress

WordPress官网：[博客工具、发布平台和内容管理系统 – WordPress.org China 简体中文][1]

点击&#8221;获取WordPress“，下载WordPress，全部解压至/var/www/html，并查看安装指南

安装mariadb数据库

<pre class="wp-block-code"><code>sudo apt install mariadb-server
mariadb --version</code></pre>

若出现最后出现mariadb版本号，即为安装成功

phpmyadmin官网：[phpMyAdmin][2]

点击Download，建议选择[phpMyAdmin-\****-all-languages.zip][3]，下载后解压至/var/www/html/phpmyadmin

后面mariadb，wordpress的配置步骤建议参考[树莓派+wordpress搭建个人网页/博客 &#8211; 知乎][4] 1-3节内容（不用管nginx配置，我们使用的是apache2，兼容php，无需额外配置）

## 3 搭建内网穿透，实现外网访问 

### 3.1 ngrok配置（不建议使用） 

最开始使用ngrok（现在看来十分不推荐！！！一个月1GB流量限制，https经常会出莫名其妙的问题，不利于NextCloud文件同步）：<https://dashboard.ngrok.com/>

下载ngrok linux客户端（超级慢）

<pre class="wp-block-code"><code>sudo apt install ngrok</code></pre>

点击getting started，并选择Raspberry Pi，找到<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async" src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image-5.png" alt="" /></figure> 

复制下方指令并执行以绑定账户

回到官网，点击左边Domains，点击NewDomain，会生成个人域名（超长难记），回到Setup&Installation，选择Raspberry Pi，找到<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async" src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image-6.png"/></figure> 

运行下方指令即可从外部域名访问网站

### 3.2 通过ChmlFrp+Cloudns域名或ChmlFrp免费域名 

<ol class="wp-block-list">
  <li>
    ChmlFrp官网：<a href="https://www.chmlfrp.cn/"></a><a href="https://www.chmlfrp.cn/">ChmlFrp | 内网穿透 &#8211; 免费,高速,稳定,不限流量的端口映射工具。</a>
  </li>
  <li>
    Cloudns（可访问，但添加域名与解析记录需要魔法上网）：<a href="https://www.cloudns.net/main/lang/chs/">ClouDNS: 控制面板</a>
  </li>
</ol>

#### 3.2.1 安装frp客户端

点击 隧道管理=>软件下载 选择 Linux，复制arm64地址，下载，解压至/home/自己的用户 文件夹，重命名为ChmlFrp

#### 3.2.2 配置隧道 

点击 隧道管理=>隧道列表=>添加隧道，选择可建站非大陆节点（大陆节点需要工信部备案）

<ol class="wp-block-list">
  <li>
    端口类型 http
  </li>
  <li>
    内外端口 80
  </li>
  <li>
    域名类型 免费域名（正在维护）/自定义域名（先阅读3.2.2.1！）
  </li>
</ol>

记住此处CNAME解析域名（不同节点域名不同)：  
<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async" src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image-7.png" /></figure> 

创建完成后，点击右下角小扳手，获取配置代码，复制frpc.ini配置，并将其写入frpc客户点目录下的frpc.ini

##### 3.2.2.1 获得Cloudns免费域名（需要魔法）

点击右上角国旗更改语言，注册登录账户，点击DNS托管下的创建区域=>免费区域，创建域名后，会进入如图界面<figure class="wp-block-image size-large">

<img loading="lazy" decoding="async" width="1024" height="409" src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image-8-1024x409.png" /></figure> 

点击右下角添加新记录

<ol class="wp-block-list">
  <li>
    类型：CNAME
  </li>
  <li>
    主机：自定义即可（要填在3.2.2中的域名）
  </li>
  <li>
    指向到：3.2.2中记住的解析地址
  </li>
</ol>

###### 3.2.2.1.1 拓展：使用Cloudflare双向解析 

[Cloudflare Dashboard | Manage Your Account][5]

在Cloudns仪表盘中删除所有默认NS记录，保留CNAME记录

按照Cloudflare Dashboard指引创建新NS记录，并在DNS=>记录 中加入相同的CNAME记录，可开启其他优化选项

#### 3.2.3 设置frp客户端自启动

利用crontab自动任务实现

<pre class="wp-block-code"><code>sudo crontab -e</code></pre>

写入以下指令：

<pre class="wp-block-code"><code>@reboot sudo nohup sudo ngrok ***** //ngrok指令
30/* * * * * sudo nohup sudo ChmlFrp客户端目录/frpc -c frpc.ini目录</code></pre>

Ctrl+O 回车保存 ctrl+x 退出

### 3.3 使用Cloudflare Tunnel+ClouDNS免费域名 

申请免费域名后，按照Cloudflare指引配置NS服务器

打开个人主页，点击Zero Truse，选择网络->Tunnels，添加Tunnel，并安装Cloudflare客户端，配置端口

注意！ClouDNS需要双向解析！推荐按照图片配置：  
<figure class="wp-block-image size-large is-resized">

<img loading="lazy" decoding="async"  src="https://www.fc.cloudns.ch/wp-content/uploads/2025/08/image-9-edited.png"/></figure> 

Cloudflare中添加CNAME解析，域名为resolve，目标：resolve.cloudflare.182682.xyz

（加速IP）

## 4 启用https访问 

### 4.1 使用Let's Encrypt免费SSL证书 

我们使用Certbot进行签名

<pre class="wp-block-code"><code>sudo apt install certbot</code></pre>

安装好后执行

<pre class="wp-block-code"><code>sudo certbot --apache</code></pre>

选择你要签名的网站，回车，经过一系列杂七杂八的自动验证后会自动申请到SSL证书，并提供https的apache2配置，这里我们就可以更新ChmlFrp的隧道配置了

<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
  <p>
    如果验证失败，请检查你的网站是否能通过公网http访问到
  </p>
</blockquote>

<ol class="wp-block-list">
  <li>
    协议从https改为http
  </li>
  <li>
    端口从80改为443
  </li>
</ol>

之后更新frpc.ini配置，并重启apache2服务

<pre class="wp-block-code"><code>sudo systemctl restart apache2</code></pre>

https就成功启用了

### 4.2 使用Cloudflare

启用Cloudflare SSL/TLS加密即可，无需任何额外配置

 [1]: https://cn.wordpress.org/
 [2]: https://www.phpmyadmin.net/
 [3]: https://files.phpmyadmin.net/phpMyAdmin/5.2.2/phpMyAdmin-5.2.2-all-languages.zip
 [4]: https://zhuanlan.zhihu.com/p/165123275
 [5]: https://dash.cloudflare.com/