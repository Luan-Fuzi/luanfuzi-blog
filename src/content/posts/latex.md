---
title: "Latex学习记录"
published: 2024-03-31T20:49:17+08:00
description: "记录一下Latex学习过程，从安装到入土。"
category: legacy
tags: ["Latex", "论文"]
---

记录一下Latex学习过程，从安装到入土。

安装Tex Live，找编辑器，学语法一条龙。

LaTex是一种排版技术，通过特定的指令可以控制文档内容（如图片、文本等）的位置、大小和样式。

以下是基础使用流程。

*操作系统：Windows 10 22H2*

*CPU: Intel i7-11800H*

## 安装Tex Live

使用LaTeX进行写作的第一步是安装LaTex的编译环境。为新手考虑，在硬盘空间充足的硬盘内优先考虑安装功能较全的Tex Live.

![Texlive](/imgs/posts/latex/texlive.png)

简陋的官网

国内比较方便的下载途径——清华镜像站：
Index of /CTAN/systems/texlive/Images/ | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror
*

![清华镜像站](/imgs/posts/latex/texlive_tuna.png)

清华镜像站

下载镜像后，打开镜像内部index.html，可以查看官方提供的简易安装教程；也可以观看类似教程视频
TeX Live 2023安装
*

Tex Live是一个集成功能较多，镜像体积较大的All In One，安装较为耗时（i7-11800H安装全程45分钟左右，仅作参考），嫌时间长的可以选择按装更简单、更小的MiKTeX：
Getting MiKTeX
*

安装完记得在Path路径下添加环境变量。

## 编辑器

安装完成后，Tex Live会自带一个编辑器（或者叫IDE？）TexWorks，可以方便地将Latex文档编译成PDF。

因为LaTeX到PDF是一种编译过程，所以编辑器并不局限于TexWorks或某种编辑器。可选的编辑器/编译环境还有TexStudio|VS Code|Sublime Text等。

作为一个万年VS Code用户，我抛弃了便捷好用的TexWorks，安装了更人性化、更强大的Tex Studio也没久用，最终选择了VS Code + LaTeX插件。需要注意的是，VS Code安装插件后虽然能用，但并不是最舒服的一个使用环境，需要进入Settings打开JSON文件进行某些配置。我本人也对研究配置环境兴趣不大，所以这里贴一个我用的配置文件：
Visual Studio Code (vscode)配置LaTeX - 知乎 (zhihu.com)
*

## 开写！

LaTeX作为一种[能且仅能在写文章时用上]的工具，不必像编程语言那样从零开始啃语法，更不需要搞懂LaTeX的模板是怎么做的。作为初阶使用者，把别人写好的拿过来用是最方便的方式，每个期刊或者会议都会有模板，想投那个刊就从哪家网站上下载模板。模板在满足期刊板式要求的同时，一般也会附带有较为详细的LaTeX语法教程，在模板的上基础上把自己的内容敲进去即可。随用随学，效率至上。

值得注意的是，LaTeX对数学公式的支持完备而复杂，可以找几个在线LaTeX公式编辑器写几个公式，再把LaTeX表达式粘贴回来。这里给出几个网站以供参考。

在线LaTeX公式编辑器-编辑器 (latexlive.com)
*

LatexEasy | 在线Latex数学公式编辑和渲染
*

## 碰到的问题

### 安装过于耗时

我其实不是现在（2024年3月）才真想用一下LaTeX的。我在前两年有过一两次课程作业要提交报告，报告中含有数学公式，我想来想去用markdown和word都写不上去，于是找到一个叫LaTeX的工具，第一次或者前几次安装都因为没有耐心而把进程关掉了。后来发现markdown支持LaTeX公式，于是直接学了语法，放弃了安装。

如果安装时感到烦躁，站起身，喝口水，下楼转一圈。安装时间长是正常的。（一定要多喝水

### VS Code编译问题

VS Code使用LaTeX插件的问题不止在于一开始没有配置文件，我前几次编译出来的PDF文件连格式都不对，编辑器里几十个报错。

后来得知默认选择的编译器不对。在插件设置里默认选择的是XeLaTeX，换成PDFLaTeX就可以解决我的问题了。

![编译选项](/imgs/posts/latex/compiler.png)

侧边栏选择编译选项
