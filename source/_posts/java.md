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
    InputStreamReader input=new InputStreamReader(System.in);//定义在键盘输入
    BufferedReader Buff=new BufferedReader(input);//以缓冲流的形式来接受input
    //用try和catch机制来处理异常
    try{
    System.out.println("请输入字符：");
    String s=Buff.readLine();
    System.out.println("字符："+s);
    }catch (Exception e){
    System.out.println("异常");
    }
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
```
public class Test{
    public static void main (String args[]){
            char ch = '\"';//转义字符
            System.out.println(ch);
            System.out.println("\"hello,world!"\");
            System.out.println(ch+"hello,world!"+ch);
    }
}
```

```
运行结果
"
"hello,world!"
"hello,world!"
```
---

`总结可以得知，不管是用变量来存放转义字符，还是直接使用转义字符的方式来输出字符，程序都是可以顺利运行的，当然你也可以不使用变量来存放转义字符，但一个程序里面有太多的转义字符的存在你用变量来存放不是更好使用？这样你也不容易搞混已有的转义字符的使用。` 

```
public class Test{
    public static void main(String args[]){
        System.out.println(2+3+"k");
        System.out.println(6+6+"aa"+6+6);
    }
}
```

```
运行结果
5k
12aa66
```
---

`上面的2+3是一个表达式，所以这里是5,但后面跟的是字符和+(字符串相加)的符号，所以是5k,下面的也是一样的，唯一不一样的是在+(字符串相加)之后，计算机会自动认为后面的也是+(字符串相加)所以后面的就是12aa66。但如果把上面的双引号换成单引号就是以数字的形式先加后输出的。` 

# 数组

import java.util.Randow;//随机数字的包

```
public class Test{
    public static void main(String args[]){
                int i=3;//这是在堆内存的分配的内存(也可以说是在编译是分配的),读取速度快，但数据的活动范围小(缺少灵活性)
                int y=new Integer(1);//是在栈内存分配的内存(也可以说是运行时分配的内存),读取速度慢，但数据灵活性高。
                System.out.println((int)(Math.randow()*10));//生成随机数字，0～10
                Randow rand=new Randow();
                int i=rand.nextInt(10);//随机生成0～10的数字
                System.out.println(i);
    }
}
```

import java.util.Randow;//导入随机数字的包
```
public class test{
    public static void main(String args[]){
            Randow rand=new Randow();//声明随机数字的对象
            int []numb=new int [rand.nextInt(10)];//rand.nextInt(10)这句话的意思是随机生成一个0～10的数字作为数组的长度
            for(int i=0;i<numb.length;i++){//为数组赋值。从0～100来选择每次的赋值的数值
                numb[i]=rand.nextInt(100);
            }
            for(int a : numb){//打印数组里的元素
            System.out.println(a);
            }
    }
}
```

**在c++中的指针，在java是叫做引用数据类型，相当与c++中的地址指针** 
```
public class test{
    public static void main(String args[]){
    Randow rand=new Randow();//声明随机数字的对象
    int []a=new int[rand.nextInt(10)];//定义数组长度
    int []b=a;//把数组a赋值给数组b
    for(int i=0;i<a.length;i++){//为数组a赋值
            a[i]=rand.nextInt(100);
            System.out.println(a[i]);
            System.out.println(b[i]);
    }
    }
}
```

`上面程序的结果每次都是不要的，但值得注意的是输出的结果，肯定不会让你们失望的，因为数组b里面的元素是和数组a的元素是一样的。其实，上面最重要的一点就是数组b=数组a，它的等于是连着后面的a数组的赋值。` 

---

```
public class test{
    public static void main(String args[]){
            Randow rand=new Randow();
            int [][]numb=new int[3][1];//声明数组numb和给数组长度
            for(int i=0;i<numb.length;i++){//给数组赋值并输出数组里的元素
                for(int j=0;j<numb[i].length;j++){
                        numb[i][j]=rand.nextInt(10);
                        System.out.println(numb[i][j]);
                }
            }
    }
}
```

`一样的，上面的数组每运行一次程序的结果都是不一样的。` 

---
```
public class test{
    public static void main(String args){
            int []numb=new int[]{10,23,41,6,11};//声明一个数组，并赋初值
            int a=Randow rand=new Randow(3)+1;//生成随机数字，范围是1～4
            for(int i=0;i<a;i++){//把随机数字的大小作为条件,并从一开始交换位置
                int temp=numb[i];
                numb[i]=numb[i+1];
                numb[i+1]=temp;
            }
            for(int b:numb){//输出数组里的元素
            System.out.println(b);
            }

    }
}
```

`上面程序实现的是乱序，就是每次输出的结果都是不一样的。` 

---

# 对象
**类描述了对象的属性和对象的方法，类是对象的模板，更可以说，对象是类的实例，是一个实实在在存在的个体。所以说，面向对象的程序重要的是类的设计而不是对象的设计。** 
`类的声明格式:` 
- [ ] [标识符] class 类的名称
{
        //类的属性
        //类的方法
}
`类的标识符:` 
- [ ] 默认的(default):这个类只能被这个类的对象和同一个包中的其它的类访问，即使是其它包里的这个类的子类都不能被访问，它只认同一包里的类。

- [ ] 私有(private):如果一个方法或者属性被定义为私有的，那么只能在本类里访问它。

- [ ] 公有(public):如果一个方法或属性被定义为公有的，那么它不仅能跨类的对象所调用，还能在其它包中被访问。

- [ ] 保护(protected):如果一个方法或属性被定义为保护的，那么它能被本类的方法所访问，也能被子类所访问，即使子类在其它包里。

![java访问机制](Java/java3.png) 

```
public class Test{
    public static void main (String args[]){
            System.out.println("------"创建对象"-------");
            new Apple();//匿名对象
    }
}
class Apple{
        static String a="string-a";
        Static String b;
        String c="string-c";
        Strint d;
        Static{//static 属于静态代码块，最先运行的是这段代码块，而不是类的构造函数先
                printstatic("before static");
                b="string-b";
                printstatic("after static");
        }
        static void printstatic(String name){//这里要加静态的关键字，因为调用是静态来的所以这里也要有静态的关键字来表明这里是静态，不然是会报错的。
                System.out.println("------"+name+"-------");
                System.out.println("a="+a);
                System.out.println("b="+b);
        }
        Apple(){
            print("before class");
            d="string-d";
            print("after class");
        }
        void print(){
                System.out.println("------"+name+"-------");
                System.out.println("a="+a);
                System.out.println("b="+b);
                System.out.println("c="+c);
                System.out.println("d="+d);

        }
}
```
![运行结果](Java/java4.png) 

```
上面的对象是经过匿名对象来实例化的，也就是没有给new的对象一个堆内存，一旦这句语句实现完，计算机会自动回收这个内存，将不再存在程序里，这也是java的垃圾回收机制(BC)，这也是为我们考虑的，不知道你有没有发现，上面的几个程序我都是用new来给类分配的对象，但我不但没有在类中写析构函数，也没有在main函数里delete对象的实例化。因为这一切都是java的BC机制帮我们做了。

```
public class Test{

    public static void main(String args[]){
            String name=new String ("java");
            String _name=new String ("java");
            String hua=_name;
            if(name==_name){
            System.out.println("地址相同");
            }else{
            System.out.println("地址不同");
            }
            if(name.equals(_name)){
            System.out.println("内容相同");
            }else{
            System.out.println("内容不同");
            }
}
运行结果:
地址不同
内容相同
```

上面的程序分别实现了字符串地址(==)和字符串内容(equals方法)的比较，第一个变量和第二个变量的是经过new来分配的栈内存的地址，所以输出的是地址不相同,而最后一个的是进行的内容比较，因为初始化的原因，这里也是输出的内容相同。


构造方法的注意事项
- [ ] 构造方法的名称与类的名称是一样的
- [ ] 构造方法也是和普通方法一样的，可以被重载，但构造方法的调用是通过在创建类的对象的时候自动调用的，这是与普通方法的调用是不一样的
- [ ] 构造方法是没有返回值的
- [ ] 构造方法是不能被static和final修饰的
- [ ] 构造方法是不能被继承的，如果子类要使用父类的构造方法只能使用关键字(super)来进行调用

```
public Test{

    private String name;
    Test(){
    System.out.println("类的无参构造方法的调用");
    }
    Test(String _name){
        this->name=_name;
        System.out.println("类的有参构造方法的调用");
    }
    public static void main(String args[]){
            new Test();//这是匿名调用类的构造方法
            Test test=new Test();//这和上面是等价的
            Test t1=new Test("小明");
    }
}

上面的程序做的只是简单的演示类的构造方法的重载。

```
public Test{
    public static void main(String args[]){
    Apple apple;
    apple=Apple.V();
    System.out.println("姓名:"+apple.name);
    }
}
class Apple{
        String name;
        private Apple (){
        name="hello";
        }
        private static final Apple APPLE=new Apple();
        public static V(){
        return APPLE;
        }
}
```

上面的程序的重要性是:当你不想一个类被频繁调用的是时候，可以通过对类的构造方法的私有化来实现




# 代码块
- [ ] 普通代码块(就是普通的放在Main方法里面的代码块)
- [ ] 构造代码块(放在类里面，比构造方法更先一步执行的代码块)
- [ ] 静态代码块(比构造代码块更快一步，如果和Main方法是放在同一个类的话，那它比Main方法更快一步执行)
- [ ] 同步代码块

> 普通代码块

```
public class Test{
        public static void main(String args[]){
        {int x=10;//普通代码块
        System.out.println("x");
        }//如果不要这个代码块，程序将会报错，因为在一个方法里，不能有同名的变量名
        int x=100;
        System.out.println("x");
}
}
```

```
运行结果为:
10
100
```

>> 构造代码块

```
public class Test{
    public static void main(String args[]){
           Peron p=new peron(); 
           Peron p1=new Peron("笑话");
    }
}
class Peron{
    private int x;
    String name;
    {
    System.out.println("构造代码块的调用");//这是构造代码块
    x=10;
    }
    Peron(){
        System.out.println("类的无参构造方法的调用\t"+x);
    }
    Peron(String _name){
    this->name=_name;
    System.out.println("类的有参构造方法的调用\t"+x);
    }
}

```
```
程序的运行结果为:
    构造代码块的调用
    类的无参构造方法的调用  10
    构造代码块的调用
    类的有参构造方法的调用  10
```

上面类中是有一块属于构造代码块，而它的速度比构造方法的调用都还快，以前我们只知道对于类来说，构造方法是第一个调用的，因为在我们声明类的对象的时候就是通过类的构造方法来实现的，但现在不一样的是，你只要在类中加个中括号({}),里面的代码实现比类的构造方法都还要快被实现，这使得我们的代码更简化一步。比如，就像上面一样，给一个成员变量复制，而不是通过它的构造方法来实现，你只需要定义一个变量，然后再加个({}),就能实现对成员变量的复制，速度还比类的构造方法快一布。

**由此我们可以知道，类的代码块中的初始化是一个类的所有构造方法都共有的“交集”部分，具有个性化的初始化还是要放在各自的构造方法里** 


>>> 静态代码块

```
public class Test{
    static {
    System.out.println("静态方法的调用");
    }
    {
    System.out.println("构造代码块的调用");
    }
    Test(){
    System.out.println("构造方法的调用");
    }
    public static void main(String args[]){
            System.out.println("创建第1个对象");
            new Test();
            System.out.println("创建第1个对象");
            new Test();
            System.out.println("创建第1个对象");
            new Test();
    }
}

```
```
程序的运行结果为:
    静态代码块的调用
    创建第1个对象
    构造代码块的调用
    构造方法的调用
    创建第2个对象
    构造代码块的调用
    构造方法的调用
    创建第3个对象
    构造代码块的调用
    构造方法的调用

```


**从上面的案例可以看出来，在执行时机上，静态代码块是在类加载的时候就会执行的，因为早于类的构造代码块和类的构造方法。当一个静态代码块和Main方法在同一个类中，Main方法的调用也是在静态代码块的后面的。静态代码块的执行级别是最高的。**    



```
public class Test{
    public static int [] show(int []numb){
        numb[0]=10;
        numb[1]=12;
        numb[2]=13;
        return numb;
    }
    public static void show1(int []numb){
        for(int i:numb){
        System.out.print(i+"\t");
        }
    }
        public static void main(String args[]){
            int [] numb =new int{1,2,3,4,5};
            for(int i:numb){
            System.out.print(i+"\t");
            }
            System.out.println();
            System.out.println("--------------");
            show(numb);
            Show1(numb);

    }
}
```

```
    程序的运行结果为:
    1 2 3 4 5 
    10 11 12 4 5
```

`上面的程序只是简单的利用java的特性用新的方式来打印数组，只需要一个变量来操作数组对象就行了，比我们之前在c++中的方式简便多了，也是代码的量也减少了，这无疑是一件好事，还利用了引用数据类型来实现对数组的操作，更加利用了静态方法来进行对数组里的元素更改。` 


```
import java.util.*//导入sort包
public class Test{
    public static void main(String args[]){
    int []numb={10,2,46,33,5};
    Arrays.sort(numb);//进行数组的排序
    System.out.println("排序后:");
    for(int i:numb){
    System.out.print(i+"\t");
    }
        
    }
}

```  


```
程序的运行结果为:
排序后:
2 5 10 33 46
```

# 枚举(enum)
`enum A{红色，黄色，白色}枚举是作为类来被调用的，在定义的同时是连着对象的构造方法一起被调用的` 
```
enum Cloro{红色，黄色，白色}//是枚举的关键字,定义了一个枚举并初始化了
public class Test{
    public static void main(String args[]){
            //java中的枚举其实是一个类来的，在这个类里面还有很多不一样的方法，其作用都是不一样的。
            Cloro []cloro=Cloro.values();//Cloro.values()是类的静态方法来的，但是以字符串的形式来的，所以在前面要定义一个同类型的数组来接收,方法是自动生成的
            for(Cloro i:cloro){
            System.out.println(i);
            }
            Cloro c=Cloro.valueof(Cloro.class,"白色");//以指定的颜色来赋给对象,这里的参数有点不一样的就是，参数是类的类型,方法是自动生成的
            System.out.println(c);
            
    }
}
```

```
运行结果:
红色
黄色
白色
白色
```

枚举的注意事项
- [ ] 如果把枚举的标识符定义为public的话要放在独立的文件里面而不能和main方法放在同一个文件，如果标识符是默认的话就可以放在同一个文件里
- [ ] 使用enum来定义枚举的时候，默认会继承于java.lang.Enum类。默认会用final来修饰，因此无法派生子类。
- [ ] 使用enum来定义的时候，初始化也要和定义一起,如果没有把赋值放在同一行，而这个enum将无法被实例法。
- [ ] 所以使用enum来定义枚举的时候都会默认生成values方法，该方法可以方便遍历所有枚举值，而在枚举中还是有其它的自动生成的方法来给我们使用。

**enum(枚举)用关键字定义的时候相当于定义了一个类，而这个类继承于Enum类。而在Enum类中的所有方法都是保护类型的，因此这些方法都可以在声明了enum对象中被使用。** 

```
enum A{红色，紫色，白色}
public class Test{
    public static void main(String args[]){
            A []a=A.valuse();//把枚举中的元素都放在对应类型的数组中
            for(A i:a){
            System.out.println(i.name+i.ordinal());输出的是数组中的元素和数组的下标
            }
    }
}
```

```
运行结果:
红色0
紫色1
白色3
```

`在枚举中的下表要是没有给定提定的数值，计算机就会自动给它一个下标，而下标的值是以数组的形式来赋值的。` 


`EnumMap是Map接口的子类，也就是说Enummap是继承于类Map的` 

```
import java.util.Map;//导包
import java.util.EnumMap;//导包
enum Color{红色，黄色，绿色}
public class Test{
    public static void main(String args[]){
        EnumMap<Color,String>emap=new EnumMap<Color,String>(Color.class);//映射<><KeyType,nameType>,更重要的是EnumMap的构造方法的参数不能为空，需要指定一个枚举类
        emap.put(Color.红色,"RED");//把映射的对象和值都写进去
        emap.put(Color.黄色,"YELLOW");
        emap.put(Color.绿色,"BLUE");
        for(Map.Entry<Color,String>me:emap.entrySet()){//把映射的键和值都打印出来,其中的两个方法是Map中的静态方法，EnumMap作为Map的子类所以能调用其中的方法。
        System.out.println(me.getKey()+me.getValue());
        }
    }
}
```

```
运行结果:
红色RED
黄色YELLOW
绿色BLUE
```

上面的打印用的是新的打印方法，而EnumMap的类型是Map来的，所以它要Map.来点出它的方法来进行打印,Key是不允许重复的，而它的值却允许重复，EnumSet是一个集合来的

```
import java.util.EnumSet;//导包
import java.util.Iterator;//导包
enum Color{红色，绿色，紫色}
public class Test{
    public static void main(String args[]){
        EnumSet<Color> set=EnumSet.allof(Color.class);//声明集合<EnumTepy>并把对应类型的枚举类放在集合中,allof是集合EnumSet中的静态方法，用来把参数中的枚举类放在集合中作为集合的元素
        Iterator <Color>iter=set.iterator();//声明迭代器并把集合放在迭代器中
        while(iter.hasNext()){//参数是确认迭代器中的元素是否为空,为空的时候返回false
        System.out.println(iter.Next());//打印迭代器中的元素
        }
        EnumSet <Color>aset=EnumSet.noneof(Color.class);//表示作为空的集合
    }
    Iterator iterator=aset.iterator();
    while(iterator.hasNext()){
    System.out.println(iterator.Next());//这里是打印不出来的，所以下面的结果为空
    }
}
```


```
运行结果:
红色
绿色
紫色
```


```
enum Color{
    RED("红色",3),BLUE("蓝色",4),YELLOW("黄色",5);//定义枚举并指定颜色和下标，是以私有构造方法来显示调用枚举类的属性，(也就是说成员)
    private String Name;//元素的名字
    private int Indext;//元素的下标
    private Color(String name,int indexc){//枚举类的构造方法是私有化的,所有的枚举对象都必须显示调用此构造方法。
            this->Name=name;
            this->Indext=indexc;
    }
    public static void setname(int indexc,String name){
        for(Color c:Color.values()){
            if(c.Indexc==indexc){
            c.Name=name;
            }
        }
    }
    public static void setindexc(String name,int indexc){
        for(Color c:Color.values()){
            if(c.Name==name){
            c.Indexc=indexc;
            }
        }
    }
    public String getname(String name){
    return name;
    }
    public int getindexc(int intexc){
    return intexc;
    }


}
public class Test{
    public static void main(String args[]){
        System.out.println(Color.RED.getname());//RED是枚举类型的Color的枚举实例。这些枚举实例是公有的静态对象(进一步说，它们可以视为枚举类的属性成员)
        System.out.println(Color.RED.getindexc());
        System.out.println(Color.BLUE.getname());
        System.out.println(Color.BLUE.getindexc());
        System.out.println(Color.YELLOW.getname());
        System.out.println(Color.YELLOW.getindexc());
        System.out.println("自定义元素");
        Color.setname(3,"白色");//通过属性下标来改变属性的名字
        System.out.println(Color.RED.getname());
        System.out.println(Color.RED.getindexc());
        Color.setindexc("黄色",7);//通过属性的名字来改变属性的下标
        System.out.println(Color.YELLOW.getname());
        System.out.println(Color.YELLOW.getindexc());
    }
}
```

```
运行结果:
红色
3
蓝色
4
黄色
5
白色
3
黄色
7

```

在上面的程序中都是通过私有的构造方法来显示调用成员属性的，在上面属性其实是RED,BLUE,YELLOW,只不过我在这里都没对它操作，在这里比较容易混淆的是，根本不明白谁才是枚举的成员属性，你也可以通过上面的Values()(是枚举类自动生成的用来遍历枚举属性的方法),其实在上面我也用到了这个方法来对成员属性的名字和下标来进行改变它们对应的值。在最开始的时候定义的枚举的属性其实是在调用私有构造方法来实现实例化。只要把这个搞懂了，其实那些改变成员属性的方法都是很简单理解的。


```
enum Color{
    红色
    {
        public String show(){
            return "RED";
        }
    },
    蓝色
    {
        public String show(){
            return "BLUE";
        }
    },
    黄色
    {
        public String show(){
            return "YELLOW";
        }
    };
    public abstract String show();//把上面的show方法定义为抽象方法(abstract)抽象关键字

}
public class Test{
    public static void main(String args[]){
        
        for(Color c:Color.values){
        System.out.println(c.ordinal+"\t"+c.name()+"----"+c.show());
        }
    }
}
```

```
运行结果:
0  红色----RED
1  蓝色----BLUE
2  黄色----YELLOW
```

抽象方法关键字(abstract)，修饰没有主体的方法，在这里需要在枚举对象中一一单独实现，否则报


```
enum Weekday {Sun,Mon,Tue}
public class Test{
    public static void main(String args[]){
            Weekday w=Weekday.Sun;
            switch(w){
                case Mon:
                System.out.println(Do Monday work);
                case Sun:
                System.out.println(Do Sunday work);
            }
    }
}
```

```
运行结果:
Do Sunday work
```

这里是当你定义的是枚举类中的哪个元素的对象的时候，通过switch来进行选择，你输出的语句是你在switch写的语句。


# 类
|控制范围|private|default|protected|public|
|----|----|----|----|----|
|类|只能内部类允许私有，只能在当前类被访问|可以被当前包中的所有类访问|只有在内部类可以被设为保护权限,相同包中的类和其子类可以被访问|可以被所有类访问|
|属性|只能被当前类访问|可以被相同包中的类访问|可以被当前包中的所有类访问和当前类的子类访问|可以被所有类访问|
|方法|只能被当前类访问|可以被相同包中的类访问|可以被相同包中的类访问和当前类的子类访问|可以被所有类访问|



`java中对于类来说有封装，继承，多态。` 

`java中类的成员变量的权限有私有，公有，保护，默认，在上面的表格中都给出了对应的权限范围，java类只有允许单继承不允许多继承，但允许多重继承，` 

```
import java.util.ArrayList;
public class Test{
    public static void main(String args[]){
    System.out.println("集合大小");
    Apple a=new Apple();//调用类的构造方法来实现对集合的操作
    ArrayList <Interger>array=a.getarray();//声明一个集合来对类中的公有方法中的返回值进行赋值给这个集合,很重要的是，在这里传的是引用而不是数据的副本。
    System.out.println(array.size());//打印集合的大小
    array.add(8);//对集合的引用进行加值的操作
    Arrjy <Interger>a1=a.getarray();又重新定义一个集合来对调用的类的公有方法的返回值进行赋值
    System.out.println(a1.size());//打印集合的大小
    System.out.println("集合元素");
    for(Interger i:a1){
    System.out.println(i);
    }

    }
}
class Apple{
        private ArrayList<Interger>array=new ArrayList<Interger>();//声明一个私有集合作为类的成员变量
        Apple(){//构造方法,对集合进行初始化
        array.add(1);
        array.add(1);
        array.add(1);
        }
        ArrayList<Interger>getarray(){//返回集合
        return array;
        }

}
```

```
运行结果:
集合大小
3
4
集合元素
1
1
1
8
```

**其实在上面的程序中最难懂的是，在main方法里的集合的操作是引用的操作而不是简单的副本操作，在java中，除了基本的数据类型，其它都是引用类型,其中类也是引用类型** 


关于继承的限制
- [ ] java中继承允许多继承，但也许多重继承
- [ ] 从父类继承的私有成员不能被子类直接使用，要通过方法来间接调用
- [ ] 子类在进行对象实例化的时候，先调用父类的构造方法对父类的成员变量进行赋值，然后在调用子类的构造方法，其作用是一样的。

```
public class Test{
    public static void mai(String args[]){
        
    }
}
final class A{
    final void show(){
    System.out.println("如果这个方法在不想被子类覆写，可以在方法前面加上这个修饰符来确定不被子类覆写");
    }

}
//class B extends A{}//是错误的,所以注释掉
```

上面的程序是不行的，因为父类的修饰符是final，它是不能被继承的

```
public class Test{
    public static void main(String args[]){
        A a=new B();
        a.show();
    }
}
class A {
    A(){
    System.out.println("父类的构造方法")
    }
    void show(){
        System.out.println("走");
    }
}
class B extends A{
    B(){
    System.out.println("子类的构造方法
    }
    void show(){
        System.out.println("飞");
    }
}
class C extends A{
    C(){
        System.out.println("子类的构造方法
}
    void show(){
        System.out.println("跑");
    }
}
```

```
运行结果:
父类的构造方法
子类的构造方法
飞
```

上面的程序主要是实现多态的重要性，还有就是继承的小细节，继承是先调用父类的构造方法之后再调用子类的构造方法。在刚开始的时候就写过了在上面是先声明一个父类对象来进行对子类的实例化，然后在调用子类中覆写父类成员方法的方法，其实你也完全可以通过子类的对象来对子类进行实例化，在这里主要是实现类的多态。


方法重载与覆写的区别
- [ ] 重载是在本类中实现的，而覆写主要是在子类中重写父类的方法
- [ ] 重载要求方法的参数个数和参数类型的顺序和参数的类型和方法名字，其中的任意一个不同。而覆写是方法名称和参数个数和类型与父类是一致的就行了


`this&&super` 
----
```
public class Test{
    public static void main(String args[]){
            B b=new B();
            b.show();
    }
}
class A{
        String name;
        void show(){
        this->name="java";
        }
}
class B extends A{
    String name;
    void show(){
        this->name="shanghai";
        super.show();
        System.out.println(name+"\t"+super.name);
    }
}

```

```
运行结果:
shanghai  java

```

|区别|this|super|
|----|----|-----|
|查找范围|先从本类中找到属性或方法，本类找不到再去父类寻找|不查询父类的属性或方法，直接从子类调用父类的指定属性和方法|
|调用构造|this使用的是本类的构造|super先调用的是父类的构造方法，然后在调用子类的构造方法|
|特殊|表示当前的对象|可以看作是父类的引用对象|
|关系|两者的关系是属于二选一的关系，不能被同时调用|
---
抽象类
----

```
public class Test{
        public static void main(String args[]){
        A a=new B("小艾",11);
        a.show();
        A a1=new C("笑话",12);
        a1.show();
    }
}
abstract class A{
        public abstract void show();
}
class B extends A{
        String name;
        int age;
        B(String _name,int _age){
        }
        public void show(){
        System.out.println("学生\t"+name+"\t"+age);
        }
}
class C extends B{
    C(String _name,int _age){
            super(_name,_age);
    }
    public show(){
    System.out.println("工人\t"+name+"\t"+age);
    }
}
```

```
运行结果:
学生  小艾  11
工人  笑话  12
```

上面的类A是一个抽象类来的，抽象类是不能被实例化的，顾名思义，抽象类是没有实现的方法的，在上面的父类中只有定义成员方法为抽象方法的的一个定义，没有实现的行为，抽象类的实现一般是在子类中一一实现的，这也得于抽象类的特性，抽象类是不能被实例化的，这样做会报错的，一般的抽象类都是有子类的，子类的重要作用之一是实现父类中的抽象方法，这是很重要的，还有就是，定义在父类的全部抽象方法在子类中都要重写这些抽象方法，不然会报错，记住是全部都要重写。


# 接口(interface)
`接口是java所提供的另外一种重要的技术，是一种特殊的类，它的结构和抽象类很相似。接口里的数据成必须初始化，数据成员均为常量，常见的是全局变量。` 
`为了避免在接口中添加新的方法后要修改所有的实现类，允许定义默认方法` 

使用接口的原则
- [ ] 接口必须有子类，子类依靠(关键字)implements来实现多个接口
- [ ] 接口的子类必须重写接口中的所有抽象方法
- [ ] 接口可以利用对象的多态性，利用子类的对象进行实例化
- [ ] 接口和一般的类是一样的，具有成员变量和成员方法，但数据成员必须进行初始化，而初始化的值是不能被修改的，相当与是常量，方法也必须是抽象的或者是(default)，所以在接口中这两个特性是可以忽略的，因为在接口中不管是成员方法或者是成员变量都是特性都是肯定了的。


```
public class Test{
    public static void main(String args[]){
            
            B b=new B();
            b.show();
            b.print();
        System.out.println(A.name);
        //System.out.println(b.name);//不能通过类的实现来访问静态成员
    }
}
interface A{
        public static String name="hello";
        public void show();
        default void print(){
        System.out.println("你好");
        }
}
class B implements A{
    //name="HELLO";//这个是错误的
    public void show(){
        System.out.println(name);
    }
}

```

```
运行结果:
hello
你好
hello
```

上面的程序只是简单的介绍接口的基本定义的格式，其中有成员变量和成员方法，而其中的成员变量是全局类型的(还必须给初始化值)，成员方法分两种，一种是抽象方法(在子类是实现的方法，在接口只是声明而已)，另外是其它类型的成员方法


**在这里在强调一次，接口与抽象类唯一不同的就是子类，对于接口来说可以实现多个接口，但抽象类是不能多继承的** 

```
public class Test{
    public static void main(String args[]){
        C c=new C();
        c.show();
    }
}
interface A{
    default void show(){
    System.out.println("A接口的默认方法");
    }
}
interface B{
    default void show(){
    System.out.println("B接口的默认方法");
    }
}
class c implements A , B{}
```

上面的程序是错误的，因为在接口中的默认方法中如果有同名的方法，你在调用方法的同时，编译器会不知道你要调用的到底是哪一个方法，这就产生了所谓的二义性，一般来说在接口中一定不要有同名的变量,还有就是上面的接口是没有抽象类型的方法，所以在子类中是空的


`在前面说过，接口是允许多继承的，接口中对于抽象类和接口的继承是先继承后实现` 


```
public class Test{
    public static void main(String args[]){
        F f=new F();
        A a=f;//声明一个接口对象来指向子类，主要是在调用方法的时候让你清晰的知道在那个接口中调用的是那个方法。你也可以不写，直接用子类的实例化对象来调用
        B b=f;
        C c=f;
        D d=f;
        a.show();
        b.prin();
        c.print();
        c.xiao();
        d.printd();
        d.xi();
    }
}
interface A{
        public static String name="小新";
        public void show();
}
interface B{
    public void prin();
}
interface  C extends A , B{//接口继承多个接口
    public void print();
    default void xiao(){
    System.out.println(name+"\t多接口继承");
    }
}
abstract class D implements A,B{//抽象类继承多个接口
    abstract public void printd();
    void xi(){
    System.out.println(name+"\t抽象类继承");
    }
}
class F extends D implements C{
    public void show(){
    System.out.println("你好");
    }
    public void prin(){
    System.out.println("hello,world");
    }
    public void print(){
    System.out.println("一个接口继承多个接口"+name);
    }
    public void printd(){
    System.out.println("抽象类继承多个接口");
    }
}
```

```



运行结果:
你好
hello,world
一个接口继承多个接口
小新 多接口继承
抽象类继承多个接口
小新 抽象类继承
```

在上面的程序中我们可以知道，对于接口的继承，一个接口可以继承多个接口(extends)来继承，继承的同时不用进行对继承的接口进行实现。抽象类继承多个接口(implements),继承的同时一样不要进行对已继承的接口的方法实现，但子类一定要对继承的接口和抽象类中的方法进行实现,还有就是，不管是多接口继承还是抽象类继承，都是基于继承的特性来实现继承的，都会继承父接口的成员变量。对于接口的成员变量一定要在声明的同时就进行初始化。


接口的作用--制定标准
`接口是标准，所谓的标准，指的是各方共同遵守的一个原则。只有操作标准统一了，所有的参与者才可以按照统一的规则操作` 

```
public class Test{
    public static void main(String args[]){
        Computer c=new Computer();
        c.show(new B);//拿子类的引用来作为参数调用父接口中的方法
        c.show(new C);//拿子类的引用来作为参数调用父接口中的方法

    }
}
interface USB{
        public void work();
}
class B implements USB{
    public void work(){
        System.out.println("USB在工作");
    }
}
class C implements USB{
    public void work(){
        System.out.println("USB在打印机中工作");
    }
}
class Computer{
    public void show(USB usb){//父接口作为方法的参数
        usb.work();//调用类中的方法
    }
}
```

```
运行结果:
USB在工作
USB在打印机中工作
```

上面展现的是接口作用--制定标准，利用接口USB来制定工作的标准，通过继承来实现接口中的方法，最后通过电脑类中的方法来调用在子类的实现

接口--工厂的设计
```
public class Test{
    public static void main(String args[]){
    A a=F.getname("apple");
        
    }
}
interface A{
        public void eat();
}
class apple implements A{
    public void eat(){
        System.out.println("吃苹果");
    }
}
class oright implements A{
    public void eat(){
    System.out.println("吃橙子");
    }
}
class F{
    public static A getname(String name){
        if("apple".equals(name)){
        return new apple();
        }
        if("oright".equals(name)){
        return new oright();
        }
        return null;
    }
}
```

```
运行结果:
吃苹果
```

此时的程序，在客户端没有和具体的子类耦合在一起，这样一来，如果再有更多的A接口子类出现，只需要修改F类即可，即:所有的接口对象都通过F类取得，在程序员自己开发的代码中，只要是遇见要取得接口对象实例的操作，都应该使用工厂设计模式。
