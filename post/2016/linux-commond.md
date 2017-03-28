```toml
title = "Linux 常用命令"
slug = "Linux 常用命令"
desc = "Linux 常用命令"
date = "2016-12-02 11:17:16"
update_date = "2017-03-22 22:04:16"
author = "tcc"
thumb = ""
draft = false
tags = ["Linux"]
```

### 操作系统命令
    uname -a #查看内核/操作系统/CPU信息
    head -n 1 /etc/issue #查看操作系统版本
    cat /proc/cpuinfo #查看CPU信息
    hostname #查看计算机名
    lspci -tv #列出所有PCI设备
    lsusb -tv #列出所有USB设备
    lsmod #列出加载的内核模块
    env #查看环境变量

------------

### 文件/IO资源命令
    free -m #查看内存使用量和交换区使用量
    df -h #查看各分区使用情况
    du -sh <目录名> #查看指定目录的大小
    grep MemTotal /proc/meminfo #查看内存总量
    grep MemFree /proc/meminfo #查看空闲内存量
    uptime #查看系统运行时间、用户数、负载
    cat /proc/loadavg #查看系统负载
    mount | column -t #查看挂接的分区状态
    fdisk -l #查看所有分区
    swapon -s #查看所有交换分区
    hdparm -i /dev/hda #查看磁盘参数(仅适用于IDE设备)
    dmesg | grep IDE #查看启动时IDE设备检测状况

------------

### 网络命令
    ifconfig #查看所有网络接口的属性
    iptables -L #查看防火墙设置
    route -n #查看路由表
    netstat -lntp #查看所有监听端口
    netstat -antp #查看所有已经建立的连接
    netstat -s #查看网络统计信息

------------


### 进程命令
    ps -ef #查看所有进程
    top #实时显示进程状态

------------


### 用户命令
    w #查看活动用户
    id <用户名> #查看指定用户信息
    last #查看用户登录日志
    cut -d: -f1 /etc/passwd #查看系统所有用户
    cut -d: -f1 /etc/group #查看系统所有组
    crontab -l #查看当前用户的计划任务

------------


### 服务命令
    chkconfig --list #列出所有系统服务
    chkconfig --list | grep on #列出所有启动的系统服务

------------


### 软件命令

    rpm -qa #查看所有安装的软件包


