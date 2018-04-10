# 第一个python程序

前面已经讲解python安装、pip使用和python版本控制与虚拟环境的使用，我们可以熟悉的搭建python开发环境了，接着我们就来写第一个python程序

打开命令行，输入python，进入python3的交互环境

在交互式命令行可以通过下面代码输出一句话

```python
print('你好，python')
```

进行简单的加减乘除运算

```python
100+100  #200 加法

100//100 #1   地板除，结果只会留下整数

100/100  #1.0 除法，结果会是浮点数

100*2    #200 乘法

10**2    #100 指数运算，10的二次方

100-10   #90  减发
```

![](http://p3609n7fk.bkt.clouddn.com/firstpython.png)

输入exit()命令退出python交互环境

```python
exit()
```

## python文件形式运行

每次运行python命令都要进入python交互式命令行然后重写一遍也太麻烦了，可不可以将这些代码保存到文件中，然后下次要运行同样的代码时，直接运行该文件呢？

答案是可以的，创建一个以py为结尾的文件，然后将上面写的代码都写到这个文件中

![](http://p3609n7fk.bkt.clouddn.com/hellopy.png)

进入到hello.py这个文件所在的目录下，然后执行

```python
python hello.py
```

![](http://p3609n7fk.bkt.clouddn.com/hellopy2.png)

你会发现只输出了你好，python，其他Python语句没有执行吗？

其实其他语句同样也执行了，只是你没有通过print语句进行输出，所以没有显示到命令行中

可能有些windows的用户可能会出现下图的情况

![](http://p3609n7fk.bkt.clouddn.com/windownofile.png)

说没有找到hello.py这个文件，但是你确实是在正确的目录下的，其实这不是目录问题，观察hello.py文件的type类型栏，它是txt类型，说明其他它不是py文件，该文件完整的名称应该是hello.py.txt，只是windows系统默认是隐藏文件后缀的，也就是隐藏了txt

![](http://p3609n7fk.bkt.clouddn.com/hellopytxt.png)

要解决这个问题，首先要让windows显示隐藏文件后缀

Organize(组织)-->Folder and search options(文件夹和搜索选项)

![](http://p3609n7fk.bkt.clouddn.com/hiddentxt.png)

把Hide extensions for known file types选项的勾去除，就可以看到文件的txt后缀了，重命名文件，将txt删除，在运行python hello.py就可以运行成功了

## pycharm使用

pycharm是个专门用于编写python的编程工具，一般叫它为IDE，它的功能非常强大，有完善的代码提示功能，而且会自动缩进，非常使用python编程

可以去[pycharm官方网站](https://www.jetbrains.com/pycharm/)下载，pycharm它提供专业版和社区版，专业版是需要付费的，可以免费试用30天，而社区办是免费的，当然网上有很多破解的专业版，自行去下载，这里使用社区版就好了

打开pycharm

![](http://p3609n7fk.bkt.clouddn.com/pycharmpy.png)

点击Create New Project，创建一个新的python项目

![](http://p3609n7fk.bkt.clouddn.com/pycharmcreate.png)

我的项目路径是C:\workplace，项目名称是test，注意这里选择existing interpreter，然后将前面自己下载的python3.6导入，也就是将python3.6的路径写到Interpreter中，如果你选择了New environment using，那么pycharm会为你创建一个虚拟环境，从图中可以看出这个虚拟环境是python3.6的，其实这样pycharm会为每个项目都创建一个python虚拟环境，其实也不是不可以，只是我觉得有点麻烦，有时候多个项目其实使用的库是类似的，此时就没有必要再去创建一个新的python虚拟环境

创建一个新的python文件，名为test1的python文件

右键pytest-->New-->python

![](http://p3609n7fk.bkt.clouddn.com/createpythontest.png)

然后将上面的代码都复制到这个文件中，并为每一个计算语句都加上print输出

```python
print('你好，python')

print(100+100)  #200 加法

print(100//100) #1   地板除，结果只会留下整数

print(100/100)  #1.0 除法，结果会是浮点数

print(100*2)    #200 乘法

print(10**2)   #100 指数运算，10的二次方

print(100-10)   #90  减发
```

做完这些，右击test1这个python文件，选择run，运行该python文件

![](http://p3609n7fk.bkt.clouddn.com/runpython.png)

然后你就可以看到如下输出

```python
/Users/ayuliao/.pyenv/versions/wkpy35/bin/python /Users/ayuliao/Desktop/workplace/pytest/test1.py
你好，python
200
1
1.0
200
100
90

Process finished with exit code 0
```

## 输出与输入
从上面的代码中，其实已经可以看出，要将代码的结果显示出来，就需要使用输出语句：print()，括号内是要输出的内容

比如：

```python
print('我爱python')  #我爱python
```

也可以让print输出多个内容，比如

```python
print('我爱python', '你呢？') #我爱python 你呢？
```

逗号处，print会输出一个空格

你还可以直接在print中执行python语句，print会输出执行的结果

```python
print(100+100) #200
```

如果print()括号中是要执行的python语句，就会先执行这条python语句，然后print再将其打印出来

那如何让程序获得我们输入的内容呢？可以使用input()语句来接受你输入的内容，如下：

```python
In [8]: name = input()
ayuliao

In [9]: print(name)
ayuliao
```

上面的代码通过input()获得你的输入，然后通过print()将其输出（当然在交互式命令行中，可以不用print()也可以查看变量中的内容）

## 小结
本节介绍了如何编写一段简单的python代码，从在python交互式命令行中写，到写到一个后缀为py的文件中，再到最后使用pycharm这个成熟的python编译工具来写，同时还介绍了python中如何进行输入和输出


