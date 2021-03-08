## finalize原理
finalize 方法高度依赖 JVM 和 GC，当一个对象被标记后，便会被 JVM 包装成 Finalizer 对象，然后，被 JVM 设置到 Reference 的静态属性 pending 中，Reference 的内部线程则会将这个 pending 放入到构造函数的队列中。Finalizer 的内部线程则会从队列中取出 Finalizer 对象，并调用其包装的实际对象的 finalize 方法。所以，finalize 方法需要两个线程来处理他，一个是 ReferenceHandler ，一个是 FinalizerThread。前者负责将 Finalizer 对象放入到 Reference 队列中，后者负责从队列中取出 Finalizer 对象并调用实际对象的 finalize 方法。同时，GC 大概也要做 2 件事情，一个是创建 Finalizer 对象，一个是将该对象设置到自己的 pending 属性中。

finalize（）方法是对象逃脱死亡的最后机会，稍后GC会对F-Queue队列进行第二次标记。如果objA在finalize（）方法中与引用链上的任何对象建立联系，那么在第二次标记时，objA会被移出“即将回收”集合。之后，对象会再次出现没有引用存在的情况。在这个情况下，finalize（）方法不会被再次调用，对象会直接变为不可触及状态，也就是说一个对象的finalize（）方法只会被调用一次。
