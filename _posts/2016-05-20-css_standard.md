---
layout: post
title:  "css规范"
categories: css
comments: true
tag: css
---

* content
{:toc}

css 规范





## OOCSS (Object Oriented CSS)
O(Object) 可以抽象成一个独立的片段，

O(Oriented) 对于css Object 是可以重复使用的。

CSS(css)


{% highlight ruby %}
//Media Object
<div class="media">
    <img class="media__object" src="" alt="" />
    <div class="media__body">
        ...
    </div>
</div>

//Flag Object
<div class="flag">
    <div class="flag__item flag__item--image">
        <img src="" alt="" />
    </div>
    <div class="flag__item flag__item--body">
        ...
    </div>
</div>
{% endhighlight %}


更高层次是在项目中思考如何重用样式、模式和抽像模块。一个模块应该有一个主修饰符，不应该太具体或太深入，比如.box-heading要比ul li .box-heading更好。

## BEM (Block, Element, Modifier)
B(block): 独立的页面及逻辑单元，我们通常意义上的component

E(element): 块中的组成部分，不能脱离块单独存在

M(modifier): 修饰符，可修饰块或元素

## SMACCS (Scalable and Modular Architecture for CSS)
S(Scalable) 可以改变的，可扩展的

M(Modular) 可以组合的

A(Architecture) 风格

## METACSS | ATOMCSS (原子CSS)

{% highlight ruby %}
<button class="button button-error float-right mr10"></button>
{% endhighlight %}

## css的最佳实践应该是： Sass + OOCSS/BEM/METACSS

{% highlight ruby %}
$primary-bgc: white;
$success-bgc: green;
$error-bgc: red;

%button {
    width:80px;
    height:40px;
}
%button-primary {
    @extend %button;
    background-color: $primary-bgc;
}
%button-success {
    @extend %button;
    background-color: $success-bgc;
}
%button-error {
    @extend %button;
    background-color: $error-bgc;
}
{% endhighlight %}


{% highlight ruby %}
<button class="button-primary">提交</button>
<a href＝"#" role="submit-button">提交</a>
{% endhighlight %}


{% highlight ruby %}
.button-primary{
    @extend %button-primary;
}
a[role="submit-button"] {
    @extend %button-success;
}
{% endhighlight %}

# css书写顺序
1.位置属性(position, top, right, z-index, display, float等)

2.大小(width, height, padding, margin)

3.文字系列(font, line-height, letter-spacing, color- text-align等)

4.背景(background, border等)

5.其他(animation, transition等)


# 什么鬼，又不知道怎么命名class了
相信写css的人都会遇到下面的问题：
- 糟糕，怎么命名这个class，好像不太贴切，要是冲突了怎么办，要不要设计成通用一点...
- 而改别人css代码的时候则会一直有个疑问：这个class到底是只在这个地方用了，还是其他地方都用了？

于是就有了下面的做法：
- 最后终于被逼出了个class，简洁也好，中英混搭也罢，看着一头雾水也没关系，反正最后页面显示出来的。
- 这个class应该是只有这个地方用到，我可以放心写。上线之后。如果没问题，则暗自自我欣赏，看吧问题就这么简单，分分钟搞定呀；如果冲突了，则无限感慨，哎，改的时候我就隐隐不安啊，妈蛋，深坑，这是谁写的，谁写的！！！
- 不好，这个class说不定其他地方也用到了，我得加个限制范围，加个父元素？要不重新再命名个class吧，比较保险。最后如果没问题则表示还好比较机智，怎么说哥也是混过的，还是有几斤几两的；如果有问题则表示防不慎防啊，这也太太太坑了吧。

由此可见，class的命名真不是一件简单的事，尤其还要兼顾可辨别性与可读性。

## class命名到底有多难

第一，class跟id不一样，class本来就是设计用来可以重复利用的，而id才是设计唯一的（如果遵循BEM，class几乎也都是唯一的了）。

第二，样式是可以覆盖的，而且先按照权重，再按照定义的先后顺序。也许你花了十分钟设计定义的一个class样式，人家分分钟就给你干掉了，这得多恼火；也许这个页面好好的，跑到另一个页面就跟原先的样式有了冲突。

所以class命名的难就难在既要重复利用，又要避免样式的冲突。如果要重复利用，那么当然是越简单越好，越抽象可用的地方越大，太具体了就完蛋了。而如果要避免样式冲突。BEM的方式最简单，class都唯一了，那还冲突个毛线；其次就是通过父元素限定作用域，可以搞几个层级，而不是单独一个class定义样式；还有就是追加class，来实现差异化；最后不同的页面不同的文件，你用你的我用我的。

## 常见class关键词：

- 布局类：header, footer, container, main, content, aside, page, section
- 包裹类：wrap, inner
- 区块类：region, block, box
- 结构类：hd, bd, ft, top, bottom, left, right, middle, col, row, grid, span
- 列表类：list, item, field
- 主次类：primary, secondary, sub, minor
- 大小类：s, m, l, xl, large, small
- 状态类：active, current, checked, hover, fail, success, warn, error, on, off
- 导航类：nav, prev, next, breadcrumb, forward, back, indicator, paging, first, last
- 交互类：tips, alert, modal, pop, panel, tabs, accordion, slide, scroll, overlay,
- 星级类：rate, star
- 分割类：group, seperate, divider
- 等分类：full, half, third, quarter
- 表格类：table, tr, td, cell, row
- 图片类：img, thumbnail, original, album, gallery
- 语言类：cn, en
- 论坛类：forum, bbs, topic, post
- 方向类：up, down, left, right
- 其他语义类：btn, close, ok, cancel, switch; link, title, info, intro, more, icon; form, label, search, contact, phone, date, email, user; view, loading...

有了关键词之后，我们先来制定一些简单的规则
## 制定简单规则：
1. 以中划线连接，如`.item-img`
2. 使用两个中划线表示特殊化，如`.item-img.item-img--small`表示在`.item-img`的基础上特殊化
3. 状态类直接使用单词，参考上面的关键词，如`.active, .checked`
4. 图标以icon-为前缀（字体图标采用`.icon-font.i-name`方式命名）.
5. 模块采用关键词命名，如`.slide, .modal, .tips, .tabs`，特殊化采用上面两个中划线表示，如`.imgslide--full, .modal--pay, .tips--up, .tabs--simple`
6. js操作的类统一加上`js-`前缀
7. 不要超过四个class组合使用，如`.a.b.c.d`

关键词及规则都有了，现在可以进入本文的核心的核心，实战操作。

## 实战操作
以布局入手，大概结构如下：

{% highlight ruby %}
header.header>.inner-center
section.section-feature>.inner-center // if
section.section-main>.inner-center
section.section-postscript>.inner-center // if
footer.footer>.inner-center
{% endhighlight %}
这里我们可以看出都是些简单的关键词，比较好理解，一看就知道是什么。
现在问题来了，如果其他地方也要用到这些关键词怎么办？

## 修饰关键词
以`header`为例，我们可以添加前缀表示不同的`header`，如区块头部`.block-hd`(hd为header简写)，modal头部`.modal-hd`，文章头部`.article-hd`。
同样标题也可以分为，页面标题`.page-tt`(title的简写)，区块标题`.block-tt`等。
同样，这给我们提出了第二个问题，如果要特殊化某个class该怎么办？

## 特殊化class
以上面的tt为例，大概有三种办法：
第一种犯法：直接修改class，将`.page-tt`修改成`.page-user-tt`(可以采用scss的%先定义共用的代码)。
第二种办法： 追加class特殊化，根据我们上面定义的规则，在`.page-tt`上追加一个class成`为.page-tt.page-tt--use`r，注意`.page-tt--user`不是一个独立的class，它使基于`.page-tt`这个基础上的。
第三种办法： 使用父类，给一个范围，于是形成.page-user .page-tt。
一般我们使用的是第二种和第三种办法，因为这两种都有共同的.page-tt，可以比较方便控制一些基础共有的样式。
由第三个通过父类控制的办法，我们进入第三个要讨论的问题，层级结构

## 层级
最适合层级的例子莫过于ul>li结构了，如下面的结构：

{% highlight ruby %}
<ul>
    <li>
        <a href="#"><img src="" alt=""></a>
        <h3><a href="#"></a></h3>
        <p></p>
    </li>
</ul>
{% endhighlight %}
一般来说我们也有两种办法定义层级，第一种为继承式，第二种为关键词式。

{% highlight ruby %}
// 继承式
ul.card-list
    li.list-item
        a.item-img-link>img.item-img
        h3.item-tt>a.item-tt-link
        p.item-text

// 关键词式
ul.card-list
    li.item
        a.field-img-link>img.field-img
        h3.field-tt>a.field-tt-link
        p.field-text
{% endhighlight %}

由上可以看出继承式一般子元素接着父元素的最后一个单词如li接着ul的`list`，而li的子元素接着li的`item`；至于关键词式则完全由关键词来表示层级，`list>item>filed`正好构成三层等级。

最后由我们的层级进入我们最后一个问题，如何控制样式的范围

## 样式范围
这里以腾讯课堂的课程详细页右边栏为例，如下图：

![image description](http://7tszky.com1.z0.glb.clouddn.com/Fmp64onpSWViDDmCI6J6Yx3-4Wax)

三个区块的基础框架为：

{% highlight ruby %}
.aside-block.block--xxx>
    h3.block-tt
    .block-bd
{% endhighlight %}
其中`.aside-block.block--xxx`用到了我们的特殊化class，而`.block-tt,block-bd`则使用了我们的修饰关键词，至于`.aside-block`与它的子元素之间则使用了我们上面说的继承式层级。现在根据这个层级结构我们定义基础样式如下：

{% highlight ruby %}
.aside-block{
    .block-tt{}
    .block-bd{}
}
{% endhighlight %}
假设这里的联系机构区块的标题不一样，我们则可以：

{% highlight ruby %}
.block--contact{
    .block-tt{}
}
{% endhighlight %}
当然如果本身有5个区块，2个标题一样，另外三个标题又一样，也许我们就有需要给.block-tt追加一个特殊化class，或者给aside-block特殊化一个class，如：

{% highlight ruby %}
.aside-block{
    .block-tt{
        &.block-tt--special{}
    }
    .block-bd{}
}
// 或
.aside-block{
    &..aside-block--special{
      .block-tt{}
  }
}
{% endhighlight %}
基础框架讨论完毕之后，就轮到我们的内容了，以联系机构为例：
使用`ul>li`结构，所以样式是另外一个独立的范围，不嵌套在之前的`.aside-block`里面，html及css代码如下：


{% highlight ruby %}
ul.contact-list
    li
        i.item-icon.icon-font.i-xxx
        a.item-tt
        p.gray
{% endhighlight %}
这里我们li没有设置class，而p使用了一个全局的class.gray

{% highlight ruby %}
.gray{}
.contact-list{
    li{}
    .item-icon{}
    .item-tt
}
{% endhighlight %}

同理如果我们有其他地方应用这个可以拷贝过去，而如果需要一点调整，我们可以使用父元素来控制，如这里我们可以使用.block--contact来进一步调整contact的样式，如：


{% highlight ruby %}
.block--contact{
    .contact-list{
        li{}
    }
}
{% endhighlight %}
至此，我们的class命名方法讨论完毕，说到底就是先记住一些必备的基础关键词，然后合理应用上刚才提出的修饰关键词，特殊化class，层级及最后的样式范围就可以了。

本文转载于[IMWeb](http://imweb.io/topic/5623c25734764b2c16769749)。
























