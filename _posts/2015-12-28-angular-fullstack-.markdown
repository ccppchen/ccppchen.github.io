---
layout: post
title:  "使用yeoman生成MEAN全栈项目"
categories: mean
comments: true
tag: mean node angular mongdob express
---

* content
{:toc}

使用yeoman生成MEAN全栈项目




首先要在全局安装nodejs、git、yeoman、bower、grunt、mongodb

nodejs可以去Nodejs[官网下载](https://nodejs.org/en/)下载对应版本

git可以去Git[官网下载](http://git-scm.com/download/)下载对应版本

mongodb可以去mongodb[官网下载](http://www.mongodb.org/downloads)下载对应版本

[mongodb数据库安装教程](http://jingyan.baidu.com/article/3c343ff7140c890d37796395.html)

一、安装yeoman、bower、grunt命令到全局只需执行

{% highlight ruby %}
npm install -g yo grunt-cli bower
{% endhighlight %}

以上安装完之后验证

{% highlight ruby linenos %}
node --version
git --version
yo --version
grunt --version
bower --version
{% endhighlight %}

![验证版本]({{site.baseurl}}/images/屏幕快照 2015-12-28 10.56.06.jpg)

控制台中能打印出版本好则证明安装成功。

二、安装generator生成器

在命令行中输入
{% highlight ruby %}
npm install -g generator-angular-fullstack
{% endhighlight %}

三、在本地创建项目

首先创建一个项目文件夹，命令行指到这个文件夹，再执行yo angular-fullstack mean_demo，命令会自动运行bower install 和 npm install，根据bower.json和package.json中的配置去下载对应的包，等结束后根目录下会多一个node_modules文件夹，client目录下会多一个bower_components文件夹。

{% highlight ruby linenos %}
mkdir mean_demo && cd mean_demo
yo angular-fullstack mean_demo
{% endhighlight %}

![验证版本]({{site.baseurl}}/images/屏幕快照 2015-12-28 11.08.46.jpg)

四、运行

{% highlight ruby %}
grunt serve
{% endhighlight %}

自动会打开浏览器，你就可以在浏览器看到页面

我的MEAN项目github地址[MEAN-ionic](https://github.com/ccppchen/MEAN-ionic)

![MEAN-ionic]({{site.baseurl}}/images/屏幕快照 2015-12-28 13.12.39.jpg)
