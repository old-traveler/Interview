## Flutter2.0
https://www.zhihu.com/question/447488806
* web支持进稳定版，桌面支持进入早期稳定版
* 空安全支持
* Idea插件优化 FlutterFix、DartFix（解决框架升级的适配工具，查找废弃api）
* 引擎内存优化（单引擎180kb）
共享引擎的问题：
Flutter Boost是从应用层出发，直接复用FlutterView从而共享Flutter Engine。Native侧实现时，需要共享FlutterView，不同Activity/ViewController切换时
，需要将FlutterView从前页面的Activity/ViewController移除，然后添加到当前页面的Activity/ViewController。这个过程在Android上能够明显的感觉到页面的闪动。
Flutter 1.12的发布完美的解决了这个问题，Flutter 1.12支持将Flutter Engine通过id缓存起来，然后启动页面时，可以指定使用缓存中的Engine，
从而彻底解决了混合开发共享引擎的问题。页面间使用缓存引擎方案，需要将Native侧页面和Dart侧页面一一对应。可以使用Message Channel通信，结合路由跳转中心，由Native页面驱动即可。
