---
layout: post
title:  "查询占用某端口的进程"
date:   2018-10-14 13:54:00 +0800
categories: shell
---

以 80 端口为例, 使用 netstat -e 查询出使用某连接的 inode 号

```
netstat -ntp -e |grep 80
```

```
tcp        0      0 127.0.0.1:59365             127.0.0.1:80                TIME_WAIT   0          0          -
tcp        0      0 127.0.0.1:23001             127.0.0.1:8061              TIME_WAIT   0          0          -
tcp        0      0 127.0.0.1:23001             127.0.0.1:8030              TIME_WAIT   0          0          -
tcp        0      0 127.0.0.1:80                127.0.0.1:1380              ESTABLISHED 99         2020337777 15682/nginx
tcp        0      0 127.0.0.1:80                127.0.0.1:16897             ESTABLISHED 99         2020406244 15681/nginx
```

得到具有 inode 号的相关连接, 使用该 inode 号进行下一步的查询

```
find /proc -lname '*2020406244*' 2>/dev/null
```

```
/proc/15668/task/15668/fd/63
/proc/15668/fd/63
```

即可找到相关 socket 连接被使用的进程
