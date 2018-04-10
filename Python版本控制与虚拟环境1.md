# Python版本控制与虚拟环境1

在前面我们已经知道了Python分为python2版本和Python3版本，虽然Python3版本是大势所趋，但是有时候公司的开发环境就是Python2，毫无办法，为了生存，你只能也安装上Python2，那可能就会出现版本混乱的问题，比如你调用pip来安装第三方库，此时你使用的pip是python2上的还是python3上的呢？安装的第三方库被安装在python2上了还是安装到了python3上了？为了解决这种情况就需要**对Python的版本进行管理和控制，所以就有Python版本控制的说法**

那Python虚拟环境又是什么？其实也很好理解，现在你有2个项目要开发，其中一个项目使用到了A、C这两个第三方库且A库依赖于C库，而第二个项目使用到了B、C这两个第三方库且B库依赖于C库，可以发现两个项目都使用到了C库且A库、B库都依赖于C库，那么就会这样的问题，比如A库需要1.0版本的C库，而B库却依赖于2.0版本的C库，此时你就会发现，无论安装那个版本的C库都有个项目无法开发，如果每个项目都有个独立的Python环境，如A、C库在一个Python开发环境中，B、C库在另一个Python开发环境中就不会有这样的问题了，而Python虚拟环境就是这样的一个环境，它**在系统默认的Python之上建立新的环境，在这个环境中，所有的库和Python代码都是独立的与系统Python环境和其他Python虚拟机环境无关的**，这样就不会有第三方库冲突的问题了

因为windows和Mac/Linux上Python版本控制和虚拟环境的使用方式有点不同，所有就分开来讲解

## windows上Python版本控制与虚拟环境

直接在windows上安装python2和python3，如何安装python3可以看前面一章

但是如果你按照前一章来安装python2，你会发现没有Add Python 2.7 to PATH这样的选项，这就需要我们自己去添加PATH，所以在安装python2时，你需要记住python2安装的路径，然后将该路径填写到PATH中

方法一：
1.右击我的电脑--->属性，然后按下图操作就好了，从图中可以看出，我python的路径是C:\Python27，注意前面的;要是英文状态下的;

![](http://p3609n7fk.bkt.clouddn.com/python2PATH.png)

方法二：
打开在cmd下输入： path=%path%;C:\Python27  接着按"Enter"回车键。 


安装好后，打开cmd，输入python，你会发现进入了python2的交互环境，exit()退出python2交互环境，输入py，你会发现进入了python3的交互环境

![](http://obfs4iize.bkt.clouddn.com/py2%E5%92%8Cpy3.png)

可以看出，使用系统中的python2，只需要在cmd中输入python，而要使用python3，只需要在cmd输入py，其实python3已经考虑到了python2和python3需要共存的情况了，所以py可以直接调用python3，以此与python2区别开来

这里分别使用python2和python3的pip为例

直接使用pip，默认就是使用python2的pip，要使用python3的pip，则使用下面的命令

```
py -3 -m pip -version
```

![](http://obfs4iize.bkt.clouddn.com/pip%E5%92%8Cpip3.png)

从图中也可以看出，这两个pip分别属于python2.7和python3.6

当然你可能会遇到刚好相反的情况，输入python结果进入了python3的交互环境，那么要进入python2，只需输入py -2则可

![](http://p3609n7fk.bkt.clouddn.com/python2python3.png)

如果想要在python2上安装第三方库，比如安装requests，可以通过下面命令安装

```
py -2 -m pip install requests
```

windows下python的版本控制就到这里，接着来看windows下python虚拟环境的使用

首先讲python2如何创建和使用虚拟环境

## Python2安装和使用虚拟环境

首先通过pip来安装virtualenv，**virtualenv可以创建独立的python虚拟环境**，解决包依赖和版本等问题，命令如下，将virtualenv安装到了Python2中

```
py -2 -m pip install virtualenv
```

使用virtualenv创建名为envpy2的python虚拟环境，命令如下，它会在当前目录下创建envpy2的python虚拟环境

```
py -2 -m virtualenv envpy2
```

然后要进入envpy2\Scripts下通过activate命令来启动虚拟环境，如下图

![](http://p3609n7fk.bkt.clouddn.com/py2virtualenv.png)

输入activate后，可以发现命令行前面多了（envpy2）表示现在已经在envpy2这个python虚拟环境中，在这个环境中做的任何操作都不会影响到系统的python和其他独立环境

如果你要退出envpy2这个虚拟环境，同样进入envpy2\Scripts下，输入deactivate就可以退出虚拟环境了

```
deactivate
```

virutalenv还有一些高级用户，有能力的用户，可以自行Google学习使用

## Python3安装和使用虚拟环境

虽然virtualenv可以指定创建虚拟环境时所使用的python版本，但是在python3.3以上的版本的python中已经集成安装了venv模块，我们可以通过这个模块简单的创建python3的虚拟环境，创建Python虚拟环境的命令如下，创建名为ayuliao的Python虚拟环境

```
py -3 -m venv ayuliao
```

虚拟环境的使用方式跟上面的一样

![](http://obfs4iize.bkt.clouddn.com/py3%E5%88%9B%E5%BB%BA%E8%99%9A%E6%8B%9F%E7%8E%AF%E5%A2%83.png)

## 小结
本节介绍了如何在windows上分别使用python2和python3，同时介绍了如何在python2和python3下创建python独立的虚拟环境



