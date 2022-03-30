## 功能：

​	调用函数wirte向打开文件写数据。



## 函数体：

​	

```c
#include <unistd.h>
ssize_t write(int fd,const void *buf,size_t nbytes);
	//若成功返回已写字节数，错误返回-1
```



​	返回值一般于nbytes的值相同，否则表示出错，wirte出错的一个常见的原因是磁盘写盘或者是超过了一个给定的进程的文件长度限制。



注意：如果要在尾端写数据应该在打开文件的时候设定选项O_APPEND。