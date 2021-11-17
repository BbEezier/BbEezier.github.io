---
title: 关于Gal主题的一些使用心得
author: yLTT
avatar: 'http://q1.qlogo.cn/g?b=qq&nk=309002093&s=640'
authorLink: 'https://www.liangzt.top'
authorAbout: 与君共勉!
authorDesc: 与君共勉!
categories: 技术
comments: true
tags:
  - web
  - 博客相关
keywords: gal主题
photos: 'https://api.amogu.cn/api/acg?=1'
abbrlink: 9596
date: 2021-07-29 12:47:54
---

{% aplayer "メビウス!" "佐橋俊彦" "http://music.163.com/song/media/outer/url?id=408772686.mp3" "https://p1.music.126.net/eLR9mBbd2W55p3Utz6oinQ==/1401877329221968.jpg?" %}

~~PS：开始前不来点音乐吗XD~~

### 针对Hexo Theme <font color=#39C5BB>[Gal](https://github.com/ZEROKISEKI/hexo-theme-gal)</font> 在git以下内容时报错的解决方案 




<pre><code class="language-java"> npm install hexo-renderer-sass --save 
 npm install hexo-renderer-scss --save</code></pre>




#### **1.下载Yarn**

[2 - 安装 | Yarn - JavaScript 软件包管理器 | Yarn 中文文档 - Yarn 中文网 (yarnpkg.cn)](https://www.yarnpkg.cn/getting-started/install)

按照文档描述下载安装好后可以重新安装

<pre><code class="language-java">yarn add hexo-renderer-sass
yarn add hexo-renderer-scss</code></pre>



#### **2.改用淘宝镜像 cnpm下载**

<pre><code class="language-java">npm install -g cnpm --registry=https://registry.npm.taobao.org 
npm config set registry https://registry.npm.taobao.org
cnpm install hexo-renderer-sass --save</code></pre>

###### 如果在git拉取时报错`OpenSSL SSL_read: Connection was reset, errno 10054` 

将ssl验证关闭即可，然后重新拉取

<pre><code class="language-java">git config --global http.sslVerify "false</code></pre>

## Gal 主题色更改方式

在你的Hexo博客根目录下\themes\gal\source\css中找到<font color=red>_variables.scss</font>文件

![1](1.png)

颜色对应关系的话其实直接对比页面与scss文件里面<font color =red>R</font><font color=green>G</font><font color =blue>B</font>代码就能看出来，建议开着F12对照。



## 代码高亮设置

Gal主题里面引用了[highlight.js](https://github.com/highlightjs/highlight.js)

最简单的应用方式就好像我上面的示例

直接按如下格式输入即可

<B><font size = 4 face="思源黑体" color =#33CCCC><xmp><pre><code class="language-代码的语言">代码内容</code></xmp></pre></font></B>

如下

```python
import random
yLTT = "BEzier"
print(yLTT)
random_num = random.randint(1,1000)
for i in range(3):
 num = int(input('请输入你猜的数字：'))
   if num>random_num:
      print('你猜的太大了')
   elif num<random_num:
      print('太小了')
   else:
      print('恭喜你猜对了，答案是：',random_num)
      break
```



我个人觉得Md文件编辑用 [Typora](https://www.typora.io/) 会方便一点，代码块高亮可以直接导入不用按格式输入



## 加载图片避坑

这里可以直接照着这位大佬的方法走就可以了:

[HEXO插入图片（详细版） - 简书 (jianshu.com)](https://www.jianshu.com/p/f72aaad7b852)

一般的，按照上面的流程走完后可以直接通过 

<pre><code class="language-java">![图片名](图片.jpg)</code></pre>

在<font color=red>**文章**</font>中进行一个图片的展示

这里的文章就是指你_post文件夹下的文件，也就是你在git中通过

<pre><code class="language-java">hexo new xxx</code></pre>

新建的文件，但如果你拿这个方法在<font color =blue>**页面**</font>中使用，就没效果了

<pre><code class="language-java">hexo new page xxx      新建页面</code></pre>

如果你想要在页面（比如“关于我”  about页面）中添加图片，直接使用Html的语法就可以了~(~~当然文章也可以使用这个方法~~)

<pre><code class="language-java">&ltimg src="/image/xxx.png" /&gt</code></pre>

这里我是直接在我的Hexo根目录的\source文件夹下面新建了一个**image**文件夹,然后把需要展示的图片放进去，调用起来也很方便。

![3](3.png)

## 自己的碎碎念

开博客是为了更好的记录自己学习的历程，目前网站是直接托管给**Github page**服务的，或许未来有钱了架设一个服务器也是不错的选择~(º﹃º ) 

<conter>![2](2.png)</conter>

话说原来暑假已经过去一个月了吗？？？！







