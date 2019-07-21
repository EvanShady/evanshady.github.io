# Qt
*图形化界面--GUI。这个工具对于程序员的开发是便利的，特别是开发用户的图形化界面，在Linux里也是用到了qt的。*
----
```
#include <QApplication>//使用qt的头文件
#include <QWidget>//窗口控制基类
#include <QPushButton>//指定父对象的头文件
int main(int argc,char *argv[]){
        QApplication  a(argc,argv);
        My_widget w;
        w.setwindowTitle("主要看气质");//文件头名
        QPushButton b;//声明按钮的类     
        b.setParent(&w);//让按钮放在父对象的函数
        b.setText("删除");//声明按钮,并赋值
        b.move(100,100);//移动按钮
        QPushButton b1(&w);//使用按钮构造函数并指向父对象
        b1.setText("确认");//声明按钮,并赋值
        b1.move(200,200);//移动按钮
        w.show();//输出函数
        return app.exec();
}
```
![运行结果](Qt/Qt1.png)
**值得注意下的就是，如果不给按钮对象指向父对象，两个窗口是独立的。还有上面是用了两种方式来指向父对象，一个是用函数setParent(),另外一个是用构造函数来指向。**
```
#include <QApplication>
#include <QWidget>
#include <QLabel>
int main(int argc,char *argv[]){
            QApplication a(argc,argv);
            QLabel label("Hello");
            return a.exec();
}
```
![运行结果](Qt/Qt2_hello.png)
**上面的代码有点不好，但要是一定要这样的话，那在main函数里面的代码是很多的。这样让别人看起来就有点不好的感觉。**
**QPushButton--是按钮，QWidget--是窗口**
* signals--信号(类似与广播，发出信号，如果有对它有意思的，就有connect连接，来把它连接在一起)
* connect--连接(意思是，用自己的函数(成为槽(solt))来处理这个信号)
```
//练练手，长长记性
//main函数里面的头文件
#include <QApplication>
#include <QPushButton>
#include "My_Widget.h"

//是以公有的方式继承了窗口化的类,.h文件
#include "sud.h"
class My_Widget:public Widget{
public:
        My_Widget(QWidget *parent =nullptr);
        ~My_Widget();
        void showb2();
        void showwid();
        void showxin();
private:
        QPushButton b1;
        QPushButton *b2;
        QPushButton b3;
        sud s;
}
//.cpp文件
#include "My_Widget.h"
My_Widget::MyWidget(QWidget *parent =nullptr):QWidget(parent){
        b1.setParent(this);
        b1.setText("^_^");
        b1.move(100,100);
        b2=new QPushButton (this);
        b2->setText("abc");
        connect(&b1,&QPushButton::released,this,&QPushButton::close);
        connect(b2,&QPushButton::released,this,&My_Widget::show);
        s.show();
        this->setWindowTitle("老大");
        b3.setParent(this);
        b3.setText("切换子窗口");
        connect(&b3,&QPushButton::released,this,My_Widget::showwid);
        connect(&s,&sud::xin,this,&My_Widget::showxin);//接收信号并处理信号
        resize(400,300);
        //当信号发出时，被连接的槽函数会被回调用来处理信号发出的操作
}
void My_Widget::showb2(){
        b2->setText("123");
}
void My_Widget::showwid(){
        s.show();
        this->hide();
}
void My_Widget::showxin{
        this->show();
        s.hide();
}

//是以公有的方式继承My_Widget类的派生类
#include <QWidget>
#include <QPushButton>
class sud : public My_Widget{
public:
        explicit*** sud(QWidget *parent =nullptr)
        void showwid();//用来发射信号的函数
signals:
        void xin();//信号
private:
        QPushButton b;
}
void sud::sud(QWidget *parent):QWidget(parent){
        this->setWindowTitle("小弟");
        b.setParent(this);
        b.setText("切换父窗口");
        connect(&b,QPushButton::clicked,this,&sud::showwid);//发送信号的
        resize(400,300);
}
void sud::showwid(){
        emit xin();
}


int main(int argc,char *argv[] ){
        QApplication a(argc,argv);
        My_Widget w;
        w.show();
        return a.exec();
}
```
**槽**
1. 任意的成员函数，普通全局函数，静态函数
2. 槽函数需要与信号一样(返回值和参数)由于信号没有返回值，所以槽函数也没有返回值
**信号**
1. 信号必须有关键字signals
2. 信号没有返回值，是个函数,可以有参数
3. 信号只有声明，无需为信号定义
4. 使用的方法:使用关键字emit来调用
* 按钮只是回调了槽函数，而窗口的所有改动都是该窗口改变的，和按钮是没什么关联的。
**内存**
1. 指定父对象后,直接或间接的继承于Q0bject
2. 子对象如果动态分配空间(new)，不需要手动释放(delete)，系统会自动调用析构函数
```
#include <QMenuBar>//菜单栏
#include <QMenu>//菜单
#include <QAction>//控件
#include <QToolBar>//快捷键
#include <QDebug>//打印
#include <QStatusBar>//状态栏
#include <QLabel>//
#include <QTextEdit>//核心控件
#include <QDockWidget>//浮动窗口
* 创建菜单栏和一些控件
* 以下的代码是在构造函数的里面的，主要是懒得写了。
        QMenuBar *mbar=menuBar();//声明一个菜单栏
        Qmenu *f1=mbar->addAction(文件);//在菜单栏里写一个以文件为名的控件
        QAction *p1=f1->addAction("新建");//在文件里写一个以新建为名的控件
        connect(p1,&QAction::triggered,//槽函数
        []()
        {
                qDebug()<<"新建被按下";
        });
        f1->addSeparator();//分割线
        QAction *p1_2=f1->addAction("打开");//同上
        Qmenu *f2=mbar->addAction("编辑");
        QAction *p2=f2->addAction("编辑");
        connect(p2,&QAction::triggered,
        []()
        {
                qDebug()<<"编辑被按下";
        });
        QStatusBar *sbar=statusBar();//状态栏，主要在最左下方显示文件的状态
        QLabel *label= new QLabel (this);
        sbar ->addAction(new QLabel("2",this));//以从左往右的方式显示2
        sbar-> addPermanentWidget(new QLabel("3",this));
        //以从右忘左的方式显示3
        QTextEdit *text=new QTextEdit(this);//核心控件，也就是文件编辑的地方
        setCentralWidget(text);
        QDockWidget *dock=new QDockWidget(this);//浮动窗口
        addDockWidget(Qt::LeftDockWidget,dock);//在左边显示
        QTextWidget *text1=new QTextWidget(this);//声明编辑
        dock->setWidget(text1);//在浮动窗口里显示文件编辑的地方

```
----
![运行结果](Qt/Qt3_caidan.png)