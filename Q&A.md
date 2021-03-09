
双缓冲 
MainThread和ReaderThread  https://www.androidperformance.com/2019/11/06/Android-Systrace-MainThread-And-RenderThread/
TCP  https://blog.csdn.net/qzcsu/article/details/72861891 https://zhuanlan.zhihu.com/p/37379780
SSL  https://zhuanlan.zhihu.com/p/72616216
事件分发 https://www.jianshu.com/p/238d1b753e64
activity 启动流程 https://juejin.cn/post/6844904116561379341   https://www.jianshu.com/p/d3be5def8398 https://zhuanlan.zhihu.com/p/27344882
Looper.getMainLooper().setMessageLogging {
  if (it.contains("FrameHandler") && it.contains(": 0")) {
    frameStart = System.currentTimeMillis()
    return@setMessageLogging
  }
  if (frameStart != 0) {
    frameEndTime = System.currentTimeMillis()
    Looper.getMainLooper().setMessageLogging(null)
  }
}
window?.decorView?.viewTreeObserver?.registerFrameCommitCallback {
  Log.d("HYC","registerFrameCommitCallback"+System.currentTimeMillis())
}
binder https://zhuanlan.zhihu.com/p/35519585
动态代理的实现。动态生成class   https://www.jianshu.com/p/23d3f1a2b3c7
mvvm  https://www.jianshu.com/p/ca40d4269c86  https://www.jianshu.com/p/699cf6117b53
retrofit  https://zhuanlan.zhihu.com/p/35121326
okhttp 连接池复用   https://www.jianshu.com/p/e4705ee2311a https://juejin.cn/post/6844904037167415310
插件化 https://zhuanlan.zhihu.com/p/33017826
四大组件原理
设计模式复习
算法复习
