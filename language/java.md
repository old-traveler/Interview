## Object中的方法
getClass
hashCode
clone
toString
equals
finalize
wait
notify
notifyAll

## static 和 final
* static可以修饰：属性，方法，代码段，内部类（静态内部类或嵌套内部类）
* static修饰的属性的初始化在编译期（类加载的时候），初始化后能改变。
* static修饰的属性所有对象都只有一个值。
* static修饰的属性强调它们只有一个。
* static修饰的属性、方法、代码段跟该类的具体对象无关，不创建对象也能调用static修饰的属性、方法等
* static不可以修饰局部变量。

* final修饰的属性的初始化可以在编译期，也可以在运行期，初始化后不能被改变。
* final修饰的属性跟具体对象有关，在运行期初始化的final属性，不同对象可以有不同的值。
* final修饰的属性表明是一个常数（创建后不能被修改）。
* final修饰的方法表示该方法在子类中不能被重写，final修饰的类表示该类不能被继承。

final本身并不是jvm中的字节码指令，只是用于javac中的编译检查，被标记后再修改会在编译时报错。
基础类型变量被final修饰，会直接使用固定值而不使用本地变量表，引用类型被final修饰仅用于编译插件，字节码上无差异

## 内部类的作用
封装、多重继承
https://blog.csdn.net/dingyahui123/article/details/68490982

* 内部类和外部类为什么可以访问对方的私有变量
会生成一个静态方法供获取

https://www.zhihu.com/question/54730071
