---
title: termux食用指南
date: 2019-08-28 13:32:45
categories: Linux
tags:
- termux
- android
- metasploit
---
# 简介
  termux是安卓上一款可以说是Linux容器吧，下载地址

  <u>[Google play](https://play.google.com/store/apps/details?id=com.termux)

  [官网](https://termux.com/)</u>

  # 一、基本设置及操作

## 基本设置

- 安装好以后，长按屏幕,会有如下显示：

```
  长按屏幕
├── COPY:复制
├── PASTE:更多
├── More:更多
   ├── Select URL: 选择网址
   └── Share transcipt: 分享命令脚本
   └── Reset: 重置
   └── Kill process: 杀掉当前终端会话进程
   └── Style: 风格配色
   └── Help: 帮助文档
```
## 快捷菜单

按<font color="pink">音量+ + Q键</font>调出常用快捷键

- 修改快捷菜单
在<font color="green">/data/data/com.termux/files/home/.termux</font>文件夹添加文件termux.properties,文件内容
```
extra-keys = [['TAB','ESC','CTRL','ALT','|','[',']','HOME','UP','END'],['=','/','-',':','"','(',')','LEFT','DOWN','RIGHT'],['%','!','#','^','@','{','}','<','*','>']]
```

## 常用快捷键

- termux使用<font color="green">音量-</font>模拟<font color="green">Ctrl</font>键，与键盘上的字母组合出快捷键

`Ctrl+A` -> 将光标移动到行首<br>
`Ctrl+C` -> 中止当前进程<br>
`Ctrl+D` -> 注销终端会话<br>
`Ctrl+E` -> 将光标移动到行尾<br>
`Ctrl+K` -> 从光标删除到行尾<br>
`Ctrl+L` -> 清除终端<br>
`Ctrl+Z` -> 挂起（发送SIGTSTP到）当前进程<br>

- 音量加键也可以作为产生特定输入的特殊键.

`音量加+E` -> Esc键<br>
`音量加+T` -> Tab键<br>
`音量加+1` -> F1（和音量增加+ 2→F2等）<br>
`音量加+0` -> F10<br>
`音量加+B` -> Alt + B，使用readline时返回一个单词<br>
`音量加+F` -> Alt + F，使用readline时转发一个单词<br>
`音量加+X` -> Alt+X<br>
`音量加+W` -> 向上箭头键<br>
`音量加+A` -> 向左箭头键<br>
`音量加+S` -> 向下箭头键<br>
`音量加+D` -> 向右箭头键<br>
`音量加+L` -> | （管道字符）<br>
`音量加+H` -> 〜（波浪号字符）<br>
`音量加+U` -> _ (下划线字符)<br>
`音量加+P` -> 上一页<br>
`音量加+N` -> 下一页<br>
`音量加+.` -> Ctrl + \（SIGQUIT）<br>
`音量加+V` -> 显示音量控制<br>
`音量加+Q` -> 显示额外的按键视图<br>

## 基本命令
<font color="green">Termux</font>除了支持<font color="green">apt</font>命令外,还在此基础上封装了<font color="green">pkg</font>命令,<font color="green">pkg</font>命令向下兼容<font color="green">apt</font>命令.<font color="green">apt</font>命令<br>
大家应该都比较熟悉了,这里直接简单的介绍下<font color="green">pkg</font>命令
```
pkg search <query>              搜索包
pkg install <package>           安装包
pkg uninstall <package>         卸载包
pkg reinstall <package>         重新安装包
pkg update                      更新源
pkg upgrade                     升级软件包
pkg list-all                    列出可供安装的所有包
pkg list-installed              列出已经安装的包
pkg shoe <package>              显示某个包的详细信息
pkg files <package>             显示某个包的相关文件夹路径
```
## 管理员身份
- 手机没有root
利用`proot`工具来模拟需要root的环境<br>
```
pkg install proot
```
终端输入：
```
termux-chroot
```
即可模拟`root`环境<br>

- 手机已经root

安装`tsu`，这是一个`su`的termux版本，在termux上代替`su`:
```
pkg install tsu
```
终端输入：<br>

      tsu

## 信息安全
### metasploit安装
```
cd ～
pkg install wget
wget https://Auxilus.github.io/metasploit.sh
bash metasploit.sh
```
### metasploit无法连接数据库<br>
启动数据库后重新进入msfconsole会发现启动没有报错了,db_status查看下数据库连接,也正常了:
```
pg_ctl -D $PREFIX/var/lib/postgresql start
```

- 更多安全工具
[<font color="green"><u>传送门</u></font>](https://www.sqlsec.com/2018/05/termux.html#toc-heading-13)

## Python环境部署
### 安装Python2
```
pkg install Python2
```
### 安装Python3
```
pkg install Python
```
### ipython
```
pkg install clang
pip install ipython
pip3.6 install ipython

```
## 安装Jupyterlab,numpy,scipy,BS4,requests,scrapy等库

### numpy
numpy是Python的扩充，提供数学函数库，机器学习框架的基础库
- 安装依赖包

`apt-get install clang python fftw`

- 安装numpy

`LDFLAGS="-lm - lcompiler_rt" pip install numpy `

### scipy
- 安装wget

`pkg install wget`

- 下载文件

`wget https://its-pointless.github.io/setup-pointless-repo.sh`

- 执行文件

`bash setup-pointless-repo.sh`

- 安装scipy

`pkg install scipy`

### 安装pandas

`LDFLAGS="-lm - lcompiler_rt" pip install pandas `

### 安装matplotlib图形工具
```
apt install libpng freetype pkg-config
LDFLAGS="-lm - lcompiler_rt" pip install matplotlib
```
### 安装jupyterlab
```
apt install libzmq
LDFLAGS="-lm - lcompiler_rt" pip install jupyterlab
```
- 运行

`jupyter-lab`

### 安装BS4,Requests

`pip install BeautifulSoup4 requests`

### 安装scrapy

```
apt-get install libxml2 libxslt
pip install lxml
apt install openssl libffi openssl-tool
pip install scrapy
```

科学相关计算库已全部完成安装
