---
title: java
date: 2019-09-19 10:37:00
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
---

```
//有必要说明一下，接下来的是在linux系统下使用终端来让我电脑上的文件进行运行

public class hello{//public(公有访问类型),class(类的标识),hello(类名)
    public static void main (String arg[]){//是main函数的基本格式,也表明main函数是静态方法
    System.out.println("hello,world!");//打印字符串"hello,world!"
    }
}
```
![终端运行的结果](Java/java0.png) 
---


**这里要注意一下的就是文件的后缀是.java,其次是以javac 来作为第一次的关键字来操作文件，接着就会生成一个后缀为.class的文件，然后就是运行你写的文件，记住后面没有任何的后缀。** 

* **java是面向对象的过程，也就是说在java中只有方法而没有所谓的函数。** 

```
public class Test{
    public static void main(String args[]){
    scanner s=new scanner(System.in);//为了可以让用户输入，在这里使用了scanner类,因为它附属与System.in
    System.out.println("请输入你的性别");
    String set=s.nextLint();//以字符串的形式输入
    System.out.println("请输入你的姓名");
    String name =s.nextLint();
    switch(set){
    case "男":
    System.out.println(name+"男士");
    break;
    case "女":
    System.out.println(name+"女士");
    break;
    default :
    System.out.println("输入有误");
    break;
    }
    s.close();//关闭类
}

```


![运行结果](Java/java2.png)


![输入的方式](Java/java1.png)

*在这里只是简单的让用户输入了两次都是以字符串的方式来输入的，当然你也可以让用户输入你想让用户输入的数据类型(eg:int ,double)，上面也有参照的照片。* 

* **合法的标识符** 
- [ ] 不能存在关键字
- [ ] 首字母不能是数字
- [ ] 不能存在运算符
- [ ] 标识符是区别大小写的
- [ ] 标识符的命令规则是强制性的

`我们都知道数据的类型有int,short,float,double,byte(字节)。最常见的就是int(整形的数据类型)。在java中我们可以通过程序来输出各个数据类型的范围是多少，最大值和最小值，和数据类型
`

```
public class Test{
    public static void main (String args[]){
    int a=Integer.Size;
    System.out.println("int的范围:"+a);
    int b=Integer.MAX_VALUE;
    System.out.println("int的最大值:"+b);
    int c=Integer.MIN_VALUE
    System.out.println("int的最小值:"+c);
    Class <Integer> d=Integer.TYPE;
    System.out.println("数据类型:"+d);
    }
}
```

```
运行结果：
int的范围:32
int的最大值:2147483647
int的最小值:-2147483648
数据类型:int
```
---
```
public class Test{
            static int i=10;
    public static void main(String args[]){
            int a=1;
            int b=2;
            {
            int b=3;//main方法的变量名是不可以重复的，一个变量只能使用一个名，在这里就是重复使用了变量b，所以程序会报错。
            System.out.println("b="+b);
            System.out.println("a="+a);
            System.out.println("i="+i);
            }
            System.out.println("b="+b);
            System.out.println("a="+a);
            System.out.println("i="+i);

    }
}
```

```
上面的程序是运行不过的，这也是java的特别之处，在c++中，变量b是可以用的，但在java中是不可以的。
```


