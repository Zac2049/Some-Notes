```csharp
===================目录操作========================
mkdir: 创建目录
　　-p : 递归的创建目录 也就是可以创建多层目录
　　一次创建多个目录： mkdir {a,b,c,d,e,f}
　　一次创建 a b c d e f多个目录。
rmdir：删除一个空文件夹
cp：复制文件或者文件夹

　　-a =-pdr
　　-p 同时复制文件属性，比如修改日期
　　-d 复制时保留文件链接
　　-r: 复制文件夹时,递归复制子文件夹
　　-l 不复制，而是创建指向源文件的链接文件，链接文件名由目标文件给出。   
　　note:可以在拷贝的同时重命名
mv：移动文件或者文件夹，可以在移动的时候重命名

rm ：删除文件或者文件夹
　　-r：递归删除
　　-f：强制删除 即没有提醒

======================文件处理命令==============================
ls :查看文件
　　-l 以列表形式查看
　　-h 以一种人性化的方式查看，也是文件的大小以合适的单位显示
　　-a 查看所有文件，包括隐藏文件
　　-i 显示出文件的i节点号
touch 文件名：创建文件 可以一次创建多个文件，以空格隔开

cat :查看文件内容 
　　-n:带行号
tac:反向显示文件内容

more：分页查看文件内容
　　进入浏览模式后：
　　f或者空格：下一页
　　enter：一行一行往下翻
　　q:退出

less:查看文件内容 
　　空格翻页
　　回车换行
　　pageup：上一页
　　pagedown：下一页
　　上箭头：向上翻
　　下箭头：向下翻
　　/搜索词 n向下找

head -n 文件名 :查看文件前n行。缺省-n显示前10行
tail -n 文件名 ：查看文件的末尾几行
　　-f :动态显示文件末尾内容

ln:链接命令
　　-s创建软连接
　　硬链接和cp -p的区别是硬链接会同步更新
　　源文件如果丢失，硬链接依然存在。
　　硬链接和源文件的i节点相同。
　　硬链接不能夸分区，软连接可以跨分区。
　　硬链接不可以链接目录，链接可以
　　软连接文件具有的权限是ugo都是rwx

====================权限管理命令==============
chmod:修改文件或目录的权限，只有root和所有者可以更改
　　[{ugoa}{+-=}{rwx}] [文件或目录] 
　　[mode=421] [文件或目录]
　　-R 递归修改
　　权限的数字表示：
　　r->4
　　w->2
　　x->1

　　例：chmod u+x a.txt
　　　　chmod g+w,o-r a.txt //同时做多个权限的修改
　　　　chmod g=rwx a.txt
　　　　chmod 640 a.txt
　　　　chmod -R 777 testdir //把目录和下面所有文件的权限

　　　　　　　　　　　　针对文件　　 　　　　 针对目录
　　　　r　　 读权限 　　 可以查看文件内容　　  可以列出目录中的内容
　　　　w 　  写权限 　　 可以修改文件内容 　　 可以在目录中创建、删除文件
　　　　x 　   执行权限      可以执行文件 　　　　 可以进入目录

chown:更改文件所有者，只有root可以更改
　　chown root a.txt//把a.txt更改为root所有

chgrp:更改所属组
　　chgrp lambrother fengjie //把fengjie的所属组更改为lambrother

umask -S:查看创建文件的缺省权限，即默认权限
umask 023:修改文件的缺省权限为777-023=754。即rwxr-xr--

 

=====================文件搜索命令========================================
find:搜索制定范围内的文件
　　find [搜索范围] [匹配条件]
　　-name 按文件名搜索
　　-iname 根据文件名查找，不区分大小写
　　-size +n大于 -n小于 n等于 这个n是数据块，在Linux中一个数据块是512字节大小
　　-user 根据所有者查找
　　-group 根据所属组查找
　　根据文件属性查找：
　　　　-amin 访问时间 access
　　　　-cmin 根据文件属性被修改的时间 change
　　　　-mmin 根据文件内容被修改的时间 modify
　　例： find /etc -cmin -5 :查找/etc目录下五分钟内被修改过属性的文件和目录

　　-a 两个条件同时满足
　　　　find /etc -size +10 -a -size -50
　　-o 两个条件满足一个即可

　　-type 
　　　　f 文件 d 目录 l软连接文件
　　-inum 根据i节点查找

　　对找到的结果进行操作
　　　　-exec或者-ok 命令 {} \;
　　　　例如：
　　　　　　find /etc -name init* -exec ls -l {} \; 对找到的文件名按列表查看

　　find /etc -name init :搜索目录/etc下面所有的init文件，精确匹配，包括子目录中的init文件
　　find / -size +204800 搜索大于100M的文件

locate:(查找速度非常快，因为它维护了一个文件库。缺点就是新建立的文件没有很快收录到文件库)
　　locate 文件名
　　updatedb 更新locate的文件资料库 文件资料库不收录/tmp下的文件
　　-i 不区分大小写

which :查找命令的目录以及别名
　　which 命令

whereis :搜索命令所在目录及帮助文档路径。

grep:在文件中搜寻字符串匹配的行并输出，多个文件以空格隔开。
　　-i不区分大小写
　　-v排除指定字符串
　　-E 以正则表达式的方式搜索
　　-F 以普通文本的方式搜索
　　-n 显示搜索到的内容在文件中的行号。

==================帮助命令======================
man：查看命令或者配置文件的帮助信息
　　man 命令/配置文件
　　在手册里面，可以输入/要查找的str
　　man ls
　　man services
　　man fstab //直接输入配置文件的名字，而不需要使用绝对路径 重点查看name选项和配置文件的格式。
　　如果一个命令即使命令又是配置文件，那么可以使用一个序号进行区分，比如：
　　man 1 passwd 查看命令passwd的帮助
　　man 5 passwd 查看配置文件passwd的帮助

whatis 命令：得到命令的简要信息

apropos 配置文件名：查看配置文件的简短信息

命令 --help：查看命令的选项。

help 命令：查看shell内置命令的帮助信息。 shell内置命令是没有命令路径。不能使用man查看帮助。

===================用户管理命令==========================================
useradd: 添加用户
　　useradd 用户名

passwd: 修改用户密码
　　passwd 用户名 不加用户名直接更改自己的密码

who:查看当前的账户 显示的格式为： 登录用户名 登录终端（tty:本地登录 pts:远程终端） 登录时间 ip地址

　　w:查看更详细的用户登录信息。


=====================================压缩解压缩命令============================
.gz格式
　　压缩：gzip 文件名 只能压缩文件不能压缩目录，压缩完源文件也不见了
　　解压缩：gunzip/gzip -d 压缩包名称

tar:
　　-zcvf 压缩后文件名 打包的目录 :生成.tar.gz文件 注：这个命令先用tar归档，然后把归档的包压缩成.gz
　　-zxvf 要解压的文件名 ：解压缩.tar.bz2的文件

　　-jcvf 压缩后的文件名 打包的目录：生成.tar.bz2 注：这个命令先用tar归档，然后把归档的包压缩成.bz2
　　-jxvf 要解压的文件名 :解压.tar.bz2的文件

zip:
　　zip -r 压缩生成的文件名 要压缩的目录
　　zip 压缩生成的文件名 要压缩的文件。

unzip:
　　unzip 要解压缩的文件

bzip2:
　　bzip2 -k 要压缩的文件名 -k选项：保留源文件
　　bunzip2 -k 要解压的文件名 -k选项：保留压缩包

 

===============网络命令==========================
write:给在线用户发送信息，用户不在线不行。以Ctrl+D保存
　　write 用户名

wall:给所有用户名发送信息
　　wall 要发送的信息

ping:测试网络连通性

　　ping ip地址 
　　-c 要ping的次数

ifconfig:
　　直接回车查看当前网卡信息
　　ifconfig 网卡名 ip地址 临时修改网络ip
　　　　ifconfig th0:0 192.168.1.100 netmask 255.255.255.0
　　　　　　给th0这个网卡新添加一个ip
　　　　ifconfig eth0:0 down
　　　　ifconfig eth0:0 up
ifdown th0
　　禁用th0这块网卡

ifup th0
　　开启th0这块网卡

mail:邮件命令
　　mail 要发送的用户名
　　mail 直接回车：查看命令
　　　　help :查看支持的命令格式
　　　　输入序列号：查看邮件详细内容
　　　　h: 回到邮件列表
　　　　d 序列号：删除序列号对应的邮件

last:统计计算机所有用户登录的时间信息，以及重启信息
lastlog:所有用户最后一次登录的时间
　　-u 用户的uid 查看指定用户的登录信息。

traceroute:显示数据包到主机间的路径
　　traceroute 要探测的地址.
　　-n 使用ip而不使用域名

nslookup www.baidu.com
　　查看百度的ip地址

netstat:显示网络相关信息
　　-t :tcp协议
　　-u :udp协议
　　-l:监听
　　-r:路由
　　-n:显示ip地址和端口号

　　netstat -tlun:查看本机监听的端口
　　netstat -an:查看所有的监听信息
　　netstat -rn ：查看路由表，即网管

wget 文件地址
　　下载文件

service network restart:重启网络服务。

telnet 域名或ip
　　远程管理与端口探测
　　如： telnet 192.168.2.3:80
　　　　探测192.168.2.3是否开启了80端口

mount:挂在命令
　　mount -t iso9660 /dev/sr0 /mnt/cdrom :把sr0挂在到cdrom

==============关机重启命令====================

shutdown:这个关机命令更安全一些，不推荐使用其他关机命令。
　　-h：关机
shutdown -h now shutdown -h 20:30
　　-r:重启 
shutdown -r now 
　　-c:取消上次的关机命令

重启：
　　init 6
　　reboot

关机：
　　init 0
　　poweroff

　　系统运行级别：
　　　　0 关机
　　　　1 单用户 类似windows安全模式
　　　　2 不完全多用户，不含nfs服务
　　　　3 完全多用户
　　　　4 未分配
　　　　5 图形界面
　　　　6 重启
　　可以通过查看/etc/inittab来查看系统启动的运行级别
　　runlevel:查看当前的运行级别
　　init n:设置系统运行级别

logout:退出当前用户，返回到登录界面

 

==============其他小技巧==========
\命令名字 :使用原始的命令
　　比如：
　　　　ls 实际上是ls --color auto
　　　　\ls 就是原始的ls


=============================================
一、软件包分类
　　源码包
　　　　脚本安装包
　　特点：
　　　　1. 开源
　　　　2. 可以自由选择所需的功能
　　　　3. 软件是编译安装，所以更加适合自己的系统，更加稳定也效率更高
　　　　4. 卸载方便，即可以直接删除文件夹。
　　缺点：
　　　　1. 安装过程步骤较多，尤其安装较大的软件集合时，容易出现错误
　　　　2. 编译时间较长，安装毕二进制安装时间长
　　　　3. 因为是编译安装，安装过程中一旦报错新手很难解决


　　二进制包(RPM包、系统默认包)
　　　　优点：
　　　　　　1. 包管理系统简单，只通过几个命令就可以实现包的安装、升级、查询和卸载
　　　　　　2. 安装速度比源码包安装快的多
　　　　缺点：
　　　　　　1. 经过编译，不再可以看到源代码
　　　　　　2. 功能选择不如源码包灵活
　　　　　　3. 依赖性

=============rpm命令管理-包命名与依赖性=======================================
1. RPM包命名原则
　　httpd-2.2.15-15.el6.centos.l.i686.rpm
　　　　httpd 软件包名
　　　　2.2.15 软件版本
　　　　15 软件发布的次数
　　　　el6.centos 适合的Linux平台
　　　　i686 适合的硬件平台
　　　　rpm rpm包扩展名
　　　　如果名字里有noarch,则表示所有平台都可以。

2、 rpm包依赖性
　　　　树形依赖： a->b->c 从后往前安装所依赖的包。
　　　　环形依赖： a->b->c->a 解决办法：一次性安装三个包
　　　　模块依赖：模块依赖查询网站 ：www.rpmfind.net 一般以.so.数字结尾的依赖包，是库依赖包，只需要安装包括这个库的软件就可以自动安装好这个所需的库依赖包

包全名：操作的包是没有安装的软件包时，使用包全名，而且要注意路径。安装、升级时用
包名 ：操作已经安装的软件包时，使用包名。是搜索/var/lib/rpm中的数据库。一般查询，卸载时用

3. rpm安装：
　　rpm-ivh 包全名
　　　　-i(install) 安装
　　　　-v(verbose) 显示详细信息
　　　　-h(hash) 显示进度
　　　　--nodeps 不检测依赖性 一般都必须要检测

4. rpm包升级：
　　rpm -Uvh 包全名
　　　　-U(upgrade) 升级
　　　　-h

5. rpm -e 包名
　　-e(erase) 卸载
　　--nodeps 不检查依赖性

6. 查询是否安装
　　rpm - q 包名 :查询包是否安装
　　　　-q(query) 查询
　　　　-a(all) 所有
　　　　-i(information) 查询软件信息
　　　　-p(package) 查询未安装包信息
　　rpm -ql 包名：查询包中文件安装位置(list) 注：包的安装路径在包生成的时候就确定了
　　rpm -qlp 包全名：查询未安装包安装时会安装在哪里。
　　rpm -qf 系统文件名 ：查询系统文件属于哪个rpm包 注：系统文件名必须是通过安装哪个包生成的文件
　　　　-f:查询系统文件属于哪个包
　　rpm -qR 包名 查询已安装软件包的依赖性
　　　　-r: 查询软件包的依赖性(requires)
　　rpm -qRp:查询未安装包的依赖性
　　　　-p: 查询未安装包的依赖性

　　　　例如：
　　　　　　rpm -qa | grep httpd 查询所有Apache的包

7. rpm包校验
　　rpm -V 已安装的包名 ：如果没有提示则表示没有被修改过
　　　　-V 校验指定rpm包中的文件(verify)
　　　　校验值的含义：
　　　　　　S:文件大小是否改变
　　　　　　M:文件的类型或文件的权限(rwx)是否被改变
　　　　　　5：文件MD5校验和是否改变(可以看成文件内容是否改变)
　　　　　　D:设备的中，从代码是否改变
　　　　　　L:文件路径是否改变
　　　　　　U:文件的属主(所有者)是否改变
　　　　　　G:文件的属组是否改变
　　　　　　T:文件的修改时间是否改变

8. rpm包中文件提取：
　　rpm2cpio 包全名 | \
　　cpio -div .文件绝对路径

　　rpm2cpio:讲rpm包转换为cpio格式的命令 
　　\表示命令没有输完,在下一行继续输入
　　cpio:是一个标准工具，它用于创建软件档案文件和从档案文件中提取文件
　　cpio 选项 <[文件|设备]
　　　　-i copy-in模式，还原
　　　　-d:还原时自动新建目录
　　　　-v:显示还原过程

　　例如：
　　　　rpm -qf /bin/ls #查看ls命令属于哪个包
　　　　mv /bin/ls /tmp #将ls命令移走
　　　　rpm2cpio /mnt/cdrom/Packages/coreutils-8.4-19.el6.i686.rpm | cpio -idv ./bin/ls #提取rpm保重ls命令到当前目录的/bin/ls下
　　　　cp /root/bin/ls /bin/ #把ls命令复制到/bin/目录，修复文件丢失

 

yum在线管理：
一、 ip地址配置
第1步：setup:使用图形界面配置ip地址
第2步：vi/etc/sysconfig/network-scripts/ifcfg-eth0 把ONBOOT="no"改为ONBOOT="yes" #启动网卡
第3步：service network restart :重新启动网络服务。

二、网络yum源
1. yum源位置：/etc/yum.repos.d/CentOS-Base.repo,这个是默认的网络yum源
　　[base]    容器名称，一定要放在[]中
　　name  容器说明，可以自己随便写
　　mirrorlist    镜像站点，这个可以注释掉
　　baseurl   我们的yum源服务器的地址，默认是CentOS官方的yum源服务器，是可以使用的，如果你觉得慢可以改成你喜欢的yum源地址
　　enabled   此容器是否生效，如果不写或写成enable=1都是生效，写成enable=0就是不生效
　　gpgcheck  如果是1是指rpm的数字证书生效，如果是0则不生效
　　gpgkey    数字证书的公钥文件保存位置。不用修改。

2. yum命令
　　yum list :获取服务器上所有可用的软件的列表
　　yum search 关键字：搜索服务器上所有和关键字相关的包
　　yum -y install 包名：安装软件包
　　　　install:安装
　　　　-y:自动回答yes
　　yum -y update 包名：升级软件包
　　　　update:升级
　　　　-y:自动回答yes
　　　　如果没有包名，就会升级所有的软件包，包括Linux内核。慎用
　　yum -y remove 包名
　　　　remove:卸载
　　　　-y:自动回答yes
　　　　注：yum会自动卸载依赖包，而很有可能这个依赖包也被别的包依赖，所以很危险，慎用。

　　yum grouplist:列出所有可用的软件组列表
　　yum groupinstall 软件组名：安装指定软件组，组名可以由grouplist查询出来 注：如果查询出来的软件组名中间有空格，要使用""引起来。
　　yum groupremove 软件组名：卸载指定软件组

3. 光盘yum源
　　1) 挂在光盘 mount /dev/sr0 /mnt/cdrom 
　　2) 让网络yum源文件失效
　　　　cd /etc/yum.repos.d/
　　　　mv CentOS-Base.repo CentOS-Base.repo.bak
　　　　mv CentOS-Debuginfo.repo CentOS-Debuginfo.repo.bak
　　　　mv Centos-Vault.repo Centos-Vault.repo.bak
　　3) 修改光盘yum源文件
　　　　vim CentOS-Media.repo
　　　　[c6-media]
　　　　name=CentOS-$releaserver -Media
　　　　baseurl=file:///mnt/cdrom 
　　　　#地址为你自己的光盘挂载地址
　　　　#   file:///media/cdrom/
　　　　#   file:///media/cdrecorder/
　　　　#注释这两个不存在的地址
　　　　gpgcheck=1
　　　　enabled=1 #把enabled=0改为enabled=1，让这个yum配置文件生效
　　　　gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6

　　　　注意：注释配置行的时候，#符号一定要写在开头，不要随便在配置文件某一行后面加注释，也不要随便加空格。

源码包管理
　　1. 区别
　　　　安装之前的区别：概念上的区别
　　　　安装之后的区别：安装位置不同

　　2. rpm包安装位置(大多数)
　　　　/etc/   配置文件安装目录
　　　　/usr/bin/   可执行的命令安装目录
　　　　/usr/lib/   程序所使用的函数库保存位置
　　　　/usr/share/doc  软件的基本使用书册保存位置
　　　　/usr/share/man/ 帮助文件保存位置    
　　3. 源码包安装位置
　　　　安装在指定位置当中，一般是
　　　　/usr/local/软件名/ 
　　4. 安装位置不同带来的影响
　　　　rpm包安装的服务可以使用系统服务管理命令(service)来管理
　　　　例如rpm包安装的Apache的启动方法是：
　　　　/etc/rc.d/init.d/httpd start 注：服务的安装路径一般在：/etc/rc.d/init.d下
　　　　service httpd start 注：service命令是红帽的专用命令,只能管理rpm包安装的服务
源码包安装过程
　　1. 安装准备
　　　　安装C语言编译器 gcc
　　　　下载源码包
　　　　http://mirror.bit.edu.cn/apach/httpd/   
　　2. 安装注意事项
　　　　源代码保存位置：/usr/local/src/
　　　　软件安装位置： /usr/local/
　　　　如何确定安装过程报错：
　　　　　　安装过程停止并出现error、warning或no的提示  
　　3. 源码包安装过程
　　　　1)下载源码包
　　　　2)解压缩下载的源码包
　　　　3)进入解压缩目录 注：里面有个INSTALL是系统安装的步骤说明
　　　　4)./configure 软件配置与检查
　　　　　　定义需要的功能选项
　　　　　　检测系统环境是否符合安装要求
　　　　　　把定义好的功能选项和检测系统环境的信息都写入Makefile文件，用于后续的编辑。
　　　　./configure --prefix=/usr/local/apache2 ：定义安装位置 
　　　　5)make :编译
　　　　　　如果前面有错误，则使用make clean命令清楚编译产生的临时文件
　　　　6)make install:编译安装
　　4. 源码包的卸载
　　　　不需要卸载命令，直接删除安装目录即可。不会遗留任何垃圾文件

脚本安装
　　1. 脚本安装包
　　　　脚本安装包并不是独立的软件包类型，常见安装的是源码包
　　　　是人为把安装过程写成了自动安装的脚本，只要执行脚本，定义简单的参数，就可以完成安装
　　　　非常类似于windows下软件的安装方式
　　2. Webmin的作用
　　　　Webmin是一个基于web的Linux系统管理界面，你就可以通过图形化的方式
　　　　设置用户账号、Apache，DNS、文件共享等服务。
　　3、 webmin安装过程
　　　　1) 下载软件
　　　　　　http;//sourceforge.net/projects/webadmin/files/webmin/
　　　　2) 解压缩，并进入解压缩目录
　　　　3) 执行安装脚本 ./setup.sh

 

其他命令

du -sh 文件名

ps 静态查看系统进程，系统默认安装
　　ps -aux 使用BSD语法查看所有进程
　　ps -ef 标准语法查看所有进程
　　　　UID 程序被该 UID 所拥有
　　　　PID 就是这个程序的 ID 
　　　　PPID 则是其上级父程序的ID
　　　　C CPU 使用的资源百分比
　　　　STIME 系统启动时间
　　　　TTY 登入者的终端机位置
　　　　TIME 使用掉的 CPU 时间。
　　　　CMD 所下达的指令为何
　　ps -aux --sort -pcpu,-pmem
　　　　根据CPU占用情况和内存占用情况来显示进程
　　watch -n 1 'ps -aux --sort -pcpu,-pmem'
　　　　每隔1秒监控一次进程情况

top 动态查看系统的状态

lsof -Pti :8000
　　通过端口号获得进程pid

kill -9 pid
　　杀死指定pid的进程，强行杀死。

history
　　查看历史命令

执行历史命令
　　!! 执行上一条命令
　　!n 执行历史命令的中第n条
　　!-n 执行导数第n条
　　!string 执行以string开头的历史命令行
　　!?string? 执行包含string的历史命令行


alias 
　　给命令起别名

　　alias 命令='别名'
　　alias -p 查看已存在的别名

unlias 
　　取消别名
　　unlias name

cal 
　　查看某一年的日历，可以是1-9999中的任意一年
　　cal 88

zcat
　　查看压缩包中的内容

sed -i 's#old#new#g' 文件名
　　使用new替换文件中的old

ssh root@192.168.8.15 "ifconfig"
　　远程执行命令

bash -x 脚本名
　　调试脚本

centos6上的三个网络配置文件
　　/etc/sysconfig/network-scripts/ifcfg-etho
　　/etc/sysconfig/network
　　/etc/resolv.conf # dns
```

![img](https://www.runoob.com/wp-content/uploads/2014/06/003vPl7Rty6E8kZRlAEdc690.jpg)

1. **/boot：**
   这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件。
2. **/dev ：**
   dev是Device(设备)的缩写, 该目录下存放的是Linux的外部设备，在Linux中访问设备的方式和访问文件的方式是相同的。
3. **/etc：**
   这个目录用来存放所有的系统管理所需要的配置文件和子目录。
4. **/home**：
   用户的主目录，在Linux中，每个用户都有一个自己的目录，一般该目录名是以用户的账号命名的。
5. **/lib**：
   这个目录里存放着系统最基本的动态连接共享库，其作用类似于Windows里的DLL文件。几乎所有的应用程序都需要用到这些共享库。
6. **/lost+found**：
   这个目录一般情况下是空的，当系统非法关机后，这里就存放了一些文件。
7. **/media**：
   linux系统会自动识别一些设备，例如U盘、光驱等等，当识别后，linux会把识别的设备挂载到这个目录下。
8. **/mnt**：
   系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在/mnt/上，然后进入该目录就可以查看光驱里的内容了。
9. **/opt**：
    这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则就可以放到这个目录下。默认是空的。
10. **/proc**：
    这个目录是一个虚拟的目录，它是系统内存的映射，我们可以通过直接访问这个目录来获取系统信息。
    这个目录的内容不在硬盘上而是在内存里，我们也可以直接修改里面的某些文件，比如可以通过下面的命令来屏蔽主机的ping命令，使别人无法ping你的机器：

## vim 操作
