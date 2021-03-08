## Java classLoader机制
jdk配置classpath
双亲委托机制（parent是传入的非继承）
BootstrapClassLoader是native实现
classloader加密机制
Thread ContextClassLoader
https://blog.csdn.net/briblue/article/details/54973413

## Android DexClassLoader机制

## Class文件加载过程
https://zhuanlan.zhihu.com/p/25228545
补充：通过classLoader.loadClass(Class.forName这种间接使用classLoader的)方法去加载Class对象的，并不会触发<clinit>方法的调用
类加载流程：
  加载：读取class文件中的字节码数据流，将数据流存储在方法区中，并且在堆区中新建Class对象，提供到方法区获取类信息的接口
  链接：验证（文件格式验证、元数据验证、字节码验证）->准备（给类变量分配内存并附上默认值 非代码中设置的默认值）->解析 （将符号引用替换成直接引用，直接引用为内存指针+偏移量）
  初始化：执行<clinit>方法，初始化静态变量和静态代码块
