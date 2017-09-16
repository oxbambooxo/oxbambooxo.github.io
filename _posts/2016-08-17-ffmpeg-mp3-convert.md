---
layout: post
title:  "ffmpeg mp3 convert to amr"
date:   2016-08-23 00:00:00 +0800
categories: ffmpeg
---

`ffmpeg -i audio.mp3 -ab 7.4k -ar 8k -ac 1 audio.amr`

在mac os下，用brew install ffmpeg安装的 ffmpeg 没有 amr 模块，需要下载 ffmpeg 的source code 进行定制的编译。

例如下载的ffmpeg 为 3.1.2 版本，将其安装至：

> /usr/local/Cellar/ffmpeg/3.1.2

再使用 `brew switch ffmpeg 3.1.2` 将系统上的 ffmpeg 链接至3.1.2