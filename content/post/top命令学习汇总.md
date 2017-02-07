+++
date = "2017-01-01T23:31:00+08:00"
draft = false
title = "top命令学习汇总"
tags = ["linux", "top"]
categories = ["学习总结"]
+++


## 常规用法:

查看cpu信息

```
root@iZwz9bruzaqhhifjeavouzZ:~# top
top - 23:43:11 up 51 days, 11:00,  1 user,  load average: 0.05, 0.05, 0.05
Tasks:  88 total,   1 running,  87 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.3 us,  1.0 sy,  0.0 ni, 97.3 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   1017712 total,   905048 used,   112664 free,   205412 buffers
KiB Swap:        0 total,        0 used,        0 free.   368316 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S %CPU %MEM     TIME+ COMMAND
    1 root      20   0   36672   4964    504 S  0.0  0.5   0:02.99 init
    2 root      20   0       0      0      0 S  0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S  0.0  0.0   0:28.03 ksoftirqd/0
```


查看各个cpu使用情况，top后，再按1，
```
[root@SE ~]# top
top - 00:04:12 up 12 days,  2:53,  1 user,  load average: 0.15, 0.07, 0.01
Tasks: 508 total,   1 running, 507 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  0.0%sy,  0.0%ni, 99.0%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu8  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu9  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu10 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu11 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu12 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu13 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu14 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu15 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu16 :  0.0%us,  0.3%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu17 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu18 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu19 :  0.3%us,  0.0%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu20 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu21 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu22 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu23 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  32837188k total,  3460832k used, 29376356k free,  1142872k buffers
Swap: 32767992k total,        0k used, 32767992k free,  1340076k cached

   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  2160 root      20   0     0    0    0 S  0.3  0.0   0:20.46 kondemand/16
     1 root      20   0 19224 1544 1252 S  0.0  0.0   0:03.73 init
     2 root      20   0     0    0    0 S  0.0  0.0   0:00.02 kthreadd
```

查看指定进程的所有线程使用cpu情况，top -Hp pid，
```
[root@SE ~]# top -Hp 1
top - 00:05:36 up 12 days,  2:54,  1 user,  load average: 0.04, 0.05, 0.00
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  32837188k total,  3459404k used, 29377784k free,  1142880k buffers
Swap: 32767992k total,        0k used, 32767992k free,  1340088k cached

   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
     1 root      20   0 19224 1544 1252 S  0.0  0.0   0:03.73 init
```

top后，再分别按PTM，按CPU、时间、内存降序排列


参考资料:

各列详细说明，http://www.cnblogs.com/me115/p/3842081.html

各列详细说明，外加部分使用案例 http://www.cnblogs.com/peida/archive/2012/12/24/2831353.html

各列详细说明，以及其他一些有用工具，http://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/top.html

