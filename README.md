# VMware调节ubuntu分辨率

    无法通过设置调节屏幕分辨率，使用xrandr命令调节分辨率：
    xrandr
    永久设置
    xrandr --output Virtual1 --mode 1360x768

# [Linux常用命令大全](Linux常用命令大全.txt)

# linux下ubuntu系统设置开机默认开启小键盘

    sudo apt-get install numlockx
    sudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
    在文件尾添加：
    greeter-setup-script=/usr/bin/numlockx on

# Ubuntu 配置 sudo 时不需要输入密码

    sudo 相关的配置位于 /etc/sudoers 文件内。但这个文件不建议直接编辑，而是使用以下命令

    sudo visudo

    该命令会打开默认的编辑器编辑 /etc/sudoers 文件，并在保存时自动检查文件格式并设置到正确的文件权限。
    进入编辑状态后，在文件最后面（划重点：一定是在文件最后面）添加以下内容：

    username   ALL=(ALL) NOPASSWD: ALL
    
    username改成自己的用户名

    NOPASSWD 表示不需要输入密码，后面的 ALL 表示所有命令。
    也就是说，用户在执行 所有的 sudo 命令时均不需要输入密码。
    如果要设置指定命令无需输入密码，只需要把最后面的 ALL 替换为具体命令即可
    ————————————————
    版权声明：本文为CSDN博主「MiddleWeek」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
    原文链接：https://blog.csdn.net/MiddleWeek/article/details/121314368

# 在当前目录下打开终端
    sudo apt-get install nautilus-open-terminal
    nautilus -q


#  解压.tar.gz文件：tar -zxvf   xx.tar.gz
#   tar -xvf archive.tar.xz

# SSH

在linux上使用github：https://www.jianshu.com/p/599ae69b57c5
    
    ssh-keygen -t rsa -C "your_email@youremail.com" // ERROR: You're using an RSA key with SHA-1, which is no longer allowed. Please use a newer client or a different key type.
    ssh-keygen -t ed25519 -C "your_email@example.com"

     cat ~/.ssh/id_rsa.pub
     
 # 在Linux下安装Python时出现一个错误：zipimport.ZipImportError: can't decompress data; zlib not available
 
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl

# python默认版本修改

update-alternatives --install /usr/bin/python python /usr/bin/python2.7 1  
update-alternatives --install /usr/bin/python python /usr/bin/python3.4 2

