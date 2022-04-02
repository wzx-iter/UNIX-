## 功能

​	ioctl函数一直是I/O操作的杂物箱，不能用本章其他函数表示的IO操作都通常都可以用ioctl表示。



## 函数体

```c
#include <sys/ioctl.h>
int ioctl(int fd, int request,...);
//若成功返回其他值，失败返回-1
```

第二个参数总是头文件定义#define的一些常量，第三个通常是一个变量或结构体的指针。

