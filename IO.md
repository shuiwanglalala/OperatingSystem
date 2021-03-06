# IO

[【面试】迄今为止把同步/异步/阻塞/非阻塞/BIO/NIO/AIO讲的这么清楚的好文章（快快珍藏）](https://mp.weixin.qq.com/s?__biz=MzIyNjAzODEyMg==&mid=2247484746&idx=1&sn=5146ae815c4bf560b8df809c2f81c78b&source=41#wechat_redirect)

## 同步和异步 阻塞和非阻塞

### 同步异步

所谓同步，指的是协同步调。既然叫协同，所以至少要有2个以上的事物存在。协同的结果就是：

多个事物不能同时进行，必须一个一个的来，上一个事物结束后，下一个事物才开始

关于同步还需知道两个小的点：

一是范围，并不需要在全局范围内都去同步，只需要在某些关键的点执行同步即可。

比如食堂只有一个卖饭窗口，肯定是同步的，一个人买完，下一个人再买。但吃饭的时候也是一个人吃完，下一个人才开始吃吗？当然不是啦。

二是粒度，并不是只有大粒度的事物才有同步，小粒度的事物也有同步。

只不过小粒度的事物同步通常是天然支持的，而大粒度的事物同步往往需要手工处理。

比如两个线程的同步就需要手工处理，但一个线程里的两个语句天然就是同步的。

所谓异步，就是步调各异。既然是各异，那就是都不相同。所以结果就是：

多个事物可以你进行你的、我进行我的，谁都不用管谁，所有的事物都在同时进行中

### 阻塞和非阻塞

因此阻塞关注的是不能动，非阻塞关注的是可以动

不能动的结果就是只能等待，可以动的结果就是继续前行

### 两两组合

同步阻塞，相当于一个线程在等待。

同步非阻塞，相当于一个线程在正常运行。

异步阻塞，相当于多个线程都在等待。

异步非阻塞，相当于多个线程都在正常运行

## I/O

IO指的就是读入/写出数据的过程，和**等待**读入/写出数据的过程。一旦拿到数据后就变成了数据操作了，就不是IO了

拿网络IO来说，等待的过程就是数据从网络到网卡再到内核空间。读写的过程就是内核空间和用户空间的相互拷贝

所以IO就包括两个过程，一个是等待数据的过程，一个是读写（拷贝）数据的过程。而且还要明白，一定**不**能包括操作数据的过程

### 阻塞IO和非阻塞IO

应用程序都是运行在用户空间的，所以它们能操作的数据也都在用户空间。按照这样子来理解，只要数据没有到达用户空间，用户线程就操作不了。

如果此时用户线程已经参与，那它一定会被阻塞在IO上。这就是常说的阻塞IO。用户线程被阻塞在等待数据上或拷贝数据上。

非阻塞IO就是用户线程不参与以上两个过程，即数据已经拷贝到用户空间后，才去通知用户线程，一上来就可以直接操作数据了。

用户线程没有因为IO的事情出现阻塞，这就是常说的非阻塞IO

### 同步IO和同步阻塞IO

按照程序的表现形式又分为两种：

+ 在等待数据的过程中，和拷贝数据的过程中，线程都在阻塞，这就是同步阻塞IO。

+ 在等待数据的过程中，线程采用死循环式轮询，在拷贝数据的过程中，线程在阻塞，这其实还是同步阻塞IO。

网上很多文章把第二种归为同步非阻塞IO，这肯定是**错误**的，它一定是阻塞IO，因为拷贝数据的过程，线程是阻塞的。

严格来讲，在IO的概念上，同步和非阻塞是不可能搭配的，因为它们是一对相悖的概念。

+ 同步IO意味着必须拿到IO的数据，才可以继续执行。因为后续操作依赖IO数据，所以它必须是阻塞的。

+ 非阻塞IO意味着发起IO请求后，可以继续往下执行。说明后续执行不依赖于IO数据，所以它肯定不是同步的。

因此，在IO上，同步和非阻塞是互斥的，所以不存在同步非阻塞IO。但同步非阻塞是存在的，那不叫IO，叫操作数据了。

所以，同步IO一定是阻塞IO，同步IO也就是同步阻塞IO

### 异步IO和异步阻塞/非阻塞IO

按照IO数据的两个过程，又可以分为两种：

+ 在等待数据的过程中，用户线程继续执行，在拷贝数据的过程中，线程在阻塞，这就是异步阻塞IO
  
  + 第一种情况是，用户线程没有参与数据等待的过程，所以它是异步的。但用户线程参与了数据拷贝的过程，所以它又是阻塞的。合起来就是异步阻塞IO

+ 在等待数据的过程中，和拷贝数据的过程中，用户线程都在继续执行，这就是异步非阻塞IO
  
  + 第二种情况是，用户线程既没有参与等待过程也没有参与拷贝过程，所以它是异步的。当它接到通知时，数据已经准备好了，它没有因为IO数据而阻塞过，所以它又是非阻塞的。合起来就是异步非阻塞IO