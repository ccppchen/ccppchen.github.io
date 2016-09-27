---
layout: post
title:  "Git提交到多个远程仓库"
categories: git
comments: true
tag: git
---

* content
{:toc}

使用Git提交到多个远程仓库





###有两种做法,先看第一种

#1、通过命令行进行操作

例如我有下面两个仓库:

[https://github.com/ccppchen/MEAN-ionic.git](https://github.com/ccppchen/MEAN-ionic.git)

[https://git.coding.net/cpchenp/mean-ionic.git](https://git.coding.net/cpchenp/mean-ionic.git)

在项目路径下打开命令行

添加一个remote,这里是all,也可以是别的名字

{% highlight ruby %}
输入:git remote add all https://github.com/ccppchen/MEAN-ionic.git

再添加另一个:git remote set-url --add all https://git.coding.net/cpchenp/mean-ionic.git

{% endhighlight %}
如果有多个,按照上面这一个命令进行添加.

提交的时候输入:`git push -u all master`

在操作完上面的添加命令后，如果我们打开.git/config文件,我们可以看到这样的配置:

{% highlight ruby %}
[remote "all"]
  url = https://github.com/ccppchen/MEAN-ionic.git
  fetch = +refs/heads/*:refs/remotes/all/*
  url = https://git.coding.net/cpchenp/mean-ionic.git
{% endhighlight %}

#2、直接配置.git/config文件:

打开.git/config文件,添加这样的配置:

{% highlight ruby %}
[remote "all"]
  url = https://github.com/ccppchen/MEAN-ionic.git
  url = https://git.coding.net/cpchenp/mean-ionic.git
{% endhighlight %}

有多少个远程库,就配置多少个url即可.

####从这里可以看出,第一种方法生成的配置中还有一个fetch配置,这个配置可以完全去掉.


