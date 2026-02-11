---
title: '驳林长枫《女友体验Linux》纯小白也能轻松上手?'
date: 2025-10-03 16:03:19
tags: [Operating Systems]
published: true
cover: /post-images/linux-easy.png
---
<blockquote><p>本文主要针对视频中UP主观性过强以及较为夸大的部分提出质疑<br>
视频链接：<a href="https://www.bilibili.com/video/BV1YvenzUEFf">「女友体验Linux」 全程禁用命令行，颠覆刻板印象，纯小白也能轻松上手！</a></p></blockquote> <p><strong>事先声明：我不是Linux黑子，本篇文章于Linux端Gridea编写</strong></p> <h2 id="1-事前准备">1. 事前准备</h2> <p>在视频开头02:45，UP主粗略带过了两句话：</p> <blockquote><p><strong>我</strong>事先腾出了硬盘空间，用Ventoy制作了安装系统所需要的U盘</p></blockquote> <p>安装双系统对普通用户最大的一道坎就是分区与烧录系统U盘，复杂的步骤被一笔带过+甩教程链接，高，实在是高</p> <h2 id="2-系统选择">2. 系统选择</h2> <p>在视频03:04，UP主再一次粗略带过两句话：</p> <blockquote><p>本期视频旨在展现Linux的易用性，所以<strong>我</strong>选择了Linux Mint</p></blockquote> <p>展现易用性的初心是不错的，但是为什么不将系统选择权交给你的女朋友呢？让我们猜一猜她会在纷繁复杂的LInux发行版里选择什么系统，说不定就是你花了1个小时讲完全教程的，安装过程没有图形界面的Arch Linux</p> <h2 id="3-输入法">3. 输入法</h2> <p>视频08:13<br> <em>中文Linux用户的痛点竟然被放到了如此靠后的位置</em></p> <blockquote><p><strong>Linux Mint</strong> <strong>自带</strong>了输入法安装向导</p></blockquote> <p>如果你的女朋友选的不是Linux Mint，这一项完全不成立，她就需要搜索Linux输入法，打开命令行，敲：</p> <pre><code class="hljs sql">sudo apt <span class="hljs-keyword">update</span>
sudo apt <span class="hljs-keyword">install</span> fcitx5 fcitx5-chinese-addons
</code></pre> <p>至此，挑战失败</p> <h2 id="4-软件安装">4. 软件安装</h2> <blockquote><p>视频中4-18均为软件生态相关挑战</p></blockquote> <p>上次视频发布后，很多人喷我：</p> <blockquote><p>用cli比用gui优雅的多！<br>
你埃及把用不用！</p></blockquote> <p>那让我们看看视频中这位用户的表现：手足无措，不知道从哪下载，不知道应该下载哪个版本，不知道AppImage如何设置使用，需要身边UP主的指导<br>
我们大胆设想一下：如果身边没有指导，你需要到互联网上翻看大量教程（可能是纯英文），你还会安装使用Linux吗？如果你喜爱的Adobe全家桶，Canvas可画，etc. 只有网页版和需要重新学习的开源替代品，你真的会为了所谓“开源自由”的理想而牺牲生产力吗？<br>
达芬奇的<strong>依赖缺失</strong>一略而过，反而要换成更难学习的功能没那么丰富Kdenlive，你真的是在展现LInux的易用性吗？<br> <em>依赖缺失的Solution见下贴：<a href="https://forum.blackmagicdesign.com/viewtopic.php?f=38&amp;t=200276">BlackMagic Forum</a>，没用过Linux的各位可以自己读读看，挑战依然失败</em></p> <p>plus，很幸运你女朋友所使用的<strong>国产软件</strong> <strong>均支持Linux&amp;Wayland</strong><br>
无Wayland支持：</p> <ul><li>腾讯会议</li> <li>钉钉</li> <li>ToDesk</li></ul> <p>无Linux支持：</p> <ul><li>网易云音乐（仅有与deepin合作版）</li> <li>爱奇艺</li></ul> <h2 id="5游戏">5.游戏</h2> <p>Proton兼容层性能损耗没提过，兼容性问题没提过，我无话可说</p> <h3 id="总结">总结</h3> <p>视频的初心是不错的，但我并不认为对缺点的一略带过是正确的，评价应该客观，而不应只说一面</p> <blockquote><p>Every coin has two sides</p></blockquote>