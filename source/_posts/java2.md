---
title: java2
date: 2019-12-16 15:52:18
tags:
---

Write Onec,Run EveryWhere
<!--more-->
                                                        Java
# I/O
当程序需要读取数据时，就会开启一个通向数据源的流，这个数据源可以是文件，内存，也可以是网络连接。而当程序需要写入数据时，也会开启一个通向目的地的流，这时，数据就可以想象成为管道中“按需流动的水”。流作为操作各种物理设备提供了一致的接口，通过打开将流关联到文件，通过关闭流操作和文件解除关联。


```
public class Test{
    public static void main(String [] args){
            File me=new File("Desktop/test.txt");
            if(me.exists()){//判断是否有这个文件
                me.delete();//删除这个文件
            }else{
                try{
                me.createNewFile();//如果没有这个文件则创建
                }catch(Excepion e){
                    System.out.println(e.getMessage());
                }
            }
            System.out.println(me.getName());//获得文件的名字
            System.out.println(me.getPath());//获得文件的相对路径
            System.out.println(me.getPaernt());//获得文件的目录
            System.out.println(me.getAbsolutePath());//获得文件的绝对路径
            System.out.println(me.canWrite?"可以写":"不能写");//判断文件是否能写
    }
}
```

```
运行结果:
没有那个文件或目录
test.txt
Desktop/test.txt
Desktop
/home/evanshady/Desktop/test.txt
不能写


```

上面的程序是利用File类的一些操作，File类中还有其它的方法，在这里就不一一实现了，File类只能对文件的一些小操作(创建，删除，更名)，对文件的读写操作是不能的。

![File类](java2/java.jpg) 
![File类](java2/java1.jpg) 

**在java中对于文件的操作有两大流，字节流和字符流。一般来说音频，视频，图像，不管是写入或者读取我们需要使用字节流来比较方便，相当与文本而言就是字符流比较合适。对于文件的写操作(Outputstream),读操作(Inputstream)** 

```
public class Test{
    public static void main(String [] args){
            File file=new File("/home/evanshady/Test/test.txt");//文件路径
            Outputstream out=null;//文件的写入流
            try{
                out=FileOutputStream(file);//将文件流和指定的文件连在一起
            }catch(FileNotoutputstream e){
                file.createNewFile();//利用错误机制来获得信息，如果没有这个文件，将会在文件的相对路径创建文件
                e.printStackTrace();//打印错误的信息
            }
            byte []a="hello,world!".getBytes();//将要写入的字符，转换成字节
            try{
            out.write(a);//写入字节,这是因为这里的write方法指定写入的要是字节类型的数据
            }catch(IOException e){//利用错误机制，如果没有写入的字符将会打印错误信息
            e.printStackTrace();
            }
            try{
            out.close();//关闭文件流
            }catch(IOException e){//利用错误的机制，如果文件没有被关闭将会打印错误的信息
            e.printStackTrace();
            }
            Inputstream in=null;//定义读文件流
            try{
            in=new FileInputstream(file);//将读文件流和指定的文件连接在一起
            }catch(FileNotoutputstream e){//利用错误机制,如果没有这个文件，将会打印错误的信息
            e.printStackTrace();
            }
            byte [] a1=new byte[1024];//定义一个字节数组
            int i=0;//定义一个变量
            try{
            i=in.read(a1);//读取文件里的内容
            }catch (IOException e) {
                e.printStackTrace();//利用错误机制，如果读取文件内容失败，将会打印错误的信息
            }
            try{
            in.close();//关闭文件流
            }catch(IOException e){
            e.printStackTrace();//利用错误的机制，如果文件没有被关闭将会打印错误的信息
            }
            System.out.println(new String(a1,0,i););//利用String来将读取到的内容打印出来

    }
}
```

```
运行结果:
hello,world!
```


上面的程序是利用File类和OutputStream和Inputstream三个类来实现的文件操作，其细致的操作说明在上面已经有详细的注释了。上面的程序值得注意的是千万不要忘记了将文件的写入流||输出流和指定的文件连接在一起，不然你拿什么来操作，还有就是关于连接以后，你可以在后面加个true来看看指定文件的内容是什么样的。

> 字符串的写入


```
public class Test{
    public static void main(String [] args){
            File me=new File("/home/evanshady/Test/a.txt");//指定的文件
            Writer writer=null;//定义文件的写入流
            try{
            writer=FileWriter(me);//将文件的写入流和指定的文件连接
            }catch (FileNotoutputstream e){
            me.createNewFile();//利用错误机制来获得信息，如果没有这个文件，将会在文件的相对路径创建文件
            e.printStackTrace();
            }
            String a="hello";//定义要写入的字符串
            try{
            writer.write(a);//利用错误机制，如果没有写入的字符将会打印错误信息 
            }catch (IOException e){
            e.printStackTrace();
            }
            try{
            writer.close();//利用错误的机制，如果文件没有被关闭将会打印错误的信息
            }catch(IOException e){
                e.printStackTrace();
            }
            int x=0;定义一个变量，初始化为0
            x+=me.length();//将指定的文件的大小赋值给变量
            char [] b=new char[x];//定义一个数组,数组的大小正好接住从文件读取的内容
            int i=0;//定义一个变量，来配合读文件的方法
            Reader reader=new Reader(me);
            try{
                i=reader.read(b);
            }catch(IOException e){
            e.printStackTrace();
            }
            try{
            reader.close();
            }catch(IOException e){
            e.printStackTrace();
            }
            System.out.println(new String(b,0,i));//将读取的内容打印出来
    }
}
```

```
运行结果:
hello
```

writer类和reader类是Outputstream的子类，此类是字节流和字符流的转换类，而字符流和字节流不同的是，字符流多了一个缓冲区，而字节是没有缓冲区的，直接对文件实时操作。

```
public class Test{
    public static void main(String [] args){
            BufferedReaber reader=new BufferedReaber(new Inputstream(System.in));//定义一个缓冲流连接着键盘输入流
            String str=null;//定义一个字符串
            System.out.println("请输入一个数字");
            while(true){//利用循环
                try{//错误机制
                str=reader.readLine();//字符串来接住输入的那个数字
                }catch (IOException e){//通过流来检测错误信息
                    e.printStackTrace();
                }
                int i;//定义一个变量
                try{
                    i=Integer.parseInt(str);//将输入的字符串转换成整形，
                    i++;//更改变量的值
                    System.out.println("数字更改后:"+i);//打印
                    break;//循环结束
                }catch(Excepion e){
                    System.out.println("数字不对,请重新输入");//利用错误来检测输入的是否是整数
                }
            }
    }
}
```

```
运行结果:
请重新输入一个数字
10
数字更改后：11
```


```
public class Test{
    public static void main(String [] args){
        File me=new File("/home/evanshady/Desktop/test.txt");
        Write writer=new FileWriter(me);
        BufferedWriter buff=new BufferedWriter(writer);
        string s="hello,world1";
        buff.writer(s);
        buff.close();
        Reader reader=new FIleReader(me);
        BufferedReaber buff1=new BufferedReaber(reader);
        String s1=buff1.readLine();
        System.out.println(s1);
    }
}

```


```
运行结果:
hello，world1
```

缓冲流(BufferedWriter)是Writer的子类，可以使用writer的方法，而BufferedReader是Reader的子类，同样是可以使用reader的方法


**缓冲流的使用，相比没有使用缓冲流的使用的程序而言是比较快的，不管是读还是写文件的操作，都是比没有使用缓冲流的程序快** 

# 管道流
**它具有将一个程序的输出当作另外一个程序的输入功能。在java中，它的I/O系统是建立在数据流概念之上，也可以使用管道流进行线程之间的通信，在这个机制中，输入流和输出流必须要相连接，这样的通信有别于一般的共享数据缓冲区通信，其不需要一个共享的空间** 

管道流也分为字符流和字节流

```
public class Test{
    public static void main(String [] args){
            One one=new One();//创建线程对象
            Two two=new Two();
            PipOutputstream out=one.getout();
            PipInputStream in=two.getin();
            one.connect(two);//将输出发送到输入
            one.start();//启动线程
            two.start();
    }catch (IOException e){
    System.out.println(e.getMessage());
    }
}
class One extends Thread{//继承管道类
            private PipOutputstream out=new PipOutputstream();//定义一个写入的管道流的对象
            public PipOutputstream getout(){//返回管道类的对象
            return out;
            }
            public void run(){
                String str="hello,world";//要写入的字符串
                try{
                out.write(str.getByte());//通过字符串的转换方法，将要写入管道流的字符串转换成字节
                out.close();//管道关闭
                }catch(IOException e){
                System.out.println(e.getMessage());
                }
            }
}
class Two extends Thread{
            private  PipInputStream in =new PipInoutputStream();//定义一个读出的对象
            public PipInoutputStream getin(){//返回管道类对象
            return in;
            }
            public void run(){
                String str;
                byte []bytes=new byte[1024];
                try{
                int len=in.read(bytes);//通过读出的对象的读方法
                str=new String(bytes,0,len);
                System.out.println("得到的信息："+ str);
                in.close();
                }catch(IOException e){
                System.out.println(e.getMessage());
                }
            }

}
```

```
运行结果:
得到的信息：hello，world
```

上面的程序是通过两个类来集成Thread类来定义两个不一样的管道流(输入管道流&&输出管道流),分别重写Thread类中的run方法，使其各自做各自的事情(写入&&读出),然后再在main方法里通过自己重新定义的PipOutputstream对象&&PipInputstream对象来接住刚刚自己写的两个类的对象，然后就是将这两个对象连接在一起(connect),再就是给两个对象都开启线程，就是我们想要的的线程工作，最后不要忘记把写和读的过程中添加在错误机制里面来测试。


# 文件连接
```
public class Test{
    public static void main(String [] args){
            File file=new File("/home/evanshady/Test/a.txt");//声明第一个文件           
            Inputstream in=new FileInputstream(file);//让第一个文件和声明的文件流连接在一起
            File File1=new File("/home/evanshady/Test/test.txt");//同上
            Inputstream in1=new FileInputstream(file1);//同上
            SequenceInputstream s=new SequenceInputstream(in,in1);//定义一个合并文件的变量把文件流1和文件流2作为参数放在里面
            File file2=new File("/home/evanshady/Test/b.txt");//定义第三个文件
            int i;
            try{
                while((i=s.inread())!=-1{//通过合并的变量和read方法来读进内容
            Outputstream out=new FileOutputStream(file2);//第三个文件和文件流连接在一起
            out.write(i);//第三个文件的写方法
                        }
                        in.close();//关闭文件流
                        in1.close();//关闭文件流
                        s.close();//关闭文件流
                        out.close();//关闭文件流

            }
    }
}
```

```
运行结果:
hello.hello,world
```

上面的程序是让两个文件先通过SequenceInputstream来连接在一起，在这里的前提是前两个文件是要先确定有的，后面的通过文件流的读把要读进的内容通过第三个文件的write方法来写进去。


# 打印流(PrintWrite)
```
public class Test{
    public static void main(String args[]){
            PrintWrite out=new PrintWrite(System.out);//输出流
            out.write("hello");//把内容写在输出流
            out.close();//关闭输出流
            File file=new File("/home/evanshady/Test/a.txt");//文件
            PrintWrite out1=new PrintWrite(new FileWriter(file));//通过打印流来连接一个输出流
            out1.print("me");//把内容写在输出流里
            out1.close();//关闭输出流

    }
}
```

```
运行结果:
hello

```

上面的程序主要是通过输出流来把内容分别输出在屏幕上和写进文件里


# 读文件里的多行内容(BufferedReaber)

```
public class Test{
    public static void main(String []args){
            File file=new File(/home/evanshady/Test/a.txt);//文件的路径
            /*
            BufferedReaber in=new BufferedReaber(new FileReder(file));//将读文件的变量和文件流连接在一起
            Stream<String> lin=in.lines();//lines的方法调用的返回值是(字符流)类型
            lin.foreach((L)->System.out.println(L));//将上面的字符流对象通过foreach来将内容打印在屏幕上
            in.close();//将文件流关闭
            */
            List<String> list=Files.readAllLines(file.toPath());//通过列表来调用文件里的readAllLines方法来把文件.toPath来作为参数，将文件里的内容都放在列表里
            for(String a:list){
            System.out.println(a);
            }
    }
}

```
上面的程序主要是将文件中多行内容通过lines的方法放在流里，然后在通过foreach方法来将流里的内容打印在屏幕上。后面的方法也是一样的行为，只是方法的类型和方法的名字不一样而已，后面那个方法有点自闭的就是字体要utf-8在能读对，不然会有一些奇怪的字符出现


# 对象的写文件(Serializable)
```
public class Test{
    public static void main(String [] args){
        File file=new File("/home/evanshady/Test/a.txt");
        w(file);
        r(file);
    }
    public static w(File f){
        Outputstream out=new Outputstream(f);
        ObjectOutputstream ob=new ObjectOutputstream(out);
        ob.writeobject(new A("张三",1000));//直接将对象写入文件
        ob.close();
    }
    public static r(File f){
        Inputstream in =new Inputstream(f);
        ObjectInputstream ob=new ObjectInputstream(in);
        A a=(a)ob.readobject();//直接在文件中将对象读出
        System.out.println(a);
        ob.close();
    }
}
class A implements Serializable{
        private String name;
        private int i;
        A(String _name;int _i){
        this->name=_name;
        this->i=_i;
        }
        public String toString(){
        return "姓名为："+this->name+"工资为："+this->i;
        }
}
```

```
运行结果:
姓名为：张三工资为：1000
```
上面的程序只是简单的把类的属性值写进文件里，但你要是不想要类中的某个属性值的时候只需要在类中的元素关键字前面加上transient就能把这个属性值不放进文件里

# 线程

进程与线程的区别
- [ ] 就是一个执行中的程序，它是动态的表现。当我们在下载QQ程序的时候，程序是静态不变的。但在我们打开三个QQ的聊天窗口的时，实际上就是开启了三个线程。由此可见，一个程序是可以对应多个进程的，每一个进程都有自己独立的一组系统资源。在进程的概念中，每一个进程的内部数据和状态是独立的，这是容易理解的，但我们开启三个QQ窗口聊天是，三个QQ进程对应的聊天对象，聊天内容都是不一样的。

- [ ] 由此可以发现多线程就在我们的身边，而且占据着重要的位置，经常为网络流读取，IO读取，下载等一些任务量比较巨大，耗时比较长的任务单位才开发线程

- [ ] 进程是操作系统的资源分配单位，创建并执行一个进程的系统开销是比较大的。相比而言，线程是进程的一个执行路径，多线程指的是在但个进程中同时运行不同的线程，执行不一样的任务。多线程意味着一个程序的多行语句块并发执行。

- [ ] 同属一个进程的多线程是共享一块内存空间和一组系统资源，属于线程本身的数据通常只有寄存器和堆栈内的数据。所以，当进程生产一个线程或者是在多线程之间来回切换时，负担是比进程小的多的，正因如此，线程也被称为清负荷进程。


```
public class Test{
    public static void main(String [] args){

        new test.run();
        for(int i=0;i<2;i++){
        System.out.println("main,在运行");
        }
    }
}
class test{
    public void run(){
        for(int i=0;i<2;i++){
        System.out.println("test,在运行");
        }
    }
}

```

```
运行结果:
test,在运行
test,在运行
main,在运行
main,在运行
```


```
public class Test{
        public static void main(String [] args){
        new test.start();
        for(int i=0;i<2;i++){
        System.out.println("main,在运行");
        }
        try{
        Thread.sleep(1000);
        }catch(InterruptedException e){
        e.printStackTrace();
        }

}
class test extends Thread{
    public void run(){
        for(int i=0;i<2;i++){
        System.out.println("test,在运行");
        }

        try{
        Thread.sleep(1000)
        }catch(InterruptedException e){
        e.printStackTrace();
        }
}
```


```
test,在运行
test,在运行
main,在运行
main,在运行
```

这里的运行结果是和书上不一样的，这是因为多线程的执行顺序是有一定的不确定性的。但是只要知道线程的父类是Thread，要想启动线程就要调用父类的start方法，系统会自动调用run你重写的类里的run方法。


## 多线程
```
public class Test{
    public static void main(String [] args){

        test t=new test();
        new Thread(t).start();
        for(int i=0;i<5;i++){
        System.out.println("main,在运行");
        }
        try{
        Thread.sleep(1000);
        }catch(InterruptedException e){
        e.printStackTrace();
        }
    }
}

class test implements Runnable{
    public void run(){
        for(int i=0;i<5;i++){
        System.out.println("test,在运行");
        }

        try{
        Thread.sleep(1000)
        }catch(InterruptedException e){
        e.printStackTrace();
        }
}
```

`利用Runnabe接口来实现多线程，同样是利用Thread类里的start方法来调用自己覆写的run方法，在Runnable里只有一个run方法，在这个接口里面是没有start这个方法的，要想用这个接口来实现多线程只能通过Thread类里的start方法来实现` 

```
public class Test{
    public static void main(String [] args){
        new test.start();
        new test.start();
        new test.start();
        new test.start();
        new test.start();
    }
}
class test extends Thread{
        private int i=2;
        public void run(){
            while(i>0){
            System.out.println(Thread.currentThread().getName()+"出售票"+i);
            i-=1;
            }
        }
}
```

```
运行结果:
Thread-0出售票2
Thread-0出售票1
```

上面的结果是五次的一样的，只能说利用Thread类的多线程的资源是分开的，而不是共享资源的。这里的结果是没调用一次它的售票数量都是重新更新的，这是因为这里的资源是不共享的,你也可以将变量的类型设置为static类型来试试，将变量设置为全局变量

```
public class Test{
    public static void main(String [] args){
    test t=new test();
    new Thread(t).start();
    new Thread(t).start();
    }
}
class test implements Runnable{
        private int i=2;
        public void run(){
            while(i>0){
            System.out.println(Threa.currentThread().getName()+"出售票"+i);
            i-=1;
            }
        }
}
```

```
运行结果:
Thread-0出售票2
Thread-0出售票1
```
而利用Runnable接口的资源是共享的,这里的变量是属于典型的临界资源,而run方法里面代码块是属于临界区。多个进程中涉及到同一个临界资源的临界区成为相关临界区。


```
public class Test{
    public static void main(String [] args){
            test test=new test();
            test.test();
            new test().start();
    }

}
class test extends Thread {
    pubic void run(){
        test();
    }
    public test(){
        String str=Thread.currentThread().getName();
        System.out.println(str);
    }
}
```

```
运行结果:
main
Thread-1
```

这里就是将线程的名称打印出来，利用的是Thread的currentThread方法的getName方法，它的返回值类型是String类型，它返回的不仅仅是当前线程的名称，还返回调用这个方法的线程名称，所以这里输出是不一样的,


```
public class Test{
    public static void main(String []args){
            A a=new A();
            Thread th=new Thread(a);//通过Thread类来声明A类
            th.setName("main123");//更改名字
            th.start();//线程开启
    }
}
class A implements Runnable{
    public void run(){//得到线程的名称并输出
        String name=Thread.currentThread.GetName();
        System.out.println(name);
    }
}
```

```
运行结果:
main123
```


```
public class Test{
    public static void main(String []args){
        A a=new A();
        System.out.println("线程=="+a.isAlive());//判断线程是否开启
        a.setName("main123");//更改线程的名称
        a.start();//线程开启
        System.out.println("线程=="+a.isAlive());//同上
        System.out.println(a.test());//调用自己写的方法

    }
}
class A extends Thread{
    public void run(){//调用方法
            test();
    }
        public void test(){//通过调用类的全局方法来获得线程的名称并输出
            String name=Thread.currentThread.GetName();
            System.out.println(name);
        }
}
```

```
运行结果:
线程==false
main123
线程==true
main
```

```
public class Test{
    public static void main(String [] args){
        Thread tt=new Thread(new A());
        tt.setDaemon(true);//设置为守护线程
        test.start();//启动线程
    }
}
class A implements Runnable{
    public void run(){
    for(int i=0;true;i++){//死循环
        String name=Thread.currentThread.GetName();
        System.out.println(i+"--"+name);
        }
    }
}
```

这里的运行for循环虽然是一个死循环，但随着线程的设置属性把它设置为守护线程(后台线程)之后就不会出现死循环的结果，守护线程是随着main结束时就随之终止的。这就验证了只要是只有守护线程运行时，程序就会有终止的时候。另外的情况就是，只要还有用户线程(一般线程，前台线程)的时候，java虚拟机(JVM)就不会退出


**线程阻塞** 

*线程阻塞，其实就是让一个线程先执行完成，然后再调用另外一个线程。* 

```
public class Test{
    public static void main(String [] args){
        Thread thread=new Thread(new A());//线程的声明
        thread.start();//线程开启
        int i=0;
        for(int x=0;x<3;x++){
            if(i==1){
                try{
                thread.join();//在特定的数值的时候开启线程的阻塞
                }catch(Exception e){
                e.getMessage();
                }
            }
            System.out.println("main"+i);
            i+=1;
        }
    }
}
class A implements Runnable{
    public void run(){//改写的方法
        for(int i=0;i<3;i++){
            try{
            Thread.sleep(1000);
            }catch(InterruptedException e){
            ex.printStackTrace();
            }
            String name=Thread.currentThread.GetName();
            System.out.println(name+"--"+i);
        }
    }
}
```

```
运行结果:
main0
main1
0--Thread-0
0--Thread-1
0--Thread-2
main2
```
就是在main方法里先执行完你写的线程里面的方法，然后在执行main里面的代码，

**线程中断** 

* interrupt() 一个线程运行时，另外一个线程可以调用另外一个线程对应的interrupt()方法来中断它
* isInterrupted() 来获取线程的中断状态
* interrupted() 这是一个静态方法，用来获取中断状态，并清除中断状态，其获取的是清除之前的值，也就是说连续两次调用的话，返回的一定是false。

```
public class Test{
    public static void main(String [] args){
        Thread test=new Thread(new A());
        test.start();
        try{
            Thread.sleep(2000);
        }catch(InterruptedException e){
        ex.printStackTrace();
        }
        System.out.println("在main方法中中断其他线程");
        test.interrupt();
        System.out.println("在main方法中退出");
    }
}
class A implements Runnable{
    public void run(
            try{
            System.out.println("在run方法中睡眠10秒")
            Thread.sleep(10000);
            System.out.println("在run方法中正常运行")
            }catch(InterruptedException e){
            System.out.println("在run方法中中断线程");
            }
    )
}
```

```
运行结果:
在run方法中睡眠10秒
在main方法中中断其他线程
在main方法中退出
在run方法中中断线程
```

中断线程(interrupt)方法是利用join和sleep或对于I/O操作等原因受阻的线程产生影响，

```
public class Test{
    public staric void main(String [] args){
        Thread test=Thread.currentThread();
        System.out.println("main没有被中断的状态:"+test.isInterrupted());
        test.interrupt();
        System.out.println("main中断之后的状态:"+test.isInterrupted());
        try{
        Thread.sleep(1000);
        }catch(InterruptedException e){
            System.out.println("在main方法中中断");
        }
        System.out.println("main方法的状态:"+test.isInterrupted());
    }
}
```

```
运行结果:
main没有被中断的状态:false
main中断之后的状态:true
在main方法中中断
main方法的状态:false
```

**线程同步** 

```
public class Test{
    public static void main(String [] args){
        
    }
}
class A implements Runnable{
        private  int i=5;
        public void run(){
            while(true){
                synchronized(this){
                    if(i<=0){
                    break;
                    }
                    try{
                    Thread.sleep(100);
                    }catch(InterruptedException e){
                    ex.printStackTrace();
                    }
                    System.out.println(Thread.currentThread.GetName()+"出售票:"+i)
                    i-=1;
                }
            }
        }
}
```

```
运行结果:
Thread-0出售票5
Thread-0出售票4
Thread-0出售票3
Thread-0出售票2
Thread-0出售票1
```

为了进一步保证线程同步的更好，我们这里将进行原子性，所谓的原子性是值，代码要么被执行，要么不执行，不存在执行一部分被中断的情况。在这里的代码就好比是独步桥，任何时刻都只能是一个人在桥上走，即程序不能是多个线程同时访问临界区(共享资源)，从上面可以看出来，synchronized针对的是对象。

> 对方法进行同步

```
public class Test{
    public static void main(String []args){
            A a=new A();
            new Thread(a).start();
            new Thread(a).start();
            new Thread(a).start();
            new Thread(a).start();
    }
}
class A implements Runnable{
        private int i=5;
        public void run(){
            while(i>0){
                test();
            }
        }
        public synchronized void test(){
            if(i>0){
                try{
                    Thread.sleep(100);
                }catch(InterruptedException e){
                ex.printStackTrace();
                }
                System.out.println(Thread.currentThread.GetName()+"出售票"+i)
                i-=1;
            }
        }
}
```

```
运行结果:
Thread-0出售票5
Thread-0出售票4
Thread-0出售票3
Thread-0出售票2
Thread-0出售票1

```

这是利用synchronized修饰的方法，原子型的方法，这种方法的特点是，要么执行完毕，要么不执行。还有就是，当有一个线程进入这种类型的方法时，其他线程就不能进入到同一个对象，直到第一个线程执行完它所进入的synchronied修饰的方法为止。


**线程通信** 

```
public class Test{
    static class A implements Runnable{
        Perion p;
        public A (Perion p){
            this.p=p;
        }
        public void run(){
            for(int i=0;i<10;i++){
                if(i%2==0){
                this.name="里斯";
                this.sex="女";
                }else{
                this.name="张三";
                this.sex="男";
                }
            }
        }
    }
    static class B implements Runnable{
        Perion p;
        public B (Perion p){
        this.p=p;
        }
        public void run(){
            for(int i=0;i<10;i++){
            System.out.println(this.name+"--"+this.sex);
            }
        }
    }
    public static void main(String [] args){
        Perion  p=new Perion ();
        new Thread(new A(p)).start();
        new Thread(new B(p)).start();
    }
}
class Perion{
        String name="张三";
        String sex="男";
}
```

上面的结果的性别是打印出来的是不一样的，这相当与，A类还没有将数据写入，B类就先打印出来了，这就是所谓的资源没有被共享，生产者还没生产东西，消费者就先消费了，消费者还没消费完，生产者就先生产了，不管是消费还是生产都应该相互通信好


```
public class Test{
    static class A implements Runnable{
        Perion  p;
        public A (Perion p){
        this.p=p;
        }
        public void run(){
            for(int i=0;i<10;i++){
                if(i%2==0){
                p.set("里斯","女")
                }else{
                p.set("张三","男")
                }
            }
        }
    }

    static class B implements Runnable{
        Perion p;
        public B(Perion p){
        this.p=p;
        }
        public void run(){
            for(int i=0;i<10;i++){
            p.get();
            }
        }
    }
    public static void main(String [] args){
        Perion p=new Perion ();
        new Thread(new A(p)).start();
        new Thread(new B(p)).start();
    }
}
class Perion(){
        String name="张三";
        String sex="男";
        public synchronized void Set(Sting name,String sex){            
        this.name=name;
        this.sex=sex;
        }
        public synchronized void get(Perion p){
        System.out.println(this.name+"--"+this.sex);
        }
}
```

上面虽然保证了数据的准确性，但打印的只是第一次写入的东西,而不是说每一次写入的东西都会直接打印出来，这也相当与是生产者和消费者之间的关系


```
public class Test{
    static class A implements Runnable{
        Perion  p;
        public A (Perion p){
        this.p=p;
        }
        public void run(){
            for(int i=0;i<10;i++){
                if(i%2==0){
                p.set("里斯","女")
                }else{
                p.set("张三","男")
                }
            }
        }
    }

    static class B implements Runnable{
        Perion p;
        public B(Perion p){
        this.p=p;
        }
        public void run(){
            for(int i=0;i<10;i++){
            p.get();
            }
        }
    }
    public static void main(String [] args){
        Perion p=new Perion ();
        new Thread(new A(p)).start();
        new Thread(new B(p)).start();
    }
}
class Perion(){
        String name="张三";
        String sex="男";
        boolean bfull=false;
        public synchronized void Set(Sting name,String sex){
            if(bfull){
                try{
                wait();//让线程等待
                }catch(InterruptedException e){
                    ex.printStackTrace();
                }
            this.name=name;
            this.sex=sex;
            bfull=true;
            notify();//唤醒最先到达的线程
            }
        }
        public synchronized void get(Perion p){
            if(!bfull){
                try{
                    wait();
                }catch(InterruptedException e){
                ex.printStackTrace();
                }
                System.out.println(this.name+"--"+this.sex);
                bfull=false;
                notify();
            }
        }
}
```
结果是每写一次进去就读一次出来，主要是靠wait和notify这两个方法和变量bfull来控制的，通过bfull来控制什么时候写入和打印，而wait和notify这两个方法是相互影响的，notify唤醒的是所有线程中含有wait方法的线程。

**线程的生命周期** 

```
public class Test{
    public static void main(String [] args){
        A a=new A();
        new Thread(a).start();
        for(int i=0;i<4;i++){
            if(i==2){
            a.show();
            }
            System.out.println("在main方法中运行");
        }
    }
}
class A implements Runnable{
        private boolean bfull=true;
        public void run(){
            while(bfull){
            System.out.println(Thread.currentThread.GetName()+"在运行");
            }
        }
        public void show(){
            bfull=false;
        }
}
```

```
运行结果
在main方法中运行
在main方法中运行
Thread-0在运行
在main方法中运行
在main方法中运行
```

- [ ] 同步代码块和同步方法针对的是对象，而不是代码
- [ ] 如果一个进程中只有后台进程，则这个进程一定会结束
- [ ] 每一个已经被创建的线程在结束之前都是处于就绪，运行，阻塞状态之一


**socket** 

*在网络上运行的两个程序间双向通信的一端，它既可以接受请求，也可以发生请求，利用它可以较为方便地实现网络上数据的传输。* 

socket有两种连接方式：1.面向连接。2.面向无连接。

- [ ] 面向连接就像是打电话，在发送数据前要先建立好连接，然后再发送要发送的数据，所有到达的事情都将与它们出发时的顺序是一样的。
- [ ] 面向无连接的直接发送数据，但它们是没有保障的，它们的到达顺序与出发时是不一样的。

TCP/IP：我们叫做服务端和客户端。一般来说是由客户端发起请求，服务端接受请求，然后开始通信。在这其中有一个特殊的地方就是，作为服务端的一方需要等待客户端来连接。

serversocket封装的底层操作就是作为服务的提供端。主要完成以下功能:
1.绑定ip地址(是为了让客户端能够在浩瀚的网络上找到提供服务的这台服务器)
2.绑定端口(实际上是为了解决一台服务器上标识好几个服务用的。比如，你电脑上有HTTP服务和FTP服务)

```
public class Test{
    public static void main(String [] args){
    //服务端
        ServerSocket server=new ServerSocket(9999);//定义服务端的端口号
        Socket socket=server.accept();//用来监听客户端
        PrintWrite print=new PrintWrite(socket.getOutputStream(),true);//通过流来向客户端写东西
        print.println("hello");
        print.flush();//刷新输入流(刷新读的操作)
        188517020052
        server.close();
        socket.close();
        print.close();
    //客户端 
        Socket socket1=new Socket("127.0.0.1",9999);//与服务端进行连接
        BufferedReaber buff=new BufferedReaber(new Inputstream(socket1.getInputStream()));//通过流来读取服务端发送的数据
        System.out.println(buff.readLine());//输出数据
        socket1.close();
        buff.close();
    }
}
```

```
运行结果:
hello
```
程序分别分布在不同的文件上，ip地址写的是本机的地址(127.0.0.1)||(0.0.0.0)，然后端口号绑定的是一样的就行了，通过ServerSocket类来定义服务端的端口号，

```
public class Test{
    public static void main(String [] args){
    //服务端
            ServerSocket server=new ServerSocket(8888);
            Socket socket=server.accept();
            BufferedReaber buff=new BufferedReaber(new Inputstream(socket.getInputStream(),"UTF-8"));
            String str;
            while()(str=buff.readLine())!=null){
                System.out.println(str)
                    if(str.equals("bye")){
                        System.out.println("聊天结束");
                        server.close();
                        socket.close();
                        buff.close();
                        break;
                    }
            }

    //客户端
            Socket socket=new Socket("127.0.0.1",8888);
            BufferedReaber buffr=new BufferedReaber(new Inputstream(System.in));
            BufferedWriter buffw=new BufferedWriter(new OutputStream(socket.getOutputStream),"UTF-8");
            while(true){
            String str=buffr.readLine();
            buffw.write(str);
            buffw.write("\n");
            buffw.flush();
            if(str.equals("bye")){
                socket1.close();
                buffw.close();
                buffr.close();
                break;
            }
            }
    }
}
```

单面的在服务端打印出客户端的消息，并通过特定的字符来关闭对话。

```
public class Test{
    public static void main(String [] args){
    //服务端
            ServerSocket server=new ServerSocket(8888);
            while(true){
                try{
                Socket socket=server.accept();
                new Thread(new Runnable(){
                        public void run(){
                        try{
                        BufferedReaber buff=new BufferedReaber(new Inputstream(socket.getInputStream,"UTF-8"));
                        String s;
                        while((s=buff.readLine())!=null){
                            System.out.println(s);
                            if(str.equals("bye")){
                                server.close();
                                break;
                            }
                        }
                            }catch(IOException e){
                        e.printStackTrace();
                        }
                }
            }).start();
                }catch(IOException e){
                    System.out.println("聊天结束")
                }
        }

    //客户端
        Socket socket=new Socket("127.0.0.1",8888);
        BufferedReaber buffr=new BufferedReaber(new Inputstream(System.in));
        BufferedWriter buffw=new BufferedWriter(new OutputStream(socket.getOutputStream()),"UTF-8");
        while(true){
            String str=buffr.readLine();
            buffw.write(str);
            buffw.flush();
            if(str.equals("bye")){
                socket.close();
                buffw.close();
                buffr.close();
                break;
            }
        }
    }
}
```

利用线程来进行多个客户端来向服务端进行模拟通信，只是在服务端中回显客户端的写入的数据。

**UDP** 

使用流套接字的每个连接需要花费一定的时间，要减少这样的开销，网络API提供了第二种套接字：自寻址套接字(DatagramSocket)。

*自寻址使用UDP发送寻址信息，不同的是可以通过自寻址套接字发送多个IP信息包，自寻址信息包含在自寻址包中，自寻址包又包含在IP包中，这样就将寻址信息长度限制在60000字节中。* 

```
public class Test{
    public static void main(String [] args){
        //服务器
        DatagramSocket ds=new DatagramSocket(3000);
        String s="hello";
        DatagramPacket dp=new DatagramPacket(s.getbytes(),s.length(),InetAddress.getLocalHost(),9000);
        ds.send(dp);
        //客户端
        DatagramSocket ds=new DatagramSocket(9000);
        DatagramPacket dp=new DatagramPacket(new byte[1024],1024);
        ds.receit(dp);
        System.out.println(new String(dp.getData()));
    }
}
```


