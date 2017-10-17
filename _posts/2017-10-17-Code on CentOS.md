---
title: Code on CentOS
layout: post
description: I have a CentOS, I have a Python, emmmmmmm...
---

## Install Python3

If you do not have root access and you want to install python3 on your CentOS server, follow below steps.

### Download Python3 

Get the python installation package from https://www.python.org/ftp/python/

```shell
wget https://www.python.org/ftp/python/3.6.2/Python-3.6.2.tar.xz
```

### Unzip

```shell
xz -d Python-3.6.2.tar.xz
tar -xvf Python-3.6.2.tar
```

### Enter the Python Directory

```shell
cd Python-3.6.2/
```

### Configure

Install at current user's root directory, the direcotry may be like /users/Chriskuei on CentOS

```shell
./configure --prefix=/users/Chriskuei
```

### Make and Make Install

```shell
make
make install
```

### Check

```
python3 --version
```



## nohup

### About nohup(no hangup)

when using the command shell, prefixing a command with **nohup** prevents the command from being aborted if you log out or exit the shell.

### nohup syntax

```shell
nohup COMMAND [ARG]...
nohup OPTION...
```

### Examples

```shell
nohup python3 train.py &
nohup python3 train.py >result.txt & 
```



## Commands

```shell
wc -l filename
head -n filename
tail -n filename
vimdiff file1 file2
scp source username@server:target
scp -r sourcefolder username@server:target
```

