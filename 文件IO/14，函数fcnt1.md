## 功能：函数fcnt1

​	(1) 复制一个已有的描述符（cmd=F_DUPFD 或 F_DUPFD_CLOEXEC）；

 （2）获取/设置文件描述符标志(cmd=F_GETFD 或 F_SETFD)；

   (3)获取/设置文件状态标志(cmd=F_GETFL 或 F_SETFL);

   (4)获取/设置异步I/O所有权(cmd = F_GETOWN 或 F_SETOWN)。

（5）获取/设置记录锁（cmd = F_GETLK,F_SETLK 或 F_SETLKW）。

各cmd标志详细说明 P66

## 函数体

```c
#include <fcnt1.h>
int fcnt1(int fd, int cmd, .../*int arg*/);
	//返回成功则依赖于cmd,失败则返回-1
```

