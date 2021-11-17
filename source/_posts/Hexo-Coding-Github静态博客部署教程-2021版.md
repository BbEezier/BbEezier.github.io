---
title: Hexo + Coding/Github静态博客部署教程 2021版
author: yLTT
avatar: 'http://q1.qlogo.cn/g?b=qq&nk=309002093&s=640'
authorLink: 'https://www.liangzt.top'
authorAbout: 与君共勉!
authorDesc: 与君共勉!
categories: 技术
comments: true
tags:
  - Hexo
  - 博客技术
keywords: 'Hexo,Github'
description: Hexo+Github搭建博客
photos: 'https://api.amogu.cn/api/acg?=2'
abbrlink: 38649
date: 2021-07-30 10:35:39
---

## Hexo + <font color = #50C7D9>Coding</font>/<font color=pink>Github</font> 静态博客部署教程

本篇文章内容由本人实践后亲测有效，遇到奇奇怪怪的BUG建议熟练使用<font color =#E90602>[百度](https://www.baidu.com/)</font>等搜索引擎，如若无果在尝试联系本人=v=

{% aplayer "sweets parade" "花澤香菜" "http://music.163.com/song/media/outer/url?id=809268.mp3" "https://p1.music.126.net/soVzasgTYU36F1uAirKEhQ==/109951165628137310.jpg?" %}

文章共分成4大块构成

- <a href="#bb1">前言</a>
- <a href="#bb2">前期准备工作</a>
- <a href="#bb3">网页配置</a>
- <a href="#bb4">个性化域名设置</a>

### <div id= bb1>前言</div>

​	这个博客之前是直接托管给**Github pages**进行架设的，Github的速度大家都懂的，没有撑杆简直可以说是龟速，而我又给这个博客放置了太多<span class="heimu" title="—————你知道的太多了">**~~二次元~~**</span>图片，导致本就不快的网页加载的更加慢了QAQ

(PS:原先打算是使用**Gitee pages**托管，但是不知道为什么现在Gitee pages暂停了服务)

<a data-fancybox="gallery" href="1.png">![1](1.png)</a>

经过检索，决定使用**Coding**的静态网页托管服务，Coding的节点在中国香港，比起Github的荷兰节点肯定是快上不少。于是折腾了一个上午，把博客的架设全面迁移到了Coding上。

Github和Coding的构建方式其实大同小异，不过要留意的是，Coding虽然是免费的,但他所使用的CDN加速服务是腾讯云的，这一点很蛋疼，我才刚构建不到2个小时给我扣了0.04元(钱虽然少，但积少成多就不可忽视了)而Github的服务则就是完全免费开源的了，大家按需选择

### <div id= bb2>前期准备工作</div>

1. 安装Git
2. 安装Node.js
3. 注册[Coding](https://www.baidu.com/s?wd=%E5%A6%82%E4%BD%95%E6%B3%A8%E5%86%8Ccoding&rsv_spt=1&rsv_iqid=0xcbfd65b1001f0a24&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=80035161_1_dg&rsv_enter=1&rsv_dl=tb&rsv_btype=t&inputT=721&rsv_t=e34fOVbieZJGXEyvljJKErooeYVXrpJPGcYpQOnRAPsI4n2e2KIeHCHz1016O5pr%2FzIJZQ&oq=%25E5%25A6%2582%25E4%25BD%2595%25E6%25B3%25A8%25E5%2586%258Cgithub&rsv_pq=ec306dce000a5b37&rsv_sug3=112&rsv_sug1=84&rsv_sug7=100&rsv_sug2=0&rsv_sug4=1116)/[Github账号](https://www.baidu.com/s?wd=%E5%A6%82%E4%BD%95%E6%B3%A8%E5%86%8Cgithub&rsv_spt=1&rsv_iqid=0xcbfd65b1001f0a24&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=80035161_1_dg&rsv_enter=1&rsv_dl=tb&rsv_btype=t&inputT=1794&rsv_t=d182QqHF8qoLFS1WzXGR6uOWxyJBr3Orwsy%2FCSv%2BbzeFKaklXJUQHkDo0E5DdUDScO7hEg&oq=%25E5%25A6%2582%25E4%25BD%2595%25E6%25B3%25A8%25E5%2586%258Cgithub%2520coding&rsv_pq=f6af8849000ab1fa&rsv_sug3=105&rsv_sug1=77&rsv_sug7=100&rsv_sug2=0&rsv_sug4=2282)
4. 获取ssh公钥
5. 安装Hexo

查阅<font color=#46DDFF>**Hexo**</font>官方文档进行1-2步的配置 

[文档 | Hexo](https://hexo.io/zh-cn/docs/)

### 如何获取ssh公钥

对着文件夹空白处右键，选择 **Git Bash Here** 打开git界面

<a data-fancybox="gallery" href="2.png">![2](2.png)</a>

紧接着，先配置<font color =#A11E00>**用户名**</font>,然后在配置自己的<font color =#A11E00>**邮箱**</font>

(PS:如果你想要双线部署的话Coding和Github的邮箱以及用户名都设置一样会方便很多，但是密钥是可以多个生成的，按需选择吧~)

<pre><code class="language-java">git config --global user.name "xxx"(注册网站的用户名)
git config --global user.email "xxx@xx.com"(注册网站的邮箱,别忘记了双引号哦)</code></pre>
<a data-fancybox="gallery" href="3.png">![3](3.png)</a>

然后继续，在git界面键入

<pre><code class="language-java">ssh-keygen -t rsa -C xxx@xx.com</code></pre>

过后他会弹出几个询问是否设置密码的提示，为了避免麻烦，建议不用设置，直接回车。

<a data-fancybox="gallery" href="4.png">![4](4.png)</a>

这样就算建立成功了

你可以在刚才的文件夹中发现两个新的文件

<a data-fancybox="gallery" href="5.png">![5](5.png)</a>

然后打开到你刚注册好的网站的页面(英文的那个是**Github**,中文的是**Coding**)

<a data-fancybox="gallery" href="6.png">![6](6.png)</a> <a data-fancybox="gallery" href="7.png">![7](7.png)</a>

找到SSH公钥设置>新增公钥

右键，用笔记本来打开**id_rsa.pub**文件，并且将里面的内容从头到脚复制一遍，黏贴到网页中的公钥内容中，标题随便设置，**Coding**记得勾选永久有效，然后点击确定

完成后回到 git界面，输入

<pre><code class="language-java"> ssh -T git@github.com 或者  ssh -T git@coding.net </code></pre>

来测试SSH连接

<a data-fancybox="gallery" href="8.png">![8](8.png)</a>

询问是否连接，输入yes

重新键入测试

<a data-fancybox="gallery" href="9.png">![9](9.png)</a>

如图，即为正确连接

### 安装Hexo

右键电脑桌面计算机>属性>高级系统属性>环境变量

<a data-fancybox="gallery" href="10.png">![10](10.png)</a>

选中Path，打开编辑

将node.js、npm、git都加入进环境变量中

<a data-fancybox="gallery" href="11.png">![11](11.png)</a>

（PS:如果不清楚怎么找到它们的地址，请活用百度等搜索引擎上网查询）

依旧是打开我们熟悉的git

<pre><code class="language-java">cnpm install -g hexo-cli</code></pre>

或者

<pre><code class="language-java">yarn add -g hexo-cli</code></pre>

出现报错的情况，请查看我上一篇文章[《关于Gal主题的一些使用心得》](https://liangzt.top/2021/07/29/%E5%85%B3%E4%BA%8EGal%E4%B8%BB%E9%A2%98%E7%9A%84%E4%B8%80%E4%BA%9B%E4%BD%BF%E7%94%A8%E5%BF%83%E5%BE%97-0/)有写Cnpm和Yarn的下载方式

安装结束后，找到一个合适的文件夹，用作你的博客根目录

在空白处右击鼠标，打开Git界面

键入 <pre><code class="language-java">hexo init</code></pre>

我的根目录就是在一个名为blog的文件夹中

<a data-fancybox="gallery" href="12.png">![12](12.png)</a>

完毕后直接

 <pre><code class="language-java">hexo g  (或者输入hexo generate)</code></pre>

<pre><code class="language-java">hexo s  (或者输入hexo server)</code></pre>

<a data-fancybox="gallery" href="13.png">![13](13.png)</a>

出现如图指令即为成功建立本地端网站，你可以打开 http://localhost:4000  来浏览它

### <div id= bb3>网页配置</div>

**Github**首先我们要新建一个仓库，仓库名必须是你的 **用户名**.github.io 格式如图

<a data-fancybox="gallery" href="14.png">![14](14.png)</a>

我这里报错是因为已经建立过了

**Coding**这边一样，不过只需要仓库名称是用户名就好了，两个网站都一样勾选生成README文件

其中Coding要记得勾选公开仓库，要不然别人是进不了你的网页的

<a data-fancybox="gallery" href="15.png">![15](15.png)</a>

创建仓库完毕后，将你仓库的ssh链接**Clone**一下

<a data-fancybox="gallery" href="16.png">![16](16.png)</a>

<a data-fancybox="gallery" href="17.png">![17](17.png)</a>

然后打开博客根目录的_config.yml文件，直接拉到最下面

<a data-fancybox="gallery" href="18.png">![18](18.png)</a>

如图修改

<pre><code class="language-java">deploy:
  type: git
  repo: 这里复制黏贴上你刚才Clone下来的链接
  branch: main 这里的main还是master取决于你仓库的根目录叫什么，一般来说Github的是main而Coding的就是master</code></pre>

**<u>注意一下冒号后面有一个空格，请别忘记输入</u>**

修改完后我们还可以根据Hexo官网的[配置手册](https://hexo.io/zh-cn/docs/configuration)进行对照配置_config.yml文件

<a data-fancybox="gallery" href="19.png">![19](19.png)</a>

如图，这是我自己的配置

准备完成后，对着你的根目录，也就是_config.yml所在的文件夹右键打开git

依次输入

<pre><code class="language-java">hexo clean</code></pre>

<pre><code class="language-java">hexo g</code></pre>

<pre><code class="language-java">hexo d</code></pre>

<a data-fancybox="gallery" href="20.png">![20](20.png)</a>

<font color =red>**（注意：每次修改根目录的文件后都需要重新进行以上3个步骤(比如发布文章之类的) **</font>

<font color =red>**##Coding除了要重新上传到库之后还要手动到网页托管界面重新部署，这一点也比较麻烦）**</font>

一般的，如果你运行完以上代码后，出现和我差不多一样的界面，恭喜你，你成功的架设了属于自己的博客(此处仅限**Github**用户)可以通过 xxxx（你的用户名）.github.io 进入你的博客查看

**Coding**用户不要着急，你们还有几个步骤呢

让我们回到浏览器，找到网页托管选项

<a data-fancybox="gallery" href="21.png">![21](21.png)</a>

这里建议跟着官方的流程走一遍，因为这一块我以前用腾讯云的时候已经注册过一次了

[网站托管服务 - CODING 帮助中心](https://help.coding.net/docs/pages/intro.html)

成功进入配置后，按照我的格式来进行网页配置

<a data-fancybox="gallery" href="22.png">![22](22.png)</a>

注意这里网站类型要选择**静态网站**，选择**Hexo**会报错

然后确定后开始创建即可，网站建立完成后，右上角可以选择进入访问，上面的链接你可以直接复制黏贴出去。

### <div id= bb4>个性化域名设置</div>

首先你需要拥有一个自己的域名，这里我只推荐通过**阿里云万网**购买，因为我只在这里试过，如果你自己有其他更好的选择，按需即可

关于域名购买的方法，网上有很多全面的教程，这里就不细说了

回到博客根目录下\source，新建一个CNAME文件(**无后缀**注意)使用笔记本打开他，在里面输入你自己的域名，比如我就输入 liangzt.top ，前面不用加任何的东西。然后保存即可

<a data-fancybox="gallery" href="24.png">![24](24.png)</a>

然后重新 **clean g s**老三样一下

<a data-fancybox="gallery" href="23.png">![23](23.png)</a>

这个时候，进入你的阿里云域名管理系统，点击解析

添加记录

<a data-fancybox="gallery" href="25.png">![25](25.png)</a>

照着我这个格式设置就好了，记录值就是你刚才拿到的(xxx.github.io)，一个主机记录是www的一个是@的

如果你的主机记录选择 www ，就可以通过 www.liangzt.top 进行网站访问了，如果只想输入 liangzt.top 来访问网站，那只需要选择@做主机记录即可，我这里两个都进行了设置。
Coding用户，直接在网页托管界面有一个自定义域名，把自己域名填进去就可以了，记得把强制https给勾选上。

##### **Github用户开启强制https的方法**

<a data-fancybox="gallery" href="26.png">![26](26.png)</a>

打开仓库设置，找到pages，将最下面的选项给勾选上（一般来说颁发SSL大概要24小时，所以这个时间段应该还勾选不了，明天记得勾选就好了）

## 总结

因为这个教程大多数是靠我自己看别人的教程琢磨出来的，可能有些地方讲的不太清楚请多见谅，可以去搜索别的Hexo建站教程补充一下，我写这个 一是为了记录下自己建站的一个经历，二就是因为实在没想好要更新什么文章，索性直接把自己这3天的踩过的一些坑排除掉写一份相对比较简单易懂的建站教学，从头到尾甚至不需要你懂代码就可以完成。

希望这个教程能够帮助有需要的人，也希望自己能保持更新博客的好习惯，时刻分析自己所做的以及应该去做的事情，明确目标。

# 最后,<font color=#39c5bb>**Excelsior**!</font>

<a data-fancybox="gallery" href="27.gif">![27](27.gif)</a>

<center><span class="heimu" title="—————你知道的太多了">宫子真可爱嘻嘻</span></center>
