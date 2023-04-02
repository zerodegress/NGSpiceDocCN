# 初学者的NGSpice

## 介绍

ngspice是一个电路模拟器，用数值方法求解描述(电子)电路的方程：这些方程由无源和有源元件组成。模拟时变电流和电压以及噪声和小信号的特性。ngspice是加州大学伯克利分校久负盛名的 spice3f5的开源继承者。

![图一](img/ngspice_for_beginners/intro1.png "图一")

图一

就像图一展示的一样，你从一个电路（这里是逆变器）开始。你必须创建一个描述这个电路的网表（netlist）。网表是ngspice的输入，告诉它要模拟的电路。与一些模拟命令一起，这个输入负责读取和解析网络列表，启动模拟并绘制输出。输出电压(用红色表示)与输入(绿色表示)相反。两个电压都随时间变化。

ngspice 的输入是从文件中读取的，并且可以通过命令行中给出的命令对其进行增强。模拟输出可以写入文件，也可以绘制成y-x图或 Smith图。虽然没有电路图示意图捕捉和自动生成网表的图形用户界面，但是有[第三方工具](https://ngspice.sourceforge.io/resources.html)可以绘制电路并生成ngspice网表。

这里是一份可用的ngspice的详细的[参考手册](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/37/ngspice-37-manual.pdf/download)。
本手册描述了 ngspice 中可用的所有命令和过程，并列出了许多示例。但是，它不是一个 如何使用ngspice或者介绍性的文章。
如果您有兴趣获得更深入的信息，您可以参考我们的[书籍页面](https://ngspice.sourceforge.io/books.html)或[第三方教程列表](README.md)。

## (1) 下载和安装ngspice（MS WIndows, 64位）

下载这个[ngspice-37](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/37/ngspice-37_64.zip)的zip文件。展开压缩包到C:\下。在MS Windows 10你可能呢个需要管理员权限才能这么做。这样你就会得到C:\Spice64和几个子文件夹。主程序ngspice.exe就在C:\Spice64\bin中。

如果你想要使用PSPICE元件模型（通常由半导体公司提供），在你的用户目录（C:\users\‘你的名字’，也可以在环境变量USERPROFILE中找到）放置一个纯文本文件命名为“.spiceinit”。增加如下两行：

```plaintext
    *user provided init file
    set ngbehavior=ps
```

到“.spiceinit”中。如果文件名“.spiceinit”对你不奏效，使用另一个文件名“spice.rc”。就那样！

在双击“C:\Spice64\bin\ngspice.exe”之后，nspice主窗口就会弹出。

![图二](img/ngspice_for_beginners/fig2-complete.png "图二")

图二

## （2）下载和安装ngspice（Linux）

如果你正在使用Linux，请检查你的发行版提供了一个[ngspice软件包](https://ngspice.sourceforge.io/packages.html)用于安装。你可能使用发行版的包管理工具（apt,Yast等等）安装。

如果不是，你需要下载[ngspice-37.tar.gz](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/37/ngspice-37.tar.gz/download)并用以下命令编译ngspice：

```shell
./configure --with-x --enable-xspice --enable-cider --with-readline=yes --enable-openmp --disable-debug CFLAGS="-m64 -O2" LDFLAGS="-m64 -s"
make -j8
sudo make install
```

或者是运行文件夹下的compile_linux.sh脚本：

```shell
./compile_linux.sh 64
```

(WIP)
