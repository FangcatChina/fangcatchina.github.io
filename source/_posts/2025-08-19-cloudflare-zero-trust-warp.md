---
title: '不绑卡，解锁Cloudflare Zero Trust'
date: 2025-08-19 09:01:56
tags: [Web]
published: true
cover: /post-images/2025-08-19-cloudflare-zero-trust-warp.png
---
众所周知，Cloudflare WARP可以用来安全加密互联网连接，而WARP分为二这几种类型：

<ul class="wp-block-list">
  <li>
    WARP 1G流量
  </li>
  <li>
    WARP+ 需要特定渠道获得License，1923837100 GB，基本够用
  </li>
  <li>
    Zero Trust 几乎无限流量
  </li>
</ul>

而获取Zero Trust正常来讲需要绑卡，但是，我们今天用特殊方法获取Zero Trust

打开Cloudflare Zero Trust，不要理会绑卡提示，打开左边侧栏=>Gateway=>概述

拉到下方提示，点击：<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async"  src="https://www.fc.cloudns.ch/wp-content/uploads/2025/08/image.png" /></figure> 

按照提示操作，注意！在这个地方：<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async"  src="https://www.fc.cloudns.ch/wp-content/uploads/2025/08/image-1.png" /></figure> 

不建议使用默认邮箱，容易注册失败！建议自己添加一个

**题外话：启用MASQUE协议**

连接完别退出！点这个跳过绑卡验证：  
<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async"  src="https://www.fc.cloudns.ch/wp-content/uploads/2025/08/image-2.png"  /></figure>