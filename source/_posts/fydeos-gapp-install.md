---
title: '如何在FydeOS v20中手动安装Open GApps? '
date: 2025-10-02 16:00:30
tags: [Operating Systems]
published: true
cover: /post-images/fydeos-gapp-install.jpg
---
<blockquote><p>FydeOS论坛页：<a href="https://community.fydeos.com/t/topic/51921">Here</a></p></blockquote> <h2 id="注意笔者电脑架构为x86_64可能因机器而异本帖仅供参考"><strong>注意！笔者电脑架构为x86_64，可能因机器而异，本帖仅供参考</strong></h2> <blockquote><p>在论坛里求助没人鸟🌚还是自己摸索出来的</p></blockquote> <h2 id="requirements">Requirements:</h2> <p>开启开发者模式<br>
关闭根文件系统验证（https://fydeos.com/help/knowledge-base/developer-options/developer-mode/disable-rootfs-verification/ ）</p> <h2 id="1下载">1.下载</h2> <p>已通过gh-proxy加速过的链接：<a href="https://gh-proxy.com/https://github.com/MindTheGapps/13.0.0-x86_64/releases/download/MindTheGapps-13.0.0-x86_64-20231025_201203/MindTheGapps-13.0.0-x86_64-20231025_201203.zip">MindTheGapps-13.0.0-x86_64-20231025_201203.zip</a><br>
未加速链接（默认下载链接）：<a href="https://github.com/MindTheGapps/13.0.0-x86_64/releases/download/MindTheGapps-13.0.0-x86_64-20231025_201203/MindTheGapps-13.0.0-x86_64-20231025_201203.zip">MindTheGapps-13.0.0-x86_64-20231025_201203.zip</a><br> <strong>请保存至我的文件=&gt;下载内容</strong></p> <h2 id="2文件替换">2.文件替换</h2> <p>在桌面上按Ctrl+Alt+T，进入crosh<br>
输入：<br> <strong>（星号部分请自动Tab补全，因机器而异）</strong></p> <pre><code class="hljs bash">shell
sudo -i
<span class="hljs-built_in">cd</span> /home/user/*/MyFiles/Downloads
cp MindTheGapps-13.0.0-x86_64-20231025_201203.zip /home/chronos/fydeos-arc-gapps/arc-rec/download_temp
</code></pre> <h2 id="3大功告成">3.大功告成</h2> <p>按照正常流程安装，不出意外的话会自动跳过下载流程</p>