---
layout: post
title:  "Linux的后台运行和关闭、查看后台任务命令"
categories: 命令行
comments: true
tag: mac
---

* content
{:toc}

Linux的后台运行和关闭、查看后台任务命令






fg、bg、jobs、&、nohup、ctrl+z、ctrl+c、kill、ps 命令

一、&

加在一个命令最后，可以把这个命令放到后台执行，如

{% highlight ruby %}
jekyll s &
{% endhighlight %}#在后台运行jekyll s

二、ctrl + z

可以将一个正在前台执行的命令放到后台，并且处于暂停状态。

三、jobs

查看当前终端上有多少在后台运行的命令

{% highlight ruby %}
jobs -l
{% endhighlight %}#查看所有后台命令的PID,jobs的状态可以是running, stopped, Terminated。

四、fg

将后台中的命令调至前台继续运行。如果后台中有多个命令，可以用fg %jobnumber（是命令编号，不是进程号）将选中的命令调出。

五、bg

将一个在后台暂停的命令，变成在后台继续执行。如果后台中有多个命令，可以用bg %jobnumber将选中的命令调出。

六、kill

{% highlight ruby %}
kill 1423
{% endhighlight %}

法子1：通过jobs命令查看job号（假设为num），然后执行kill %num

法子2：通过ps命令查看job的进程号（PID，假设为pid），然后执行kill pid

前台进程的终止：Ctrl+c

七、nohup

{% highlight ruby%}
nohup jekyll s &
{% endhighlight %}

如果让程序始终在后台执行，即使关闭当前的终端也执行（之前的&做不到），这时候需要nohup。该命令可以在你退出帐户/关闭终端之后继续运行相应的进程。关闭中断后，在另一个终端jobs已经无法看到后台跑得程序了，此时利用ps（进程查看命令）

八、ps

{% highlight ruby %}
ps -aux
{% endhighlight %}

a:显示所有程序 u:以用户为主的格式来显示 x:显示所有程序，不以终端机来区分

九、ctrl + c

进程的终止

