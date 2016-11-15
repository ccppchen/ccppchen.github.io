---
layout: post
title:  "React Native总结"
categories: react
comments: true
tag: React-Native
---

* content
{:toc}

React-Native总结






<ol style="list-style:decimal;">
<li><p>react 宽度基于<code>pt</code>为单位， 可以通过<code>Dimensions</code> 来获取宽高，<code>PixelRatio</code> 获取密度。</p></li>
<li>
<p>基于flex的布局</p>
<ol>
<li><p>view默认宽度为100%</p></li>
<li><p>水平居中用<code>alignItems</code>, 垂直居中用<code>justifyContent</code></p></li>
<li><p>基于flex能够实现现有的网格系统需求，且网格能够各种嵌套无bug</p></li>
</ol>
</li>
<li>
<p>图片布局</p>
<ol>
<li><p>通过<code>Image.resizeMode</code>来适配图片布局，包括<code>contain</code>, <code>cover</code>, <code>stretch</code></p></li>
<li><p>默认不设置模式等于cover模式</p></li>
<li><p>contain模式自适应宽高，给出高度值即可</p></li>
<li><p>cover铺满容器，但是会做截取</p></li>
<li><p>stretch铺满容器，拉伸</p></li>
</ol>
</li>
<li>
<p>定位</p>
<ol>
<li><p>定位相对于父元素，父元素不用设置position也行</p></li>
<li><p>padding 设置在Text元素上的时候会存在bug。所有padding变成了marginBottom</p></li>
</ol>
</li>
<li>
<p>文本元素</p>
<ol>
<li><p>文字必须放在Text元素里边</p></li>
<li><p>Text元素可以相互嵌套，且存在样式继承关系</p></li>
<li><p><code>numberOfLines</code> 需要放在最外层的Text元素上，且虽然截取了文字但是还是会占用空间</p></li>
</ol>
</li>
</ol>

React-Native 打包，分两种，在线打包，离线打包；

在线打包，原声app指向npm服务器端的js文件，可以在线访问，把js文件部署在服务端，这样的有点可以随时改变服务端文件，便于发布；但是依赖网络，没有网络立即报错。
离线打包：离线访问，没有网络的时候程序不会报错；缺点，每次有更新必须从新发布app

下面给大家分享一下离线打包app的方法，ios版本。
```
react-native bundle --entry-file index.ios.js --platform ios --bundle-output ios/main.bundle  

```
截图如下：

![image](http://img.blog.csdn.net/20160606174624769?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

然后需要在代码中配置一下，将bundle文件拷贝到ios项目目录下，指向生成的main.bundle文件

代码如下：

![image](http://img.blog.csdn.net/20160606174632172?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

成功了。

