---
title: file
date: 2019-05-31 13:57:01
tags:
---
# 文件
> 文件有两种类型：
* 文本文件--以ASCLL码形式存储在计算机中。
* 二进制文件--以二进制写进计算机。
>> 分为三种类型：1.写文件（ofstream）,2.读文件（ifstream）3.（fstream）。
* 写入文件分为5大部分：
1. 先把写文件的头文件包含进去。
2. 然后确定你要写的文件的类型
3. 之后确定文件的名字和打开的方式
4. 把内容写进去
5. 关闭文件
![打开方式](file/file.png)
```
#include<iostream>
#include<fstream>//引入写文件的头文件
using namespace std;
void test(){
    ofstream ofs;// 文件的类型 写入文件
    ofs.open("test.txt",ios::out);文件名和打开的方式
    ofs<<"你好！"<<endl;把你要写进文件的内容写进去
    ofs.close(); 关闭文件
}
void test1(){
    ifstream ifs;//文件类型，读文件
    ifs.open("test.txt",ios::in);//打开的文件名和打开方式
    if(!ifs.is_open()){//判断打开文件
        cout<<"文件打开失败"<<endl;
    }
    string buf;
    while(getline(ifs,buf)){//以一行的形式写入编译器并输出
        cout<<buf<<endl;
    }
    ifs.close();关闭文件
}
int main(){
    test();//调用test函数
    test1();//调用函数
}
```
## 对于写的内容追加到文件中的命令是如下：
```
#include <iostream>
#include <fstream>
using namestape std;
int main(){
    ofstream ofs;//声明文件的形式
    ofs.open("test",ios::app);//打开的方式
    ofs<<"你好"<<endl;//写进的内容
    ofs.close();//关闭文件
    ifstream ifs;//声明文件的形式
    ifs.open("test",ios::in);//打开的方式
    if(!ifs.isopen()){//判断文件的打开是否成功
        cout<<"文件打开失败"<<endl;
    }
    ifs.close();//关闭文件
}
```
* 在这里运行几次之后的结果会和第一次的不一样，因为在这里是以追加的形式向文件中写入你的内容。
![运行结果](file/file1.png)