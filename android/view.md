## 帧率统计
https://zhuanlan.zhihu.com/p/108022695
通过Choreographer的postFrameCallback

## requestLayout和invalidate区别
* requestLayout 会触发当前节点和其上父节点调用onMeasure和onLayout（可能会触发onDraw方法）
* invalidate（硬件加速）只触发当前节点的onDraw
* invalidate（非硬件加速）触发当前View的子树以及parent路径节点的onDraw



https://www.jianshu.com/p/b6437e4b81ac

## RecyclerView的缓存机制
https://www.jianshu.com/p/3e9aa4bdaefd

## RecyclerView的局部刷新
notifyXXX 实际上是给指定范围的viewholder打上标记，后续会通过判断标志位来确定是否需要调用onBindViewHolder方法
存在的问题，默认的局部刷新粒度为整个itemView，实际需求中可能只刷新itemView中的某些控件，可以通过payload来解决
RecyclerView刷新图片闪烁，通过取消默认动画解决

## window机制
https://juejin.cn/post/6888688477714841608#heading-19

## UI绘制原理
https://www.jianshu.com/p/d3be5def8398

## 事件分发
https://www.jianshu.com/p/238d1b753e64

## 嵌套滑动
https://juejin.cn/post/6844903788789104648
