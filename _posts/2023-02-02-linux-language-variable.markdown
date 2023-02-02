---
layout: post
title:  "Linux LC_ALL、LC_* 和 LANG"
date:   2023-02-02 15:11:55 +0800
tags:   Linux
---
它们之间有一个优先级的关系： LC_ALL>LC_*>LANG 。

可以这么说，LC_ALL是最上级设定或者强制设定，而LANG是默认设定值。

- 设定了LC_ALL＝zh_CN.UTF-8，不管LC_*和LANG设定成什么值，它们都会被强制服从LC_ALL的设定，成为 zh_CN.UTF-8。

- 设定了LANG＝zh_CN.UTF-8，而其他的LC_=en_US.UTF-8，并且没有设定LC_ALL，那么系统的locale 设定以LC_=en_US.UTF-8。

- 设定了LANG＝zh_CN.UTF-8，而其他的LC_*，和LC_ALL均未设定，系统会将LC_*设定成默认值，也就是LANG的值 zh_CN.UTF-8 。

- 设定了LANG＝zh_CN.UTF-8，而其他的LC_CTYPE=en_US.UTF-8，其他的LC_*，和LC_ALL均未设定，那么系统的locale设定将是： LC_CTYPE=en_US.UTF-8，其余的 LC_COLLATE，LC_MESSAGES等等均会采用默认值，也就是LANG的值，也就是LC_COLLATE＝LC_MESSAGES＝……＝ LC_PAPER＝LANG＝zh_CN.UTF-8。