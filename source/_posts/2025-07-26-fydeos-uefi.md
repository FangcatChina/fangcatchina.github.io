---
title: '用rEFInd-theme-Yours解决FydeOS UEFI安全启动问题 '
date: 2025-07-26 12:33:41
tags: [Operating Systems]
published: true
cover: /post-images/2025-07-26-fydeos-uefi.png
---
**Requirements:**

<ul class="wp-block-list">
  <li>
    能够访问Github
  </li>
  <li>
    DiskGenius
  </li>
  <li>
    BIOS支持64位UEFI（若不支持可参考下载链接中的教程）
  </li>
</ul>

**1.下载**  
必须：[Grub2 Fyde&nbsp;2][1]

<ul class="wp-block-list">
  <li>
    BIOS支持64位UEFI：<a href="https://github.com/M-L-P/Yours-UEFI">Yours UEFI 1</a>
  </li>
  <li>
    不支持：<a href="https://github.com/M-L-P/Yours-LegacyBIOS">Yours LegacyBIOS</a>
  </li>
</ul>

（在此感谢上方Github仓库的贡献者！）  
下载最新Release压缩包并解压

**2.安装EFI文件 （以下以支持64位UEFI为例）**  
打开DiskGenius，选择SYSTEM_DRV分区并打开  
按照以下步骤复制文件：

<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
  <p>
    注意：若想保留Windows原引导，忽略删除EFI\Boot步骤，并将压缩包中Boot中的Bootx64.efi更名为其他名称，否则Windows容易PIN码失效
  </p>
</blockquote>

Yours-UEFI:<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async"  src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image.png" /></figure> 

Grub2-Fyde:  
<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async"  src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image-1.png" /></figure> 

**3.调整引导顺序并安装证书**  
在DiskGenius中转到&#8221;工具=>设置UEFI BIOS启动项&#8221;，按照图示新增/修改原Windows引导项

<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
  <p>
    若不保留Windows原引导，请将启动文件替换为\EFI\Boot\Bootx64.efi
  </p>
</blockquote><figure class="wp-block-image size-full">

<img loading="lazy" decoding="async" src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/屏幕截图-2025-07-21-191433.png"  /></figure> 

点击保存后，勾选“下次启动时…”，或将该启动项移至最前面，关闭电脑  
在BIOS中暂时禁用安全启动（Secure Boot）  
开机后，出现MokManager页面<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async"  src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image-2.png" /></figure> 

选择OK<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async"  src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image-3.png"  /></figure> 

按下任意键

选择Enroll key from disk  
接下来找到ENROLL\_THIS\_KEY\_IN\_MOKMANAGER.cer，回车，选择Continue=>Yes=>Reboot  
在BIOS中开启安全启动后，即可正常进入引导界面<figure class="wp-block-image size-full">

<img loading="lazy" decoding="async" src="https://www.fc.cloudns.ch/wp-content/uploads/2025/07/image-4.png"  /></figure> 

选择FydeOS，回车，之后即可在安全启动下正常使用FydeOS  
之后的引导界面自定义可参考[rEFInd-theme-Yours&nbsp;][2]

 [1]: https://github.com/M-L-P/grub2-fyde
 [2]: https://github.com/M-L-P/rEFInd-theme-Yours