# Python版本控制与虚拟环境2

上一章，讲解了windows中python的版本控制和虚拟环境的使用，本章来讲解mac\linux上python版本控制与虚拟环境的使用，因为mac和linux的使用方式几乎一样，所以放在一起讲解

## Pyenv进行版本控制

为了解决python多版本带来的问题，python版本切换工具—pyenv应运而生，pyenv不支持windows，只能在mac或linux上使用

如果你是mac系统，可以直接通过[Homebrew](https://brew.sh/)来安装pyenv

```
$ brew update
$ brew install pyenv
```

Homebrew是Mac下的包管理工具，可以通过Homebrew来安装你需要的应用

如果你是linxu系统，通过下面方法来安装pyenv

首先通过git命令去github上下载pyenv，然后再修改环境变量

```
$ git clone https://github.com/yyuu/pyenv.git ~/.pyenv     #使用 git 把 pyenv 下载到家目录
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc     #然后需要修改环境变量，使用 Bash Shell 的输入
$ echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(pyenv init -)"' >> ~/.bashrc     #最后添加 pyenv init
$ exec $SHELL -l     #输入命令重启 Shell,然后就可以重启pyenv
```

安装完成后，就可以使用pyenv了，通过下面命令来查看pyenv可以支持安装那些python版本

```
$ pyenv install --list
```

pyenv安装某个版本的python，比如这里我安装python3.6.2

```
$ pyenv install 3.6.2
```

因为国情，所以安装速度会非常非常慢，而且很容易失败，可以通过下面方法来实现快速安装

首先运行安装命令，获得该版本python的下载地址

```
$ pyenv install 3.6.2
```

![](http://p3609n7fk.bkt.clouddn.com/python362download.png)

然后通过其他方式下载，比如迅雷，几秒就下载完成了

![](http://p3609n7fk.bkt.clouddn.com/xunleidownload.png)

如果你没有迅雷，可以通过wget命令进行安装

```
wget https://www.python.org/ftp/python/3.6.2/Python-3.6.2.tar.xz
```

下载好后，将安装包移动到**~/.pyenv/cache/**目录中，一开始cache目录是不存在的，你需要通过mkdir命令创建

```
mkdir  ~/.pyenv/cache
```

将Python-3.6.2.tar.xz移动到 ~/.pyenv/cache，使用mv命令

```
mv Python-3.6.2.tar.xz ~/.pyenv/cache
```

然后重新执行pyenv安装命令，只是加多了一个 -v 参数，加了该参数，pyenv就会先去cache目录下查找有没有对应的安装包，如果有就直接通过该安装包进行安装

```
pyenv install 3.6.2 -v
```

![](http://p3609n7fk.bkt.clouddn.com/pyenvinstallpy362.png)

从图中可以发现，已经没有下载过程了，直接进行安装，如果没有任何意外，那就安装成功了

如果你在安装时遇到问题，可以去 [https://github.com/pyenv/pyenv/wiki/Common-build-problems](https://github.com/pyenv/pyenv/wiki/Common-build-problems)上找相应的解决方法，几乎所有问题都有相应的解决方法

当我们把3.6.2安装好后，最好先刷新一下pyenv的数据库，让pyenv可以找到最新安装的3.6.2

```
$ pyenv rehash
```

通过下面命令可以查看系统中安装了了哪些python版本

```
$ pyenv versions
```

从下图可以看到我们刚刚安装好的3.6.2
![](http://p3609n7fk.bkt.clouddn.com/pyenvversions.png)

仔细观察上图，可以发现第一行是system，它就是系统本身的python，然后还可以发现3.6.3前有个*号，说明当前python环境使用的事3.6.3这个环境

可以通过下面命令切换全局Python版本，切换到python3.6.2版本上

```
pyenv global 3.6.2
```

如果你要卸载某个版本的python，可以通过下面命令，弹出的提示输入y则可

```
删除python3.6.2
pyenv uninstall 3.6.2
pyenv: remove /Users/ayuliao/.pyenv/versions/3.6.2? y
```

更新pyenv

```
pyenv update
```

## pyenv-virtualenv创建python虚拟环境

pyenv-virtualenv基于pyenv，是pyenv的一个插件，所以使用pyenv-virtualenv的前提是安装了pyenv，pyenv-virtualenv作用就是可以基于pyenv安装好的python版本来创建相应python版本的虚拟环境

Mac下安装，通过Homebrew可以直接安装

```
$ brew install pyenv-virtualenv
```

然后添加下面命令到你shell的配置文件中，如果不添加到配置文件中，那么下次打开shell，又要运行一次下面的命令

```
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

我Mac上使用的oh-my-zsh这个shell终端，所有我将这两行命令添加到~/.bash_profile中，然后重启一下oh-my-zsh终端就可以了

![](http://p3609n7fk.bkt.clouddn.com/bash_profile.png)

linux下安装pyenv-virtualenv，先通过git命令将pyenv-virtualenv安装到~/.pyenv/plugins/目录下

```
$ git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
```

通过下面的命令就可以将pyenv的virtualenv-init添加到你的shell

```
$ echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
```

然后重启shell，让它重新加载自己的配置文件，让我们可以启用pyenv-virtualenv

```
$ exec "$SHELL"
```

### 使用pyenv-virtualenv

通过下面命令创建python3.6.3的虚拟环境，名为envpy3

```
pyenv virtualenv 3.6.3 envpy3
```

激活envpy3虚拟环境

```
pyenv activate envpy3
```

退出虚拟环境

```
pyenv deactivate
```

查看系统中创建了多少个虚拟环境

```
pyenv virtualenvs
```

卸载虚拟环境

```
pyenv uninstall envpy3
```

如果pyenv没有安装某个版本的python，你却要通过pyenv-virtualenv来创建该版本python对应的虚拟环境，那么就会先执行pyenv安装该版本python的流程，才会通过pyenv-virtualenv来创建虚拟环境，建议自己手动通过迅雷来安装某版本的python，然后再创建其虚拟环境，不然下载速度会非常慢

## 小结
本节介绍了如何在linux、mac下进行python的版本控制和创建独立的python虚拟环境，如果你是电脑新手，这节内容可能会显得有点复杂，如果遇到了文章讲解之外的情况，可以自行在网上搜索解决方法

