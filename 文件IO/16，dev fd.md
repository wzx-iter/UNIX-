## /dev/fd:

​	较新的一些系统提供了名为/dev/fd的目录。里边的目录项是名为0,1,2的文件，打开文件/dev/fd/n相当于复制描述符号n。

 例如 : fd = open("/dev/fd/0",mode);



大多数系统会忽略掉mode,其相当于

fd =  dup(0);



如果调用文件描述符0打开之前是只读模式，不管mode设置成什么都会忽略。

下面的调用时可行的；

fd = open("/dev/fd/0",O_RDWR);  

但是我们不能对fd进行写操作。



/dev/fd/n 可以用creat调用,但是在linux上必须小心，一般不建议使用。



还有一些系统提供 /dev/stdin,/dev/stdout,/dev/stderr,等效于/dev/fd/0,1,2;



