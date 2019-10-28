---
title: java
date: 2019-08-19 10:37:00
ags:
---

Write Once,Run Everywhere
 <!--more-->
 **达到对面向对象编程思想更加深入的理解，是对面向对象的各种特性及其实现细节更加熟练的掌握。** 
 ---

 *一步一个脚印的连好java的基本功。对于我来说是最好不过的，掌握java的基本语法。(类与对象，构造方法，引用传递，内部类，异常，包，java常用类库，javaIO，java类集)* 

1. 走技术之路(在学习java的同时，把基础的知识打好一定的基础)
2. 定位成为技术类管理成员(掌握基础的java知识，还要有几年的工作经验)
3. java软件开发发展前景好，移植性也很强。
- [ ] JDK(java开发工具包)

*是编程语言和javaAPI类库和java虚拟机(是完成移植性的重要机制)来组成的* 

- [ ] JRE(java运行时环境)
*是javaAPI子集和java虚拟机组成* 
**前面二者的区别是：JDK包含着JRE。如果仅仅是运行java程序的话就需要JRE。如果是要自己动手写java程序就要部署JDK环境。** 
---

**java系统可分为：javaEE(标准版)，javaSE(企业版)，javaME(微型版)，javaCARD(智能卡版)** 

```
//有必要说明一下，接下来的是在linux系统下使用终端来让我电脑上的文件进行运行

public class hello{//public(公有访问类型),class(类的标识),hello(类名)
    public static void main (String arg[]){//是main函数的基本格式,也表明了这里的main是公有的静态方法
    System.out.println("hello,world!");//打印字符串"hello,world!"
    }
}
```
![终端运行的结果](Java/java0.png) 

**这里要注意一下的就是文件的后缀是.java,其次是以javac 来作为第一次的关键字来操作文件，接着就会生成一个后缀为.class的文件，然后就是运行你写的文件，记住后面没有任何的后缀。** 
