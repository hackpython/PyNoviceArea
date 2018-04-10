# Python安装与pip包管理工具使用

下面分别简单的介绍如果在window、Mac、Linux下安装Python3.6

首先打开 [https://www.python.org](https://www.python.org)，选择Downloads，如果你是windows系统，就选择windows，然后点击旁边的Python3.6.4进行下载，如果你是mac，就选择Mac OSX，然后选择Python3.6.4进行下载

![](http://p3609n7fk.bkt.clouddn.com/windowandmacdownloads.png)

## Mac 安装

下载好了Python3.6.4后双击运行，就完成安装了

可以打开shell，输入python3，如果进入了python3的交互式命令行，就说明安装成功了

## window安装

因为我目前使用mac，所以就从他人教程网站上截取相应的图片进行说明

下载好Python3.6.4后(图片中是Python3.5)，同样双击运行进行安装，进入如下界面

![](http://p3609n7fk.bkt.clouddn.com/windowspython3.png)

注意选中Add Python 3.5 to PATH，只有选中了这个，你才可以在window的任何地方使用Python

?>科普一下
PATH：PATH是系统环境路径，这是什么东西？其实就是系统中的路牌，比如你安装了Python，如果你不在PATH中记录下Python在你系统中的位置，那么当系统要使用Python时就会不知道它在哪里，那么就无法使用它，所以在安装Python时你需要将Python所在的路径添加到PATH中，让系统可以在任何地方都可以通过PATH找到Python从而使用Python

为什么在Mac中没有这一步呢？其实它同样做了类似的操作，区别在于它默认就做了，不需要用户进行勾选

安装好后，你可以打开cmd，然后输入python，如果进入了Python3的交互环境，就说明安装成功

## Linux安装
Linux有不同的发行版，但是都可以通过源码的方式进行安装，请自行Google解决，我默认使用Linux都不是小白，所以我认为你有能力自己解决

## pip包管理工具
Python的强大除了语言本身的强大还有个很重要的原因就是有丰富的第三方库，几乎可以满足你所有的需求，合理的使用第三方库可以让你的编程效率大大提高，很快就可以完成一个任务，那么如何来安装第三方库呢？

?>科普一下 第三方库：对于没有任何编程经验的人来说，第三方库可能是个陌生的概念，它其实就是别人针对某个需求写好的代码，这些代码放到互联网特定的几个地方，当你遇到相同类似的需求时，就可以直接拿别人的代码来解决这个需求，不用自己再动手重写一遍，这种对已经被人解决的问题再次重写一遍代码重新解决一遍的做法在编程界称为重复造轮子。

这里就需要提到pip包管理工具，pip是一个管理第三方库的库，pip本身也是个第三方库，只是现在当你安装好Python时，自动就安装好了(如果你安装的Python没有安装好pip，你就需要自己去安装)，如果你现在需要安装某个第三库就可以通过pip来安装，这里以requests这个第三方库为例，你打开命令行，输入下面命令

```
pip install requests
```

然后pip就会帮我们去互联网上下载requests这个第三方库到我们本地，因为Python官方存放第三方库的地方在国外，所有pip默认会去国外Python官方地址那里下载你需要的第三方库，因为国情(长城防火墙)，有时候pip从国外下载第三方库会非常慢，为了解决这个问题，我们可以更换pip的下载源(所谓源就是从哪里下载)，下面我们通过豆瓣源(豆瓣是国内的，也提供相同的服务)来安装requests这个库

```
pip  install  -i  https://pypi.doubanio.com/simple/  --trusted-host pypi.doubanio.com requests
```

当然如果提示你已经安装过requests了，可以通过下面命令将安装过的第三方库删除

```
pip uninstall requests
```

如果你想看自己已经安装了那些第三方库，可以通过下面命令来查看

```
pip list --format=columns
```


科普一下
命令行：命令行其实就是与操作系统交互的一种手段，通过输入相应的命令让操作系统执行相应的操作，在windows中，命令行程序为cmd.exe，通过cmd我们除了可以调用python还可以完成其他操作，比如关闭计算机(shutdown -s -f -t)等，当然windows中的powershell也是命令行，在mac/linux中就是我们常说的shell

## 小结
本节简单的介绍了如何在不同平台上安装python，并介绍了pip包管理工具，通过本节，希望你已经在自己的电脑上安装好了python，而且学会了如何通过pip安装python第三方库，简化自己的编程







