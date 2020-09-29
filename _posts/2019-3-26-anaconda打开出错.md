---
layout: post
title:  anaconda打开出错解决方案
date:   2019-3-26 12:54:00 +0800
categories: Solutions
tag: Python
---

* content
{:toc}


卸载anaconda之后重新安装，再次打开anaconda-navigator会报错
```
could not determine a constructor for the tag 'tag:yaml.org,2002:python/unicode'
  in "C:\Users\Wayne\AppData\Local\ContinuumIO\binstar\config.yaml", line 1, column 1
```
查找了网上方法非常凌乱，故整理如下：

1. 管理员运行conda prompt
2. conda update anaconda-navigator]
3. anaconda-navigator --reset
4. conda update anaconda-client
5. conda update -f anaconda-client
需要说明的是，我在1之后2之前还执行了
```
conda update conda
```
在2之后3之前执行了
```
conda update navigator-updater
```
更新了包但是我觉得可能没什么影响。

另外，由于anaconda原生是连接到国外网站更新，所以最好更改成国内镜像，比如清华的，
1. conda prompt中执行
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```
2. 此时，目录 C:\Users<你的用户名> 下就会生成配置文件.condarc
3. 修改上述配置文件，删除上述配置文件 .condarc 中的第三行（即 -defaults），然后保存
4. (option)查看是否生效，通过命令 conda info 查看当前配置信息，关注 channel URLs 字段内容，改成清华镜像的地址了就成功了