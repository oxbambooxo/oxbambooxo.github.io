---
layout: post
title:  "Supervisor 的 minfds 参数"
date:   2016-08-23 00:00:00 +0800
categories: supervisor
---

Supervisor的配置文件中有一个 minfds 之前没有注意到，直到系统上由 Supervisor托管的程序出现问题。

使用 `cat /proc/<pid>/limits` 查看进程 ulimit 参数时，得到的限制总是 1024 4096 ，与当时系统配置的默认值不一样，不管是重启进程还是重启 supervisord。

而且值得说明(吐槽)的是，注释 /etc/supervisord.conf 中的 `minfds`、`minproc`参数后，supervisord 使用的将会是其默认设置的值 1024 4096……

也就是说还得把系统 /etc/security/limit.conf 中配置的值再写一遍到 supervisord 配置中。