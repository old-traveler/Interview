## android apt
apt为注解解释器，在java文件被编译成class文件的过程中被调用，具体是在javac将源代码编译成AST（抽象语法树）之后会触发注解处理过程。会将编译好的AST作为输入交给解释器分析处理，然后得出修改后的AST继续编译流程

## javac 编译流程
.java->parse(词法分析) -> enter （生成符号表） -> process (处理注解) ->attr（检查语义合法性、常量折叠） -> flow（数据流分析） -> desugar （去除语法糖） -> generate（生成字节码）
