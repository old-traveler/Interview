## dex、odex、vdex、art、oat
https://www.jianshu.com/p/f48eac038384
补充： 引入vdex的目的
目的不是为了提升性能，而是为了避免不必要的验证Dex 文件合法性的过程，例如首次安装时进行dex2oat时会校验Dex 文件各个section的合法性，这时候使用的compiler filter 为了照顾安装速度等方面，并没有采用全量编译，当app盘启动后，运行一段时间后，收集了足够多的jit 热点方法信息，Android会在后台重新进行dex2oat, 将热点方法编译成机器代码，这时候就不用再重复做验证Dex文件的过程了，我测试了下，例如支付宝淘宝这类Dex文件比较大的app在Nexus 5X上大概可以节省2秒左右时间。

