---
layout: post
title:  "在终端下跳转字符"
date:   2016-11-03 00:00:00 +0800
categories: shell
---

在 shell 中工作的时候，一定会需要在一长串的命令中修改某个单词或参数，这个时候就需要有一个快捷的方法能跳到指定的地点，但终端又不是 vim 里面，我们也不想方向键按到底（有点像踩油门到底？）

在 linux 的 shell 中，我们可以通过 alt + F 跳到上一个单词开始处，通过 alt + B 跳到下一个单词开始处。

但是在 mac 下，终端的 alt + F/B 行为已经变成了输出一个 unicode 字符，怎么把这个 linux 下亲切的动作复制到 mac 下呢

在 mac zsh 下，可以增加以下配置到 ~/.zshrc
```
bindkey "\e\e[D" backward-word
bindkey "\e\e[C" forward-word
```
就可以用 alt + 左方向键、alt + 右方向键 跳转了。