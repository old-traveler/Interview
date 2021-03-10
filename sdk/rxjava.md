## rxjava的线程调度
RxJava的线程调度实际上是一个调用链实现的
eg：
```
Flowable.just(imageFile)
        .observeOn(Schedulers.io())
        .map(uris -> Luban.with((BaseActivity) observer)
            .load(uris)
            .ignoreBy(100)
            .filter(path -> !(TextUtils.isEmpty(path) || path.toLowerCase().endsWith(".gif")))
            .get())
        .observeOn(AndroidSchedulers.mainThread())
        .subscribe(files -> FileHelper.uploadImage(userBean, "0", files, uploadBeanObserver),
            observer::onError);
```
  跟这段代码的调用顺序类似，运行时RxJava的执行顺序也如上一致
  实现的原理，通过装饰者的设计模式，将传入的Scheduler或者Function对象与当前源对象生成一个装饰者对象。外部调用订阅方法时先调用装饰者对象，
  装饰者对象会继而再调用源对象的订阅方法并同时再将之前的Scheduler或者Function对象与传入的Subscriber对象生成一个新的订阅者对象。
  
  订阅的调用顺序从下到上，完成订阅链路的绑定，被观察者发生变化后，通知订阅者的调用顺序从上到下
  （生成的装饰订阅者对象收到通知后会先调用传入的Scheduler进行线程切换或者调用传入的Function对象进行转化，再调用实际的订阅者对象，也就是订阅时传入的订阅者）
  
 如果要自定义不同的操作符，只需要实现对应的一个FlowableXX然后在实际订阅的时候调用source的订阅方法，并且传入自己实现的订阅者对象。并且操作的功能实现就在这个装饰的订阅者中实现
 比如FlowableMap就定义了自己的内部订阅者class MapSubscriber ，在onNext的时候会先调用mapper方法对返回的数据就行转化，然后再将转化后的数据传递给下一级的订阅者
