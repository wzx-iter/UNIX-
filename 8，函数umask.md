## 功能：

​	为进程设置文件模式创建屏蔽字，并返回之前的值



## 函数体

![image-20220401144157320](../image/image-20220401144157320.png)



参数cmask是之前列出9个常量中的按位或。

在进程创建一个新文件和新目录时都会使用文件模式创建屏蔽字如，如O_RDONLY中这些也就时mode，指定新文件访问权限位。





umask创建屏蔽字，umask（0）表示的时 7 7 7 

```c
#include <stdio.h>
#include <fcntl.h>

#define RWRWRW (S_IRUSR|S_IWUSR|S_IRGRP|S_IWGRP|S_IROTH|S_IWOTH)

int main(void)
{
	umask(0);
	if(creat("foo",RWRWRW) < 0)
		perror("creat error for foo");
	umask(S_IRGRP|S_IWGRP|S_IROTH|S_IWOTH);
	if(creat("bar",RWRWRW)<0)
		perror("creat error for bar");
	

	return 0;

}
```

foo的权限: rw rw rw

bar的权限:-rw --- ---



该进程的父进程时shell，umask的值时002，该进程如何创建umask屏蔽字都不会影响父进程的umask,可以看出umask的功能就是控制访问权限。
