## 功能：

​	更改文件的用户ID和组ID，如果两个参数owner或group中的任一个是-1，则对应的ID不变。



## 函数体

![image-20220402104117675](../image/image-20220402104117675.png)



除了所引用的文件是符号链接以外，这4个函数的操作类似。在符号链接情况下，lchown和fchownat（设置了AT_SYMLINK_NOFOLLOW标志）更改符号链接本身的所有者，而不是该符号链接所指向文件的所有者。

fchown函数改变fd参数指向的打开文件的所有者，既然它在一个已打开的文件上操作，就不能用于改变符号链接的所有者。

fchowndat函数和chown或lchown函数在下面两种情况下是相同的：一种是pathname参数为绝对路径，另一种是dirfd参数取值为AT_FDCWD而pathname参数为相对路径。在这两种情况下，如果flags参数中设置了AT_SYMLINK_NOFOLLOW标志，则fchownat跟lchown行为相同，如果flags参数中清除了AT_SYMLINK_NOFOLLOW标志，则fchownat跟chown行为相同。否则，fchowndat计算相对于打开目录（由dirfd参数指向）的pathname。
