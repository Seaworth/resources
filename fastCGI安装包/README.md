在网上找了很久，都没有下载到`fcgi-2.4.1-SNAP-0910052249.tar.gz`这个版本的安装包，在csdn上用积分下载下来，保存在`GitHub`上，方便以后取用。

顺便记录下安装过程：

一共需要两个安装包：

- `fcgi-2.4.1-SNAP-0910052249.tar.gz`
- `spawn-fcgi-1.6.4.tar.gz`

主要是`fcgi-2.4.1-SNAP-0910052249.tar.gz`安装过程有一点小坑。

1. 解压并进入目录

```shell
tar -zxvf fcgi-2.4.1-SNAP-0910052249.tar.gz
cd fcgi-2.4.1-SNAP-0910052249
```

2. 打开该目录下的`libfcgi/fcgio.cpp`文件，添加头文件`#include <stdio.h>`

```
vim libfcgi/fcgio.cpp
```

然后在头文件的位置添加`#include <stdio.h>`，保存退出。添加这个的目的是因为直接执行`./configure`会报错，说`EOF`没有在该工作空间定义。在头文件`stdio.h`中有对宏`EOF`的定义，所以在`fcgio.c`中添加该头文件即可。错误如下：

![](https://user-images.githubusercontent.com/30982520/79546854-b0b84380-80c5-11ea-9c6a-e05edb77a6d9.png)

3. 执行配置文件并make安装

```
./configure
make
sudo make install
```



`spawn-fcgi-1.6.4.tar.gz`的安装比较简单，没什么坑，步骤如下：

```
tar -zxvf spawn-fcgi-1.6.4.tar.gz
cd spawn-fcgi-1.6.4
./configure
make
sudo make install
```


