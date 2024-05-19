---
title: Vim学习笔记
date: 2024-05-19 16:06:21
category: Vim
---

进入vim不用说了

vim分4个模式，normal、insert、cmd、visual

## 移动光标

←h ↓j ↑k →l

> j和k可以想象成扑克牌的jack和king，King的等级肯定比jack高，所以king是向上

## 进入insert模式

**i**nsert光标往左边，按**a**ppend光标往右边，如果按住shift就往最前面或最后面插入（类似home和end按键）

> insert可以想象成插队是往前面插的

**o**pen a new line新增一行编辑，如果按住shift就往上面新增一行

**c**hange **w**ord删除当前单词，然后编辑，**c**hange **i**n+**单个括号**删除括号内然后编辑

## 进入visual模式

ctrl+**v**isual可视化块

shift+**v**isual可视化行

## 导航

```
# 显示行号
set number
# 显示相对行号
set relativenumber
```

shift+**g**oal到最后一行，按**g**ood **g**ame到第一行

> 写代码的目标是坚持写到最后一行，所以shift goal是最后一行。gg表示游戏结束了，可以再来一把，所以到第一行

**数字**+**hjkl**可以光标往上下左右移动多个字符或者行

**w**ord移动到下一个单词开头

**e**nd下个单词结尾

**b**ack上个单词开头

**/**搜索

**:%s/old/new/g**lobal全局替换

## 编辑

**y**ank **y**ank复制当前行，**y**ank **w**ord复制单词，**p**aste粘贴，**数字**+**p**aste粘贴多次

**d**elete **d**elete删除当前行，**d**elete **w**ord删除单词，**d**elete删除visual中的内容

## 重复

** . **句号重复上一次操作

**u**ndo撤销，ctrl+**r**edo重做
