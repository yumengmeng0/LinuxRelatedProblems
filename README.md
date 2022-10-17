# VMware调节ubuntu分辨率
```shell
# 无法通过设置调节屏幕分辨率，使用xrandr命令调节分辨率：
xrandr
# 永久设置
xrandr --output Virtual1 --mode 1360x768
```

# [Linux常用命令大全](Linux常用命令大全.txt)

# linux下ubuntu系统设置开机默认开启小键盘
```shell
sudo apt-get install numlockx
sudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
# 在文件尾添加：
greeter-setup-script=/usr/bin/numlockx on
```

# Ubuntu 配置 sudo 时不需要输入密码
```shell
# sudo 相关的配置位于 /etc/sudoers 文件内。但这个文件不建议直接编辑，而是使用以下命令
sudo visudo

# 该命令会打开默认的编辑器编辑 /etc/sudoers 文件，并在保存时自动检查文件格式并设置到正确的文件权限。
# 进入编辑状态后，在文件最后面（划重点：一定是在文件最后面）添加以下内容：
# username   ALL=(ALL) NOPASSWD: ALL
# username改成自己的用户名

# NOPASSWD 表示不需要输入密码，后面的 ALL 表示所有命令。
# 也就是说，用户在执行 所有的 sudo 命令时均不需要输入密码。
# 如果要设置指定命令无需输入密码，只需要把最后面的 ALL 替换为具体命令即可
```
    ————————————————
    版权声明：本文为CSDN博主「MiddleWeek」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
    原文链接：https://blog.csdn.net/MiddleWeek/article/details/121314368

# 在当前目录下打开终端
```shell
sudo apt-get install nautilus-open-terminal
nautilus -q
```

#  解压.tar.gz\tar.xz文件：

```shell
tar -zxvf   xx.tar.gz
tar -xvf archive.tar.xz
```

# SSH
```shell
# 在linux上使用github：https://www.jianshu.com/p/599ae69b57c5
    
ssh-keygen -t rsa -C "your_email@youremail.com" 
# ERROR: You're using an RSA key with SHA-1, which is no longer allowed. Please use a newer client or a different key type.
ssh-keygen -t ed25519 -C "your_email@example.com"
cat ~/.ssh/id_rsa.pub
```

# Ubuntu安装JDK并配置环境变量

```shell

# http://www.oracle.com/technetwork/java/javase/downloads/index.html

# 解压到当前目录
tar -zxvf jdk-8u171-linux-x64.tar.gz 
# 重命名
mv jdk-8u171-linux-x64 jdk1.8
# 将解压后的文件移动到指定目录
mv jdk1.8 /usr/lib/java

# 使用全局设置方法，它是所有用户的共用的环境变量
sudo gedit ~/.bashrc

# 然后把如下命令复制到最底部

# export JAVA_HOME=后面要填写自己解压后的jdk的路径

export JAVA_HOME=usr/lib/jvm/jdk-11
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib 
export PATH=${JAVA_HOME}/bin:$PATH


source ~/.bashrc

```

# Ubuntu中查找软件安装位置详解

```shell
 
# 1.执行该程序
# 	直接执行程序，有时候执行时会显示出位置。
# 	尝试使用type，如：type google-chrome
# 2.在进程中找
# 	显示所有进程名：
ps -e
# 过滤命令：
ps aux|grep 软件名
# 3.用find或whereis命令（查看软件安装的所有路径）
# 直接找的整个硬盘；
find / -name filename
# 什么都会找出来；
locate filename
# 能找到以前删除的。
whereis filename
# 4.which查询运行文件所在路径
#	如果只查询文件的运行文件所在目录，命令：
which google-chrome
#	结果会显示：
	/usr/bin/google-chrome
# 5.其他
# 如果知道使用 apt-get install 命令安装的软件。则：
# 显示包含此软件包的所有位置；
dpkg -S softwarename 
# 显示安装路径。
dpkg -L softwarename 
# 查看软件版本。
aptitude show softearename或dpkg -l softwarename

```

# 查看监听端口

```
# 查看监听端口
netstat -lunpt

# ping ip port
tcping ip port

```
     
# 在Linux下安装Python时出现一个错误：
zipimport.ZipImportError: can't decompress data; zlib not available

## 解决方式：
```shell
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl
```

# python默认版本修改
```
update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1  
update-alternatives --install /usr/bin/python python /usr/bin/python3.4 2
```
# jdk
``` shell

su root
vi /etc/profile

export JAVA_HOME=/usr/local/java/jdk-11.0.16.1
export JRE_HOME=${JAVA_HOME}/jre
export CLASS_PATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH

# source /etc/profile 使新的环境变量生效
```


# 查看进程
```shell
# 查看所有进程的详细信息
ps aux
#查询进程名对应的进程信息。
ps a | grep 进程名
```

# 关闭进程

```shell
#关闭进程。
kill pid
# 强制关闭进程
kill -9 -pid
# 更加强制关闭进程
kill -KILL pid

# 当然，我们也可以通过进程名command来关闭进程。执行下面任一指令即可关闭该进程：
#关闭进程。
pkill 进程名 

#关闭同一进程组内的所有进程。
killall 进程名 
————————————————
版权声明：本文为CSDN博主「振华OPPO」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_42257666/article/details/124197052

```

# SQLYog 连接服务器中出现的问题

## 端口3306在Ubuntu服务器上似乎已关闭，SQLYog 2003错误

问题在于服务器仅在内部进行侦听。
从/etc/mysql/my.cnf删除行bind-address 127.0.0.1解决了该问题。
较新版本的Ubuntu(≥16.04)在/etc/mysql/mysql.conf.d/mysqld.cnf中可能有此行。


## mysql 错误代码1130

解决方法：

1、 改表法：
可能是你的帐号不允许从远程登陆，只能在localhost。这个时候只要在localhost的那台电脑，登入mysql后，更改 “mysql” 数据库里的 “user” 表里的 “host” 项，从“localhost”改称”%”mysql -u root -p

```shell
    mysql>use mysql;
    mysql>update user set host = ‘%’ where user =’root’;
    mysql>flush privileges;
    mysql>select host,user from user where user=’root’;
```

现在就可以连接了！

2、 授权法：

例如，你想root使用root从任何主机连接到mysql服务器的话。GRANT ALL PRIVILEGES ON *.* TO ‘root’@‘%’ IDENTIFIED BY ‘root’ WITH GRANT OPTION;

如果你想允许用户root从ip为192.168.1.3的主机连接到mysql服务器，并使用root作为密码GRANT ALL PRIVILEGES ON *.* TO ‘root’@‘192.168.1.3’ IDENTIFIED BY ‘root’ WITH GRANT OPTION;
————————————————
版权声明：本文为CSDN博主「web_15534274656」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/web_15534274656/article/details/126493936
