




# Linux
# Linux基础入门
### Linux硬件资源管理
#### 查看系统PIC设备
`lspic`命令可以列出所有的PIC设备，如主板、声卡、显示卡和网卡等，也会把USB接口设备列出来
##### 查看CPU信息
```shell
more /proc/cpuinfo
```
- 查看物理CPU个数使用如下命令：
```shell
cat /proc/cpuinfo | grep "physical id" | sort | uniq | wc -l
```
- 查看每个CPU中内核个数
```shell
cat /proc/cpuinfo | grep "cpu cores"
```
- 查看系统所有逻辑CPU个数
```shell
cat /proc/cpuinfo | grep "processor" | wc -l
```
##### 查看系统内存信息
```shell
more /proc/meminfo
```
##### 查看磁盘分区信息
```shell
fdisk -l
```
### Linux外在设备的使用
#### 硬件与设备文件
在Linux系统下，硬件设备都以文件形式存在。不同硬件设备有不同的文件类型，硬件与系统下相对应得文件叫设备文件
Linux把设备文件存放在`/dev`下面，设备文件得命名方式是主设备号加次设备号；主设备说明设备类型，次设备号说明具体指哪一个设备
#### 常见文件系统类型

<img src="https://img-blog.csdnimg.cn/20200523175126415.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

#### 1.2.3设备的挂载使用
Linux下挂载的命令是`mount`，格式如下
```shell
mount -t 文件系统类型 设备名 挂载点
```
文件系统类型就是图表中的，设备名就是对应的设备文件，挂载点就是在Linux下指定的挂载目录
#### 设备的卸载
命令为
```shell
umount 挂载目录
```
### 文件系统结构
Linux将所有内容都以文件的形式展现出来，通过一个树形结构统一管理和组织这些文件。
Linux只有一个根目录，根目录下又有很多的子目录，如图所示：

<img src="https://img-blog.csdnimg.cn/20200524145448282.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

#### 目录功能
- `/ext`
这个目录主要用于存放系统管理相关的配置文件以及子目录，其中比较重要的有系统初始化文件`/etx/rc`、用户信息文件`/ext/passwd`等，相关的网络配置文件和服务启动文件也在这个目录下。具体如下图：

<img src="https://img-blog.csdnimg.cn/20200524145821466.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524145913524.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524150023842.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524150043816.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

- `/usr`
此目录主要用于存放应用程序和文件。安装的一些软件默认安装到此目录。具体如图所示：

<img src="https://img-blog.csdnimg.cn/20200524150314774.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524150337559.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

- `/var`
该目录主要用于存放系统运行以及软件运行的日志信息。具体如图所示：

<img src="https://img-blog.csdnimg.cn/20200524150636450.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524150648111.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

- `/dev`
该目录包含系统所有的设备文件，具体如图所示：

<img src="https://img-blog.csdnimg.cn/20200524150743257.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524150752814.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

- `proc`
这是一个虚拟目录，存在于内存中，所有的信息都是内存的映射。通过 此目录，可以和内核内部数据结构进行交互，获取有关进程的有用信息，也可以在系统运行中修改内核参数，具体看图：

<img src="https://img-blog.csdnimg.cn/20200524151124463.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524151136377.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524151157912.png">

- 其他目录
`/boot`：该目录存放的是启动Linux时的一些文件，如果遭到破坏，系统将无法启动
`/bin`和`/sbin`：这两个目录存放的是一些可执行的二进制文件。`/bin`下存放了一些我们经常使用的Linux目录，`/sbin`中的`s`是`super`，该目录存放的是一些超级用户才能执行的命令
`/home`：该目录是系统中每个用户的工作目录，在Linux系统中每个用户都有一个自己的目录
 `lib`：存放的是共享程序库和映像文件
`/root`：超级用户`root`的默认主目录，一般用户没有这个目录的权限
`/run`：外在设备的自动挂载点目录
`lost+found`：用于保存丢失的文件
`tmp`：临时目录，存放临时文件
### 运行机制
#### Linux初始化init系统
Linux操作系统的启动首先从BIOS开始，然后Linux引导程序将内核映像加载到内存，对内核进行初始化，内核初始化的最后一步就是启动PID为1的init进程。这个进程是系统的第一个进程，负责生产其他所有进程
#### 运行级别
- `0`：关机模式
- `1`：单用户模式，只有系统管理员可以登录
- `2`：多用户模式，不支持文件共享，例如不支持NFS服务，不常用
- `3`：完全多用户模式，支持NFS服务，最常用的用户模式，默认登录到字符界面
- `4`：基本不用的用户模式，可以实现某些特定的登录请求
- `5`：完全多用户模式，登录到Linux图形界面
- `6`：重启模式

修改运行级别：
```shell
init 运行级别
```
默认的运行级别通过软链接来实现
查看默认运行级别
```shell
ll /etc/systemd/system/detault.target
```
修改默认运行级别，要先删除默认的软链接，然后重新建立软链接
```shell
rm -rf /etc/systemd/system/default.target
ln -sf /lib/systemd/system/multi-user.target /ect/systemd/system/default.target
```
`multi-user.target`是多用户模式，对应运行级别3，要查看运行级别与`target`的对应关系，可执行如下命令
```shell
ll /lib/systemd/system/runlevel*.target
```
#### 系统关机过程
- `shutdown`命令
使用`shutdown`可以安全的关闭系统。执行该命令后，系统会以广播的形式通知系统中工作的所有用户，系统将在指定时间内关闭。此时`login`指令被冻结，新的用户不能登录，当时间已到或者所有用户注销，`shutdown`就发送信号给init程序，要求init根据`shutdown`传过来的参数改变相应的运行级别。语法如下：
```shell 
shutdown [-fFhknrc（参数名称）] [-t(秒数)] [警告信息] 
# f:重新启动时不执行fsck，fsck是Linux下的一个检查和修复文件系统的程序
# F：重启时执行fsck
# h：将系统关机，在某种程度上与halt命令相当
# k：只是发送信息给用户，但并不会真正关机
# n：不调用init程序关机，而是由shutdown自己进行，不建议使用
# r：shutdown之后重新启动系统
# c：取消上一个shutdown命令
# t：延迟多少秒关机
```
- `halt`命令
最简单的关机命令，相当于`shutdown -h`。执行该命令时将终止所有应用程序，然后调用系统指令`sync`，将所有内存信息通过文件系统写入硬盘，然后停止内核。语法如下：
```shell
halt [-finp]
# f：不管当前系统处于任何运行级别，都不调用shutdown强制关机
# i：关机之前关闭所有网络接口
# n：half执行时不调用系统指令sync
# p：关机是调用poweroff，也就是关机的同时关闭电源，默认选项
```
- `reboot`命令用于重启系统
- `init`命令用于切换运行级别
### 系统服务管理工具`systemd`
以Apache HTTP服务器为例
#### 启动、停止、重启服务
```shell
systemctl start httpd.service#启动服务
systemctl stop httpd.service#停止服务
systemctl restart httpd.service#如果服务是在运行中它将重启，不在运行则启动
systemctl try-start httpd.service#只在服务已经在运行时重启服务
```
#### 查看、禁止、启用服务
使用`enable`或`disable`选项控制一个服务是否开机启动，命令如下：
```shell
systemctl enable httpd.service#开机启动
systemctl disable httpd.service#关闭开机启动
```
查看一个服务的运行状态：
```shell
systemctl status httpd.service
```
`systemctl`管理系统电源

<img src="https://img-blog.csdnimg.cn/20200524163741106.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

### shell简介
`shell`是围绕在Linux内核之外的一个`壳`程序，用户在操作系统上完成的所有任务都是通过`shell`与Linux系统内核的交互来实现的
- `shell`的命令格式
用户登录系统后，`shell`命令启动，`shell`遵循一定的语法格式将用户输入的命令进行分析解释并传递给内核。格式一般为：
```shell
command [options] [arguments]
# command：表示命令的名称
# opitons：表示命令的选项，一般在选项的前面会加一个“-”用于区分参数
# arguments：表示命令的参数 
```
#### 通配符
通配符主要是为了方便用户对文件或目录的描述。常用通配符有“*”，“？”，“[]”

- `*`：匹配任意一个或多个字符
- `?`：匹配任一单一字符
- `[]`：匹配任何包含在方括号内的单字符
通配符也可组合使用
#### shell的重定向
用户的`shell`将键盘设置为默认的标准输入，默认的标准输出和标准错误输出为屏幕
所谓的重定向，就是不使用系统默认的标准输入/输出，而是重新指定

- 输入重定向
输入的重定向用于改变命令的输入源，利用输入重定向可以将一个文件的内容作为命令输入，而不从键盘输入
操作符有`<`和`<<`
`<<`告诉`shell`当前命令的标准输入为来自命令行中一对分隔号之间的内容
- 输出重定向
输出重定向不是将命令的结果在屏幕输出，而是输出到一个指定的文件中
操作符有`>`和`>>`
如果`>`后面的文件不存在，`shell`就会自动创建一个文件，如果文件存在，这个文件的原有内容将被覆盖，使用`>>`则不会被覆盖
- 错误重定向
操作符：`2>`和`2>>`，使用和标准输出重定向一样
#### shell的管道
管道可以把很多命令连接起来，可以把第一个命令的输入当做第二个命令的输出，第二个命令的输出当做第三个命令的输入，以此类推。所以管道的作用就是把一个命令的输出当做下一个命令的输入，而不经过任何文件
通过管道符`|`可以建立管道连接
#### shell中的引用
- 转义字符`\`
将`\`放到特殊字符的后面，`shell`就会忽略这些特殊字符的原有含义，把它们当做普通字符对待
- 单引号`''`
如果将字符窜放到一对单引号之间，字符窜中的所有字符的特殊含义将被忽略
- 双引号`""`
和单引号基本相同，但是还有一些特殊字符即使用双引号也会保留自己的特殊含义
#### 自动补全
输入某个命令一部分后，按`tab`键，`shell`就会根据系统环境变量信息提示出与用户输入命令相似的所有命令和文件
### 系统管理与维护命令
#### `ls`命令
显示指定工作目录下的内容，列出工作目录所含的文件及子目录，语法：
```shell
`ls [选项] [路径或文件]`
```
选项说明如下图：

<img src="https://img-blog.csdnimg.cn/20200524211558735.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524211615163.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200524211628767.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

#### `pwd`命令
显示当前工作目录，语法：
```shell
pwd
```
#### `cd`命令
该变当前工作目录，与Windows下的命令一样，语法：
```shell
cd [目录名]
```
#### `date`命令
显示或修改系统时间与日期，只有超级用户才能修改，一般的用户只是显示时间。语法：
```shell
date [选项] 显示时间格式（以+开头，后面接时间格式）
# -s：set的缩写，设置系统时间
# -d：date的缩写，显示描述的日期
```
时间格式表如下图所示：

<img src="https://img-blog.csdnimg.cn/20200525132754319.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200525132812524.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70)">

<img src="https://img-blog.csdnimg.cn/20200525132826586.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200525132837283.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

##### `passwd`命令
该命令用于设置用户密码，语法如下
```shell
passwd [用户名] [密码]
```
-`su`命令
该命令用于该改变用户身份，语法如下：
```shell
su [选项] [用户名]
#选项说明
# -：加载相应用户下的环境变量
# -l：使用目前的shell成为改变身份后用户默认的shell
# -c：改变身份运行一个指令后就结束
# -m：改变用户身份，但不改变环境变量
```
普通用户切换超级用户：
```shell
su -
```
普通用户修改超级用户`root`的密码
```shell
su -c passwd
```
#### `clear`命令
清除屏幕信息，语法：
```shell
clear
```
#### `man`命令
显示指定命令的帮助信息，语法：
```shell
man [命令名称]
```
#### `who`命令
显示当前用户，语法：
```shell
who [optional] [file]
# 该命令输出格式：名称 [状态] 终端 时间 [活动] [进程标识（主机名）]
```
该命令选项：

<img src="https://img-blog.csdnimg.cn/20200525171649544.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200525171830115.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

在Linux中，`who`通常通过`/var/run/utmp`文件来获取信息，如果`[file]`选项指定另一个文件，`who`就会读取该文件来获取信息
#### `w`命令
用于显示登录到系统的用户信息，语法：
```shell
w [optional] [用户]
# 选项说明：
# -h：不显示输出信息的表土
# -i：显示id地址和主机名
# -s：用短格式输出，不显示登录时间、JCPU和PCPU时间
# -V：显示版本信息
```
#### `uname`命令
显示操作系统相关信息，语法：
```shell
uname [optional]
# 选项说明：
# -a：显示操作系统全部信息
# -m：显示系统cpu类型，是32位还是64位
# -n：显示操作系统的主机名
# -s：显示操作系统类型
# -r：显示操作系统内核版本
```
#### `uptime`命令
输出系统任务队列消信息，语法：
```shell
uptime
```
#### `last`命令
列出目前与过去登入系统的用户相关信息。执行该命令时，它会默认读取`/var/log/wtmp`文件，语法：
```shell
last [optional] [-n (显示列数)]
# 选项说明：
# -a：把从任何登入系统的主机名或ip地址显示在最后一行
# -R：不显示登入系统的主机名或ip地址
# -x：显示系统关机、重新开机及执行等级的改变信息
# -n(显示列数)或-(显示列数)：设置列出名单的显示列数
# -d：将显示的ip地址转换为主机名称
```
#### `dmesg`命令
显示开机信息。内核会将开机信息储存在系统缓冲区（ring buffer）中，如果开机来不及查看相关信息，可以使用该命令查看，也可以在`/var/log/dmesg`文件中查看。语法：
```shell
dmesg [optional]
#选项说明：
# -c：显示开机信息后清除ring buffer信息
# -s：设置缓冲区大小，默认为8192
# -n：设置记录信息的层级
```
#### `free`命令
显示系统内存状态，具体包括系统物理内存、虚拟内存、共享内存和系统缓存，语法：
```shell
free [optional] [-s（间隔秒数）]
# 选项说明：
# -b：以字节为单位显示内存使用情况
# -m：以MB为单位显示内存使用情况
# -k：以KB为单位显示内存使用情况
# -t：显示内存总和列
# -s（间隔秒数）：根据指定的间隔秒数持续显示内存使用情况
# -o：不显示系统缓冲区列表
```
#### `ps`命令
显示系统进程在瞬间的运行状态，语法：
```shell
ps [optional]
# 常用选项说明：
# a：显示所有用户的进程，包含每个程序完整的路径
# -x：显示所有系统程序，包括哪些没有终端的程序
# -u：显示使用者的名称和起始时间
# -f：详细显示程序执行的路径群
# -c：只显示进程的名称，不显示进程的完整路径
# -e：将除内核进程以外的所有进程的信息写到标准输出
```
#`top`命令
对系统处理器状态的实时监控，它能够实时显示系统中各个进程的资源占用状况，类似于Windows的任务管理器。语法：
```shell
top [optional]
# 常用选项说明：
# -d：指定每两次屏幕信息刷新之间的时间间隔
# -i：不显示闲置或者僵死的进程信息
# -c：显示进程的整个命令路劲，而不是只显示命令名称
# -s：使用top命令在安全模式下运行，此时top的交互指令被取消，避免潜在危险
# -b：分屏显示输出信息，结合“-n”选项可以将屏幕信息输出到文档
# -n：top输出信息更新次数，完成后将退出top命令
```
交互式命令及说明

<img src="https://img-blog.csdnimg.cn/20200525214003179.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200525214016230.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200525214043362.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200525214056495.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200525214121216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200525214129808.png">

### 文件管理与编辑命令
#### `mkdir`命令
创建一个目录。语法：
```shell
mkdir [optional] 目录名
# 选项说明
# -m：对新建目录设置存取权限
# -p：可以指定一个路径名称。若路径中的某些目录尚未存在，加上此选项后，系统将自动创建哪些不存在的目录，也就是一次可创建多个目录
```
#### `more`命令
查看一个一屏无法展示的文本文件时，可以使用`more`命令。`more`每次显示一屏，按`enter`键再显示文件的一行，按空格键则继续显示下一屏文本内容。语法：
```shell
more [optional] 文件名
# 选项说明：
# -d：在屏幕底部more提示符后显示友好信息，
# -s：将输出中的多个空行减少为只有一个空行输出
# -p：先清除屏幕以前的信息，在显示文本
# -c：显示文件时，每屏显示都清除屏幕先前的信息，然后从最顶端显示出来
```
#### `cat`命令
用来将文件的内容输出到标准输出，同时还可用来连接合并文件。语法：
```shell script
cat [optional] 文件名
cat 文件1 文件2>文件3 #将文件1和文件2的内容合并到文件3中，如果文件3中有其他内容则被覆盖，如果文件不存在该命令会自动创建。
# 选项说明：
# -A：将文件中的制表符显示为“^|”，同事在每行末尾显示一个$符号
# -b：将文件中的所有非空行按序号编号，编号从1开始
```
#### `diff`命令
比较文件差异。该命令以逐行的方式比较文本文件的异同，如果比较的是目录，则比较目录中相同文件名的文件，不会比较其中的子目录。语法：
```shell script
diff [optional] 文件1 文件2
# 选项说明：
# -c：显示全部内容并标出不同之处
# -b：忽略行尾的空格，同时字符串中的一个或多个空格将被视为相同
# -r：当文件1和文件2为目录时，会比较子目录中的文件
# -s：当两个文件相同时，显示相同信息
```
#### `grep`命令
该命令是Linux下的过滤工具，`grep`根据指定的字符串，对文件的每一行进行搜索，如果找到了这个字符窜，就输出该行的内容。语法：
```shell script
grep [optional] 要查找的字符串 文件名
# 选项说明：
# -A NUM：除了列出符合条件的行外，同时列出每个符合条件行后的NUM行
# -c：只显示符合条件的行，而不是显示每行的具体信息
# -f file：事先将要搜索的样式写入一个文件中，每行一个样式，然后以这个文件作为条件进行搜索
# -i：搜索是忽略大小写
# -n：在搜索结果中显示行号
# -B：与选项“-A”相反，除了列出符合条件的行外，同时列出每个符合条件行的前NUM行
```
#### `rm`命令
该命令用来删除某个目录及其下的所有文件及子目录。对于链接文件，只是断开了链接，原文件保持不变。语法：
```shell script
rm  [optional] 文件或目录
# 选项说明：
# -r：告诉rm将选项中列出的全部目录及子目录还有文件均递归删除，如果在选项中不指定“-r”，“rm"命令将不能删除目录
# -f：忽略不存在的问题，也不给出提示
# -i：交互式删除，即在删除前进行确认
```
#### `touch`命令
该命令用来改变指定文件的访问时间和修改时间，若指定的文件不存在则创建，若是没有指定时间，则使用当前时间。语法：
```shell script
touch [optional] 设定的时间 文件
# 选项说明：
# -a：改变文件的访问时间为系统当前时间，无需设置时间选项
# -m：改变文件的修改时间为系统当前时间，无需设置时间选项
# -c：如果文件不存在，不创建也不提示
# -d或-t：使用指定的日期或时间
# -r<参考文件或目录>：把指定的文件或目录的日期、时间都设置成参考文件或目录的时间、日期
```
#### `ln`命令
用来在文件或目录之间创建链接
Linux下有两种链接，一种是硬链接，一种是软链接，默认情况下`ln`命令产生的是硬链接
- 硬链接
是指通过文件的inode来进行链接。在Linux的文 件系统中，保存在磁盘的所有类型的文件都会分配一个编号，这个编号称为inode号(Inode Index)。多个文件指向同一个inode在Linux系统中是允许的，这就是所谓的硬链接。硬链接的作用是允许一个文件拥有多个有效的路径名，这样用户就可以对一些重要文件建立硬链接，以防止误删除操作。因为对应该文件的inode有一个以上的链接，所以只删除一个链接并不影像inode本身和其他链接，只有当最后一个链接被删除后，文件的数据块及目录的链接才会释放，也就是说，此时文件才会被真正删除。
- 软链接
也叫符号链接，类似与Windows中的快捷方式，因此软链接是一个指向真正的文件或者目录位置的符号连接

语法：
```shell script
ln [optional] 源文件 目标文件链接名
# 选项说明：
# -f：如果在目标位置存在与链接名相同的文件，这个文件将被删除
# -s：进行软链接
# -d：允许系统管理员硬链接自己的目录
# -b：对将在链接时会被覆盖或者删除的文件进行备份
```
#### `file`命令
用来显示文件的类型。对于长度为0的文件，将识别为空文件；对于符号连接文件，默认情况下将显示符号链接引用的真实文件路径。语法：
```shell script
file [optional] 文件名
# 选项说明：
# -b：显示文件类型结果，不显示对应文件名
# -L：直接显示符号链接所指向文件的类型
# -z：显示压缩文件的信息
# -d：如果文件不是常规文件，则不进一步对文件类型进行分类
```
#### `cp`命令
将给出的文件或目录复制到另一个文件或目录中。语法：
```shell script
cp [optional] 源文件或目录 目标文件或目录
# 选项说明：
# -a：在复制目录时使用。它保留所有的信息，包括文件链接、文件属性，并递归的复制目录
# -r：若给出的源文件是一个目录，此时cp将递归复制该目录下所有子目录和文件。此时目标文件必须成为一个目录名
# -d：复制时保留链接，这样不会失去链接文件
# -p：保留文件的修改时间和存取权限
# -i：如果已经有相同文件名的目标文件，则提示用户是否覆盖
```
#### `find`命令
在指定的路径下查找指定的文件。语法：
```shell script
find path-name [-optional] [-print -exec -ok 命令 {} \;]
# 参数说明：
# path-name：查找的目录路径，可以用“.“表示当前路径
# -optional：控制搜索方式
# -print：将搜索结果输出到标准输出
# -exec：对搜索出符合条件的文件执行所给出的Linux命令，而不询问用户是否需要执行该命令。{}表示shell命令的选项，即为所查找到的文件，命令的末尾以”;“结束
# -ok：对搜索出符合条件的文件执行所给出的Linux命令，它会询问用户是否执行
```
选项说明：

<img src="https://img-blog.csdnimg.cn/20200527175136722.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200527175146873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200527175204314.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70" alt="">

<img src="https://img-blog.csdnimg.cn/20200527175216495.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70" alt="">

<img src="https://img-blog.csdnimg.cn/20200527175225620.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70" alt="">

#### `split`命令
分割文档，将一个文件分割数个。语法：
```shell script
split [optional] [input_file] [output_file]
# 选项说明：
# -b size：指定分割出来的文件大小，size可加入单位，b代表512字节，k代表1KB，m代表1MB
# -n：这里“n“指定分割的每个文件的长度，默认为1000行
# -d：将split命令生成的文件序列以数字形式命名
# -a：指定split命令生成的文件序列的长度，默认长度为2
# 参数说明：
# input_file：要分割的文件
# output_file：分割出来的文件序列，split命令分割后生成的文件序列名依次为output_fileaa、output_fileab、output_fileac等，如果没有指定output_file，系统默认以”x”作为文件输出名
```
#### `mv`命令
将文件或目录改名，或将文件由一个目录移动到另一个目录。如果源文件和目标类型都是文件或目录，mv将进行目录重命名。如果源类型为文件，而目标文件为目录，mv将进行文件的移动。语法：
```shell script
mv [optional] 源文件或目录 文件或目录 
# 选项说明：
# -i：交互操作，若要覆盖文件或目录时，体统将询问是否覆盖，用户输入“y”或“n”决定是否覆盖
# -f：禁止交互式操作，没有任何提示
```
### 压缩与解压
#### `zip`和`unzip`命令
将一般的文件或者目录进行压缩或解压，默认生成以“.zip”为后缀的压缩包。语法：
```shell script
zip [optional] 压缩文件名 需要压缩的文档列表
unzip [optional] 压缩文件名
```
`zip`命令选项说明：

<img src="https://img-blog.csdnimg.cn/20200528134336930.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

<img src="https://img-blog.csdnimg.cn/20200528134424528.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

`unzip`命令选项说明：

<img src="https://img-blog.csdnimg.cn/20200528134524168.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

####`gzip`和`gunzip`命令
将一般的文件进行压缩或解压，压缩文预设的拓展名为“.gz”，`gunzip`就是`gzip`的硬链接，所以解压和压缩都可以使用`gzip`来实现
`gzip`只能对文件进行压缩，不能压缩目录，即使指定压缩的目录，也只能压缩目录内的文件。语法：
```shell script
gzip [optionnal] 压缩（解压缩）的文档名
# 选项说明：
# -d：对压缩的文件进行解压
# -r：递归式压缩指定目录以及子目录下的所有文件
# -t：检查压缩文档的完整性
# -v：对于每个压缩和解压缩的文档，显示相应的文件名和压缩比
# -l：显示压缩文件的压缩信息，显示字段为压缩文档大小、未压缩文档大小，压缩比和未压缩文档名称
# -num：用指定的数字配置压缩比，”-1“或”-fast“表示最低压缩级比，”-9“或”-best“表示最高压缩比。系统默认压缩比为6
```
#### `bzip`和`bunzip2`命令
类似于`gzip`和`gunzip`命令，只能对文件进行压缩，对目录只能压缩目录下的所有文件，压缩完成后，在目录下生成以”.bz2“为后缀的压缩包。`bunzip2`是`bzip`的软连接。语法：
```shell script
bzip2 [optionnal] 压缩（解压缩）的文档名
# 选项说明：
# -d：执行解压缩，此时选项后面跟要解压缩的文件
# -v：压缩或解压文件时显示详细信息
# -k：bzip2在压缩或解压缩后，会删除原始文件，若要保留原始文件，可使用此选项
# -f：在压缩或解压缩时，若输出文件与现有文件同名，预设不会覆盖现有文件。若要覆盖，就要使用此选项
# -t：测试".bz2"压缩文件的完整性
# -压缩级别：压缩级别可从1~9中选取，数字越大，压缩率越高
```
#### `tar`命令
`tar`时Linux下经常使用的归档工具，对文件或者目录进行打包归档，归档成一个文件，但并不进行压缩。语法：
```shell script
tar [optional + 辅助选项] 文件或目录
# tar主要选项说明：
# -c：新建文件
# -r：把要归档的文件追加到档案文件的末尾
# -t：列出打包的档案文件中还原文件
# -x：从打包的档案文件中还原出文件
# -u：更新档案文件，用新建文件替换档案中的原始文件
```
辅助选项说明：

<img src="https://img-blog.csdnimg.cn/20200601174624140.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/2020060117470169.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200601174729361.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">

#### `dd`命令
该命令用来转换或复制文件，同时可以对设备进行备份。语法：
```shell script
dd if=input_file of=output_file bs=block_size count=number
# 选项说明：
# if：输入文件，可以是设备，例如磁盘某分区或整个磁盘
# of：输出文件，也可以是设备
# bs：指定一个block的大小，如果没有只当默认512字节
# count：就是bs的数量
```
#### `cpio`命令
该命令是通过重定向的方式将文件进行打包、备份、还原、恢复的工具，它可以解压以“.cpio”或者“.tar”结尾的文件。语法：
```shell script
cpio [optional] > 文件名或设备名
cpio [optional] < 文件名或设备名
# 选项说明：
# -o：将文件复制、打包成文件或者将文件输出到设备
# -i：将打包文件解压或者将设备上的备份还原到系统
# -t：查看cpio打包的文件内容或者输出到设备上的文件内容
# -v：显示打包过程中的文件名称
# -d：在cpio还原文件的过程中，自动建立相应的目录
# -c：一种较新的存储方式
# -B：让没认块可以增大到5120字节，没人块为512字节，这样做的好处是可以加快存取速度
```
### 磁盘管理与维护
#### `df`命令
检查Linux系统磁盘空间占用情况。语法：
```shell script
df [optional] 
# 选项说明：
# -h：以容易理解的格式输出文件系统分区占用情况，如32KB、120MB、 60GB
# -k：以KB大小为单位输出文件系统分区占用情况
# -m：以MB大小为单位输出文件系统分区占用情况
# -a：列出所有的文件系统分区，包含0大小的文件系
# -i：列出文件系统分区的inode信息
# -T：显示磁盘分区的文件系统类型
```
#### `du`ml命令
显示文件或目录所占用的磁盘看见情况。语法：
```shell script
du [optional] 文件或目录
# 选项说明：
# -s：显示文件或者整个录的大小，单位为KB
# -b：以字节为单位显示文件大小或者显示目录下所有文件的大小
# -sh：以人性化的格式显示文件或者目录大小，如300MB、1.2GB等
# -sm：以MB为单位显示文件或者目录大小
```
#### `fsck`命令
检查文件系统并尝试修复错误。语法：
```shell script
fsck [optional] [-t<文件系统类型>] [设备名]
# 选项说明：
# -a：自动修复文件系统，没有任何提示
# -r：采取交互式的修复模式，在执行修复时进行询问，让用户得以确认并决定处理方式
# -A：依照/etc/fstab配置文件的内容，检查文件内所列的全部文件系统
# -T：执行fsck指令时，不显示标题信息
# -V：显示fsck指令的执行过程
# -N：不执行指令，仅列出实际执行会进行的动作
```
在执行fsck命令修复某个文件系统时，这个文件系统下进行修复是极为不安全的，数据可能遭到破坏，也有可能下进行修复是极为不安全的，数据可能遭到破坏，也有可能损坏磁盘。
#### `sync`命令
强制把内存中的数据写回硬盘，以免数据丢失。语法：
```shell script
sync
```
在Linux系统中， 修改过的操作会缓存到内存中，不会马上写入硬盘，等待适当的时候再从内存写入磁盘，这样可以提高系统读写效率。Linux 下默认每隔3秒系统自动执行一次sync操作，系统正常关机时也会执行sync操作，保证所有操作全部从内存写入磁盘。如果非法关机，系统内存信息无法及时同步到硬盘，就会造成数据丢失或者文件损坏，由此可见，Linux系统中正常关机是非常重要的
#### `eject`命令
该命令用来退出抽取式设备，如光盘磁带。如果该设备已经挂载，则`eject`先将设备卸载，然后再退出。语法：
```shell script
eject [optional] 设备名
# 选项说明：
# -c<光驱编号>：如果Linux系统中有多个光驱，要指定某个光驱
# -d或--default：显示默认设备，而不是实际执行操作
# -f或--floppy：退出抽取式软盘
# -q或--tape：退出磁带
# -r或--cdrom：退出光盘
# -t或--trayclose：关闭光盘的托盘
# -n或--noop：显示指定的设备名对应的设备文件路径。默认显示光盘的设备文件路径
```
#### `mount`和`umount`命令
挂载以及卸载指定的文件系统。语法：
```shell script
mount [optional] [-L<标签>] [-o<选项>] [-t<文件系统类型>] [设备名] [挂载点]
umount [挂载点]
# 选项说明
# -a：加载文件/et/fstab中指定的所有设备
# -n：不将加载信息记录在/etc/mtab文件中
# -r：以只读方式加载设备
# -w：以可读写模式加载设备，属于mount默认设置
# -f或-v：不加载设备，仅查看mount的挂载状态
```
参数说明：
1) `L<标签>`：标签其实就是磁盘分区标识的别名，标签可以随便起名，这样便于记忆，在Linux 下磁盘分区的设备名比较难记，利用标签代替设备名，简单易记。
2) `-o<选项>`：指定加载文件系统时的选项，选项如下：
<img src="https://img-blog.csdnimg.cn/20200603174357451.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70" >
<img src="https://img-blog.csdnimg.cn/20200603174442172.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
3) `-t<文件系统类型>`：指定设备的文件系统类型，常用选项：
<img src="https://img-blog.csdnimg.cn/20200603174725732.png">
<img src="https://img-blog.csdnimg.cn/20200603174803628.png">
4) 设备名：硬盘分区在Linux上的设备标识，类似于`/dev/sda1`、`/dev/sda1`等
5) 挂载点：Linux系统下指定的某个目录
### 网络设置与维护
#### `ifconfig`命令
该命令用来配置网络或显示当前网络接口状态。类似于Windows下的`ipconfig`命令，该命令必须由root用户来执行。语法：
```shell script
ifconfig [optional] [interface] [inet|up|down|netmask|addr|broadcast]
# 选项说明：
# -a：显示所有的网络接口信息，包括活动的和非活动的
# -s：仅显示每个接口的摘要数据，是有关接口活动性的，每个接口显示一行信息
# -v：如果某个网络接口出现错误，将返回错误信息，以帮助发现和处理故障
```
参数说明：
1) `interface`：网络接口名，Linux 下的网络接口1名类似于eth0、eth1和Io等(在CentOS 7.x版本中，网络接口名变为类似enp0s1、enp0s2这样的标识)，分别表示第1块网卡、第2块网卡和回环接口。这是个可选项，如果不添加此选项，则显示系统中所有的网卡信息;如果添加此选项，则显示指定网卡信息。
2) `up`：激活一个网络接口。
3) `down`：与up相反，使指定的网络接口无效。
4) `netmask`：为一个指定的网络接口指定子网掩码。
5) `addr`：这里的"addr" 为网络接C ]指定的IP地址。
6) `broadcast`：为指定的接口设置广 播地址。
#### `scp`命令
该命令是`secure copy`的缩写，用于将文件或者目录从一个Linux复制到另一个Linux系统下。该命令传输数据使用的是SSH协议，保证了数据传输的安全。语法：
```shell script
scp 远程用户名@ip地址:/文件绝对路径 本地Linux系统路径 # 将远程Linux系统上的文件或目录复制到本地
scp 本地Linux系统文件路径 远程用户名@ip地址:远程系统文件绝对路径 # 将本地的文件或目录复制到远程Linux系统
```
#### `netstat`命令
显示本机网络连接、运行端口和路由表等信息。语法：
```shell script
netstat [optional]
```
选项说明：
<img src="https://img-blog.csdnimg.cn/20200605173450253.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200605173545657.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200605173630885.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70" >
<img src="https://img-blog.csdnimg.cn/20200605173709467.png">
#### `traceroute`命令
traceroute命令用来显示网络数据包传输到指定主机的路径信息，追踪数据传输路由状况。预设数据包大小是38字节，用户可另行设置。它与Windows 下的tracert命令类似。语法：
```shell script
traceroute [optional] [远程主机名或ip地址] [数据包大小]
# 选项说明：
# -i<网络接口>：使用指定的网络接口发送数据包
# -n：直接使用IP地址而不使用主机名
# -v：详细命令的执行过程
# -w<超时秒数>：设置等待远程主机回应的时间
# -x：开启或关闭对数据包的准确性校验
# -s<来源ip>：设置本地主机发送数据包的IP地址
# -g<网关地址>：设置来源的路由网关，最多可设置8个
```
#### `telnet`
该命令通过`telnet`协议与远程主机通信或获取远程主机对应端口的信息。与Windows下的`telnet`具有相同的功能。语法：
```shell script
telnet 主机名或ip地址端口
```
#### `wget`命令
该命令用来从网络上下载某个软件。语法：
```shell script
wget [要下载的软件的网址]
```
### 文本编辑工具`vi`
`vi`是Linux下标准的文本编辑器，也是Linux系统下最经常使用的文本件可视化编辑器。
`vi`编辑程序有两种工作模式，即命令模式和文本输入模式。在命令模式下，输入的字符被解释未`vi`命令，通过`vi`命令可以转换到文本输入模式；在文本输入模式下，输入的字符作为正在编辑的文件的正文内容来接受，如果按Esc键则切换到`vi`命令模式。
1) 用`vi`打开文件的命令选项：
<img src="https://img-blog.csdnimg.cn/20200608172739536.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70" >
<img src="https://img-blog.csdnimg.cn/20200608172912538.png">
2) `vi`命令模式下的命令选项，主要分为移动光标类命令、屏幕翻滚类命令、插入与删除文本类命令、搜索与替换类命令以及保护与退出命令。
a) 移动光标类及其说明：
<img src="https://img-blog.csdnimg.cn/20200608173235965.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/2020060817330135.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/2020060817333478.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200608173401295.png">
b) 屏幕翻滚类及其说明：
<img src="https://img-blog.csdnimg.cn/20200608173522832.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200608173604790.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
c) 插入与删除文本类命令：
<img src="https://img-blog.csdnimg.cn/20200608173653782.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200608173714787.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200608173758142.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200608173818250.png">
d) 搜索及替换类命令：
<img src="https://img-blog.csdnimg.cn/20200608173952500.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
<img src="https://img-blog.csdnimg.cn/20200608174019455.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
e) 保存与退出类命令：
<img src="https://img-blog.csdnimg.cn/20200608174108271.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hqXzUyNDI1NjE5Mg==,size_16,color_FFFFFF,t_70">
