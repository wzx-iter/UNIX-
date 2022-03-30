## 功能：

​	 创建一个新文件

```c
#include <fcnt1.h>
int creat(const char *path, mode_t mode);
				//若成功返回只写打开的文件符，若出错返回-1
```

不足之处：以只写方式打开所创建的文件



等效于：

`open (path, O_WRONLY | O_CREAT | O_TRUNC, mode)`

