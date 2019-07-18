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