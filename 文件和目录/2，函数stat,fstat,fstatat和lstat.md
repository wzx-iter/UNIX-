## 函数体

​	

```c
#include <sys/stat.h>
int stat(const char *restrict pathname,struct stat *restrict buf);
int fstat(int fd,struct stat *buf);
int lstat(const char *restrict pathname,struct stat *restrict buf);
int fstatat(int fd,const char *restrict pathname,struct stat *restrict buf,int flag);
//若成功返回0，失败返回-1
```

## 各函数功能

pathname，

stat:返回与此命名文件有关的信息结构。

fstat：获得已在已在描述符fd上打开文件的有关信息，

lstat：获得该符号连接的有关信息，而不是链接引用的文件信息。在降序遍历目录结构时会用到。

fstatat：为一个相对于当前打开目录的路径名返回文件统计信息；flag参数控制着是否跟随着一个符号链接，当AT_SYMLINK_NOFOLLOW标志被设置时，fsatata不会跟随着符号链接，而是返回符号链接本身的信息，否则，在默认情况下，返回的是符号链接所指向的实际文件的信息。

如果fd参数的值为AT_FDCWD，并且参数pathname是相对路径，fstatat会计算当前目录的pathname参数，如果是绝对路径名，那么就会fd参数可以忽略。这两种情况下，根据flag取值，fstatat的作用和lstat或stat一样



## 参数buf

​	一个指向stat结构体的指针

大致内容如下：

![image-20220331153003919](../image/image-20220331153003919.png)



使用stat函数最多的地方可能就是 ls -l  可以获得一个文件所有的相关信息。