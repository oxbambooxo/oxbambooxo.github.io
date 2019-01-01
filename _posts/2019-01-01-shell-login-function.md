---
layout: post
title:  "ssh 自动输入密码的 shell 函数"
date:   2019-01-01 11:04:00 +0800
categories: shell
---

使用 expect 命令等待 ssh 的输出后进行相关操作，定义为函数只是方便与用户配置文件写在同一个文件中(shell脚本而不是expect脚本)

```
function login_server() {
    expect -c "
        set timeout 10;
        spawn ssh $1;
        expect {
        \"password:\" {
            send \"$2\r\";
            interact;
        }
        \"yes/no\" {
            send \"yes\r\";
            exp_continue;
        }
    }"
}
```

该 shell 函数可在用户配置脚本中使用，也可单独输入地址和密码使用

```
function server1() { login_server user@192.168.1.122 Passwd122}
function server2() { login_server user@192.168.1.123 Passwd123}
```
