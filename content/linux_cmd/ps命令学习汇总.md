+++
date = "2017-01-01T23:30:28+08:00"
draft = false
title = "ps命令学习汇总"
tags = ["linux", "ps"]
categories = ["学习总结"]
+++

常用用法，查看进程cpu、占用内存、虚拟内存信息
```
[root@SE ~]# ps axu
USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root          1  0.0  0.0  19224  1544 ?        Ss    2016   0:03 /sbin/init
root          2  0.0  0.0      0     0 ?        S     2016   0:00 [kthreadd]
root          3  0.0  0.0      0     0 ?        S     2016   0:03 [migration/0]
root          4  0.0  0.0      0     0 ?        S     2016   0:06 [ksoftirqd/0]
root          5  0.0  0.0      0     0 ?        S     2016   0:00 [migration/0]
root          6  0.0  0.0      0     0 ?        S     2016   0:01 [watchdog/0]

```

查看进程启动精确时间。ps -ef可以看到进程的启动时间，但是这个时间如果超过24小时就只能看到年份了，使用如下命令可以看到精确的启动时间。

```
[root@store02-2sn ~]# ps -eO lstart|grep se-
 63138 Wed Dec 21 10:30:39 2016 S ?        2-01:10:38 /opt/se/modules/se-lte2db/se-lte2db
 63276 Wed Dec 21 10:30:49 2016 S ?        16:32:35 /opt/se/modules/se-fileproc/se-fileproc
```
