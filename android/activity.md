## 启动模式
https://www.jianshu.com/p/2c73be80ce8d

## 跳转生命周期变化&打开Dialog生命周期变化
https://blog.csdn.net/cdkd123/article/details/93078140
https://www.jianshu.com/p/6d9d830a758d
打开属于本Activity的Dialog生命周期不会回调
打开属于其他Activity的Dialog生命周期会回调onPause
A打开B A onPause、B onCreate 、 B onStart、 B onResume、 A onStop

