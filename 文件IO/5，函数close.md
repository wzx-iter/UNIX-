## 功能

​	关闭一个打开的文件

```c
#include <unistd.h>
int close (int fd);
 //若成功返回0，失败返回-1
```

​	关闭一个文件还会释放该进程加在该文件上的所有记录锁。

   一般一个进程终止，内核会关闭其所有的打开文件，无需手动显示调用关闭。

