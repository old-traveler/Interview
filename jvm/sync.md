## monitorenter和monitorexit的原理
这段话的大概意思为：
每个对象都有一个监视器锁(monitor)与之对应。当monitor被占用时就会处于锁定状态，线程执行monitorenter指令时尝试获取monitor的所有权，过程如下：
* 1、如果monitor的进入数为0，则该线程进入monitor，然后将进入数设置为1，该线程即为monitor的所有者。
* 2、如果线程已经占有该monitor，只是重新进入，则进入monitor的进入数加1.
* 3.如果其他线程已经占用了monitor，则该线程进入阻塞状态，直到monitor的进入数为0，再重新尝试获取monitor的所有权。

## syncronized 修饰静态方法和修饰方法和修饰代码块的区别
|  维度   | 静态同步方法  | 同步方法 | 同步代码块 |
|  ----  | ----  | ---- | ---- |
| 锁对象  | 当前class对象 |  当前实例 |  传入对象 |
| 字节码  | 标记方法为ACC_SYNCRONIZED | 同静态方法 | 进入指令monitorenter将同步代码块转化为try-catch块，并在每个出口加上monitorexit |


## syncronized的原理
https://blog.csdn.net/javazejian/article/details/72828483
https://blog.csdn.net/yinwenjie/article/details/84922958

通过monitorenter + 对象 的指令获取锁
通过monitorexit + 对象的指令退出锁

https://github.com/JsonChao/Awesome-Android-Interview/blob/master/Java%E7%9B%B8%E5%85%B3/Java%E5%B9%B6%E5%8F%91%E9%9D%A2%E8%AF%95%E9%A2%98.md

ObjectMonitor结构
* void *  volatile _owner;          // 占用当前锁的线程
* volatile intptr_t  _recursions;   //记录嵌套（递归）加锁的次数，最外层的锁的_recursions属性为0
* int OwnerIsThread ;               // 表明当前owner原来持有轻量级锁
* ObjectWaiter * volatile _EntryList ;     // EntryList 链表头元素
* volatile intptr_t  _count;        // 抢占该锁的线程数
* ObjectWaiter * volatile _WaitSet; // 调用wait方法后等待的ObjectWaiter链表
* volatile int _WaitSetLock;        // 操作WaitSet链表的锁

## volatile
禁止指令重排
读可见性（每次从主内存刷新，修改时刷新主内存）

## 公平锁和非公平锁的区别

结构应该还是链表构成的队列，每次都是从队列中出队，不会遍历都唤醒，不公平的原因是，当队列中有排队的线程时，新线程过来，不会先排队，而是直接去申请锁，拿不到锁的时候才会去排队，这样就不公平，公平应该先排队。之前的理解上出问题了

https://mp.weixin.qq.com/s?__biz=MjM5NjQ5MTI5OA==&mid=2651749434&idx=3&sn=5ffa63ad47fe166f2f1a9f604ed10091&chksm=bd12a5778a652c61509d9e718ab086ff27ad8768586ea9b38c3dcf9e017a8e49bcae3df9bcc8&scene=38#wechat_redirect

指令重排：

https://www.cnblogs.com/xdecode/p/8948277.html

只会对独立的指令进行重排，存在依赖关系的指令不会重排，指令重排的目的是为了减少因为依赖所导致的空闲等待

