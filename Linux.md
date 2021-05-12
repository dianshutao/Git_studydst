# Linux

## 1.发展史

C语言--------Unix------stallman-------linus-------Linux

Unix:solaris,AIX,HP-Unix

stallman:自由软件之父 		GNU

linus:Linux之父		Git

linux:redhat,centos,suse,ubuntu,fedora....

移动市场:基于linux内核,google发行了Android

​                                          苹果的底层:Unix

**[总结]**

Linux是一个内核开源的操作系统,主要应用在服务器端,作为服务器的操作系统使用

**[偏外]**

服务器的概念

## 2.安装

### 2.1 虚拟机+镜像

虚拟机:vm12

镜像:centos6.9,centos7

### 2.2 申请阿里云

略

## 3.连接服务器

只需要提供给我:ip,用户名,密码

工具:puuty,SSH,CRT,Xshell

**[附加]**

修改字体和颜色等

## 4.正式学习

### 4.1 背目录

Linux是个文件系统,它把所有的东西都当成文件,相同文件组成文件夹,不断嵌套后形成一个树状结构

常见目录:

/:根目录,相当于''我的电脑''

​	dev:device,设备目录

​	etc:配置文件目录

​	root:超管目录

​	home:普通用户的目录

​	mnt:mount,挂载

​	usr:软件的默认安装目录

​	var:软件的工作目录

​	tmp:temp,临时文件目录,我们一般做试验在这个里面做

[附加]

清自行百度,了解其他目录等(如果你有兴趣的话)

[https://www.runoob.com/linux/linux-system-contents.html]



### 4.2 了解前缀

不管你敲什么,前面都有这一堆,这个你先要认识

[root@iZwz99707cbxm1n1b9vjj7Z ~]#

整个这一堆叫shell,linux用的是bash 也叫 bash shell

按照这个理解:有其他的shell才对,unix它用CShell(cqdb%),windows:winshell

![](Linux/shell.png)

root:你当前所在的用户

​	useradd caichang

​	passwd caichang		111

切换用户:

​	1.超管切普通:su 用户名 		不用输密码

​	2.普通切超管:su -/root		  需要密码

iZwz99707cbxm1n1b9vjj7Z:机器名

~:当前用户的工作目录 

​	超管:/root

​	普通:/home/用户名

$/#:

​	$:普通权限

​	#:超管权限



### 4.3 基本命令

1.pwd:查看当前所在位置

2.cd:切换目录

​	cd .:.本层

​	cd ..:上一层		cd ../../../:返回上3层

​	相对路径/绝对路径:

​		相对路径:cd caichang    进入我所在目录下的caichang目录

​		绝对路径:cd /var			 进入/下的var目录

**[总结]**

​		1.相对和绝对都可以,只是你觉得哪种场景下而已(你要切目录时告诉你自己:1.我在哪,2.我要去哪)

​				我在哪:pwd

​				我要去哪:如果是本层下的,就用相对

​		             如果不是在本层下,就用绝对

​		 2.如何区分相对和绝对:带/的就是绝对



3.ls:查看当前目录都有哪些内容

常见参数:

​	ls -l

​	ls -la

**[附加]**

1.我们常用ll替代ls -l  (因为ll是ls -l的别名)

​	如果你想取别名:alias cai='ls -l'		取消别名:unalias cai

2.ll不能作用在unix系统中

3.我想知道还有哪些参数,linux用man命令来查手册

​	man 命令		回车键:往下找(按照英文字母顺序排序)          q:退出    quit

​	请你慢慢养成看man的习惯



### 4.4 文件系统

linux是把所有都当文件,就要学文件和文件夹的操作

操作:新建,删除,复制,粘贴,剪切,重命名,查找

#### 4.4.1 新建

文件夹:mkdir

```shell
mkdir caichang
mkdir caichang baobao fengjie
mkdir -p cai/chang/bao/zi
```

文件:touch

```shell
touch caichang
touch baobao caichang
```

#### 4.4.2 删除

文件夹:rmdir

```shell
rmdir caichang
rmdir caichang baobao
```

提醒:rmdir只能删除空文件夹,所以他几乎不用

文件:rm -rf		-r 递归		-f:强制

 

```shell
rm -rf caichang (文件夹)
rm -rf baobao (文件)
```

提醒:我们工作无论是删除文件夹还是文件都采用rm -rf 文件夹/文件均可,删除时请小心看清楚名称,别误删



#### 4.4.3 复制

文件/文件夹都是:cp,注意**.如果是文件夹,要带-r参数**

```shell
cp caichang /var    #文件
cp  -r /var/a /tmp  #文件夹
```



#### 4.4.4 剪切

文件/文件夹都是:mv

```shell
mv 原目录 现目录
mv 原文件 现目录
```

[注意]

如果是本层,表示重命名,如果是不同层,表示剪切

#### 4.4.5 查找

文件/文件夹:find

```shell
find 目录 -name '内容'
#技巧多集中在内容上,你可以自己百度搜炫的效果的查找方案
find / -name '*cai*'
```

#### 4.4.6 查看文件内容(重点)

静态:cat,more,less,head,tac

```shell
cat 文件名   #适合看小文件且不超过1屏
more 文件名  #回车 空格,不能往前看  q退出
less 文件名  #优于more可以往前看
head -n 20 文件名  #看前20行的
tac 文件名  #反着看
```



动态:tail -f 文件名.我们常常用它来看动态日志

```shell
tail -f 文件名
```

看后20行等,可以采用:tail -f -n 20 文件名(不常用)



### 4.5 压缩/解压缩

windows提供的方案:rar,zip,它是边打包边压缩

Linux不支持rar,只支持zip包

**压缩:**zip -r 名字 文件/文件夹

**解压缩**:unzip 名字

Linux打包和压缩是2个方案

**打包:tar   打包之前多少MB,打包后就多少MB,并不改变文件大小**

1.压缩:tar cvf 名字(xx.tar) 文件/文件夹

2.解压缩:tar xvf 名字(xx.tar) 

3.查看压缩包内容:tar -tf 名字(xx.tar) 

4.追加内容到压缩包:tar -rf 名字(xx.tar) 文件/文件夹

5.删除压缩包中的内容:tar --delete -f 名字(xx.tar) 文件/文件夹

**压缩:gz**

1.压缩:gzip 名字(xx.tar) 

2.解压缩:gunzip 名字(xx.tar.gz) 



**一次性既打包又压缩**

1.压缩:tar zcvf 名字(xx.tar.gz) 文件/文件夹

2.解压缩:tar zxvf 名字(xx.tar.gz) 



[注意]

**压缩和解压缩是不限定文件名后缀的,但工作中还是要写后缀,否则你根本不知道是个压缩包**



### 4.6 vi(必会)

vi可以简单理解为Linux中的记事本

vi **文件名**

**一定不能直接写vi或vi 文件夹**

**玩vi眼睛盯着左下角**,他决定了你处于什么模式

**理解:**其实vi非常符合人的习惯

1.打开我要编辑的文件  vi 文件名

2.定位到我要编辑的地方,开始准备编辑    移动后输入aio

3.编辑我要的内容   正常写数据

4.关闭我的编辑	esc

5.我开始保存退出  :wq

#### 4.6.1 模式和模式切换

![image-20210427090819187](Linux/image-20210427090819187.png)

**命令---编辑:a,i,o**

a:append 追加,在光标后进行插入

i:insert 插入,在光标前进行插入

o:other 在光标下一行插入

#### **4.6.2  末行模式技巧:**

w q !

w:write    q:quit	!:强制

工作用法:  wq  	w	q	q!

*显示行号:set number		取消行号:set nonumber*

**vi的很多技巧都集中在命令模式中,在门道我讲授最常见的,其他的可自行学习**

1.光标的纵向移动:G  nG

2.光标的横向移动:w e

3.上下左右:h,j,k,l    小键盘上下左右即可       左:删除键	右:空格

4.行首:^   行尾:$

5.复制:y		yy:复制一行		nyy:复制n行		y^:复制光标到行首		y$:复制光标到行尾

6.粘贴:p

7.删除:d		dd:删除一行		ndd:删除n行		d^:删除光标到行首		d$:删除光标到行尾

8.删除一个字符:x(先向后再向前)  主要用来做微调,非常有用

9.查找:/		n:向下查找(next)		N:向上查找		

10.撤销:u

#### 4.6.3 vim和gvim

vi是自带的,没有语法高亮等"炫"功能.我们可以通过安装vim来实现

如果你想在windows上玩vi,可以装一个gvim来玩



### 4.7 进程(必会)

#### 4.7.1 查看进程

1.ps -ef或ps aux

​	ps -ef用得更多 aux一般运维用

​	我们关注的点是,第二列;pid  进程号

2.工作往往是查是否有某一进程

```shell
[root@localhost tmp]# ps -ef | grep java
root      7709  7510  0 19:29 pts/2    00:00:00 grep java

#|:管道,类似于插入一个管子
#grep:过滤字符串,他是shell编程重要的家族
#这叫没有该java进程

[root@localhost tmp]# ps -ef | grep httpd
root      7739     1  0 19:33 ?        00:00:00 /usr/sbin/httpd
apache    7742  7739  0 19:33 ?        00:00:00 /usr/sbin/httpd
apache    7743  7739  0 19:33 ?        00:00:00 /usr/sbin/httpd
apache    7744  7739  0 19:33 ?        00:00:00 /usr/sbin/httpd
apache    7745  7739  0 19:33 ?        00:00:00 /usr/sbin/httpd
apache    7746  7739  0 19:33 ?        00:00:00 /usr/sbin/httpd
apache    7747  7739  0 19:33 ?        00:00:00 /usr/sbin/httpd
apache    7748  7739  0 19:33 ?        00:00:00 /usr/sbin/httpd
apache    7749  7739  0 19:33 ?        00:00:00 /usr/sbin/httpd
root      7751  7510  0 19:33 pts/2    00:00:00 grep httpd

#这种叫有该进程
#可以通过service httpd start来启动这个服务(centos6)

```



3. 查看实时进程:top   (有点像windows的任务管理器),只能通过ctrl+c来强退

   

#### 4.7.2 杀死进程

1.kill -9 pid(进程号,即我们查询出来的第二列)   -9:强制	   这种工作用得多

2.pkill/killall 进程名(如不知道进程名,问开发)



### 4.8 系统管理(理解)

1. 查看cpu信息:more /proc/cpuinfo

2. 查看内存信息:more /proc/meminfo

3. 内存占用:free -m

4. 硬盘占用:df -h

   windows的分区方案和linux完全是2回事,如果你有兴趣慢慢了解

5. 查看某目录下具体的各个文件/文件夹比重:du -sh *  (进入你要查看的目录再使用该命令)

6. 查看历史:history

7. 查看ip:ifconfig (centos6)

   centos7:ip addr

8. 服务:

   ​	service 服务名 状态

   ​	关闭防火墙:

```shell
	service iptables stop
```

​			如果我不知道服务名(查或问) 

​			如果状态不知道,随便敲然后会提示你都有哪些状态

​			**[提醒]**

​				centos6和centos7在防火墙在完全是2个概念,请下来自我学习7的防火墙

​				或者说centos7上都没有service这个动作,变成了systemctl这个命令



## 5 环境搭建

Linux部署(安装)软件有3种方式,每一种你必会,否则没办法上班

### 5.1 rpm安装

rpm（英文全拼：redhat package manager） 原本是 Red Hat Linux 发行版专门用来管理 Linux 各项套件的程序，由于它遵循 GPL 规则且功能强大方便，因而广受欢迎。逐渐受到其他发行版的采用。RPM 套件管理方式的出现，让 Linux 易于安装，升级，间接提升了 Linux 的适用度。

蕴含道理:

1.凡redhat这个分支下的所有发行版均采用rpm包管理方案

2.其他发行版不一定是rpm包,如:ubuntu(deb)

3.它比较容易让新人接受和安装部署



常见使用方式:

```shell
#安装
rpm -ivh xxx.rpm

#卸载
rpm -e xxx  #xxx名是要通过查才知道

#查询
rpm -ql xxx 
rpm -ql xxx | more #慢慢展示着看

#列出所有用rpm来安装的包
rpm -qa
#列出是否安装过某包
rpm -qa | grep jdk
```

案例:jdk

```shell
#1.通过各种方式拿到你要安装的rpm包shell
#2.通过软件上传到对应的服务器中
#3.执行安装 rpm -ivh jdk.....rpm
```

**[注意]**

rpm包有个非常恶心的问题:**包依赖**

演示:mysql (rpm方式)

笔记:略



### 5.2 yum安装

yum（ Yellow dog Updater, Modified）是一个在 Fedora 和 RedHat 以及 SUSE 中的 Shell 前端软件包管理器。

基于 RPM 包管理，**能够从指定的服务器自动下载 RPM 包并且安装**，可以**自动处理依赖性关系**，并且**一次安装所有依赖的软件包**，无须繁琐地一次次下载、安装。

yum 提供了查找、安装、删除某一个、一组甚至全部软件包的命令，而且命令简洁而又好记。





能够从指定的服务器自动下载:

1.默认是从官方的镜像库中去拉取.但由于受到网络影响,有可能你下载并安装会很慢

2.我们要能够切换回国内源(阿里云,163云,清华大学等)

3.如果服务器上没有这个rpm包,你就拉不动,想哭:(





常见命令:

```shell
#安装
yum install 软件名

#更新
yum update 软件名

#查找
yum search 软件名
```



切换源

```shell
#1.备份一个出来
cd /etc/yum.repos.d/
cp CentOS-Base.repo CentOS-Base.repo_bak

#2.删除CentOS-Base.repo中的内容并替换成对应的源的配置信息
#3.清理原来的yum信息:yum clean all
#4.生成新的yum仓库信息:yum makecache,如下图
#5.查看切换:yum repolist
```

![image-20210427155817859](Linux/image-20210427155817859.png)



**[注意]**

centos6已有很多国内国外源都不维护了,因此我们好不容易找到了华中科技大学的镜像源站

[http://mirrors.hust.edu.cn/help.html#centos]



案例:php,subversion

注意 -y的意义

```shell
yum install php
yum install -y subversion
```



### 5.3 源码安装

n Linux上几乎所有的软件都经过了GPL授权，因此几乎所有的软件都会提供源码。 

n 而一个软件要在Linux上执行，必须是二进制文件，因此当我们拿到软件源码后，需要将它**编译成二进制文件才能在Linux上运行。**



步骤:

1. 获取源码
2. 解压
3. 进入文件夹
4. 执行创建Makefile文件(configure脚本)
5. 编译(make),很遗憾,很多时候make不通过(编译器过老)
6. 安装(make install)



案例:nginx(反向代理服务器)

```shell
#预处理
cd /usr/local/ #进入目录
mkdir nginx    #创建nginx文件夹
cd nginx 	   #进入nginx目录

#预处理它的目的是为了在make时不出错
yum -y install gcc gcc-c++ autoconf automake
yum -y install zlib zlib-devel openssl openssl-devel pcre pcre-devel

#1.获取源码
wget https://nginx.org/download/nginx-1.9.9.tar.gz #如果你有这个包,直接拖动到目录下也可

#2.解压
tar zxvf nginx-1.9.9.tar.gz

#3.进入文件夹
cd nginx-1.9.9

#4.执行脚本
./configure --prefix=/usr/local/nginx/ --with-http_ssl_module
#执行后会有一个Makefile的文件.

#5.编译
make
#很遗憾,你会各种错,如果错,就执行如上的yum安装依赖等,装好后,删除Makefile的文件,然后重新执行第4步

#6.安装
make install

```



案例2:tomcat

```shell
#1.上传到/tmp (其他目录也可,但是tmp更好)
#2.解压
tar zxvf apache-tomcat-8.5.13.tar.gz
#3.复制到/usr/java (你复制到/usr/local下也可,只是我们这里和java保持同目录)
cp -r apache-tomcat-8.5.13 /usr/java
#4.进入/usr/java下并重命名成tomcat8080 (tomcat的默认端口是8080)
cd /usr/java
mv apache-tomcat-8.5.13 tomcat8080
#5.进入tomcat8080下的bin并启动tomcat
cd tomcat8080/bin
./startup.sh
#6.测试,启动chrome,输入:http://linux的ip:8080
```







**[备注]**

*wget* 是一个从网络上自动下载文件的自由工具,最最简单的理解:Linux自带的迅雷下载

通过./configure --help,可以看configure的详细说明

启动nginx:

- 进入nginx的sbin目录,执行:./nginx即可
- 前提:关闭防火墙 service iptables stop
- 测试:打开chrome,输入:http://linux的ip,即可

有的源码其实只需要解压后就可以用:tomcat





三种安装方式的比较:

rpm:

​	好:安装简单;不依赖网络,硬盘上有rpm包上传后就可以安

​	不好:包依赖;不能自定义安装路径



yum:

​	  好:解决了rpm的不好

​	  不好:源不好找;需要网络;如果源没有我要的版本,得切换源



源码:

​		好:完全自定义安装路径等一系列配置,甚至有的解压就可以用

​		不好:需要更新编译器,新人太麻烦了



作业:

1.完成centos6上rpm和yum的一切

2.尝试centos7上做今天的一切

3.尝试阿里云服务器上做今天的一切





## 6 Nginx+tomcat

1.nginx

*Nginx* (engine x) 是一个高性能的[HTTP](https://baike.baidu.com/item/HTTP)和[反向代理](https://baike.baidu.com/item/反向代理/7793488)web服务器.其特点是占有内存少，[并发](https://baike.baidu.com/item/并发/11024806)能力强



2.正向代理&反向代理

代理:中介

正向代理:vpn,客户端

反向代理:nginx,服务器端

参考文章:[https://www.cnblogs.com/xuepei/p/10437114.html]

[注意]

**理解正向代理和反向代理的区别**





案例:nginx+tomcat (负载均衡)

1.复制出3个tomcat,分别叫tomcat8080,8081,8082

2.分别改3个tomcat的端口(启动端口和关闭端口都要改)

端口:tomcat/conf/server.xml

22行:关闭端口			69行:启动端口

可参考:启动8080 8081 8082    关闭:8005 8006 8007

3.为了区分和能看懂我到底是哪个tomcat,我修改他的标题来区分(你改其他也可以)

vi tomcat/webapps/ROOT/index.jsp

29行:分别取名 tomcat8080 tomcat8081 tomcat8082

完全前面3个tomcat的修改,其实你已经可以分别把项目部署在不同的tomcat中



**4.修改nginx的配置文件,让他分别认识前面的tomcat**(重中之重) 他写错一个字符都不行

1.编辑nginx的配置文件:vi /usr/local/nginx/conf/nginx.conf

修改2处即可.一处是纯添加,一处是在已有的后面添加,注意名称的一致性

![image-20210428144911062](Linux/image-20210428144911062.png)



![image-20210428145021670](Linux/image-20210428145021670.png)



5.测试

启动ngxin,访问:http://linux的ip,你不断刷新,你注意看标题栏,他在8080 8081 8082之间切换









































