# Linux—CentOS 8 安装记录

- 我选择安装的是CentOS 8.4.2105 版本，为什么选择CentOS呢，因为我看的学习书籍《鸟哥的Linux私房菜》用的是CentOS，但是他用的是CentOS 7.x，版本；我看网上说7.x和8.x没有什么很大的区别，于是选择的最新版本，因为CentOS 8.x 将会是最后的更新，为了减少后期升级的麻烦，我就选择的最新的版本，但是安装完成后有一些后悔，在安装软件向日葵远程控制时发现安装不了，所以，现在安装的话我建议安装7.x版本的CentOS；
- 安装的机器是物理机，用的家里的老电脑，反正不怎么使用，不如直接安装成Linux，继续他的使命；
- 物理机器的配置是Intel Core i3-3240；nVidia GT 620；8G内存；120GB SSD+300G HDD
- ![1](Linux.assets/1.png)
- 根据计算机选择合适的ISO，我选择的是X86_64
- ![2](Linux.assets/2.png)
- 选择镜像
- ![3](Linux.assets/3.png)
- ![4](Linux.assets/4.png)

## 制作安装盘

- 因为电脑之前有系统，是Windows 10专业版，在安装之前首先需要把系统盘格式化；
- 下载U深度软件，将U盘制作成启动盘，将U盘插入需要将要安装成CentOS的电脑中，启动电脑进入BIOS，设置成从U盘启动；
- ![5](Linux.assets/5.png)
- ![6](Linux.assets/6.png)
- 在PE环境中进入硬盘分区工具，把SSD格式化
- ![7](Linux.assets/7.png)
- 再下载软件UltralISO，目的是把之前下载的CentOS提取的U盘（一个已经格式化的U盘）中；
- 在U盘格式化时，注意更改一下命名，因为在之后会再次用的这个名字，这里，我把名字设为LEI；
- ![8](Linux.assets/8.png)
- ![8](Linux.assets/9.png)
- 将CentOS的ISO提取到LEIU盘中
- ![10](Linux.assets/10.jpg)
- ![11](Linux.assets/11.png)
- 提取过程可能有点长
- ![12](Linux.assets/12.png)

## 系统安装

- 提取完成之后，将U盘插入待安装电脑，开机进入BIOS，设置成从UEFI启动盘进入

- ![13](Linux.assets/13.jpg)
- 启动后进入如下界面，需要注意的是不能直接选择两者中的任一个，应该先对第一个进行修改，确定其指定正确的U盘位置！因此根据下面的提示是，先按'e'键
- ![14](Linux.assets/14.jpg)
- 在进入的如下界面，对第二行进行修改，修改成如下（LEI为U盘的名称）
- ![15](Linux.assets/15.jpg)
- ![16](Linux.assets/16.png)
- 这就完成了修改，接下来使用Ctrl+X，退出改界面之后便出现类型如下界面，等待一会儿之后就进入了UI安装界面
- ![17](Linux.assets/17.jpg)
- 进入UI安装界面上，首先设置语言，这里我选择设置为简体中文；设置键盘样式；
- ![18](Linux.assets/18.jpg)
- 在如下界面中，带有感叹号的都是需要接下来设置的
- ![19](Linux.assets/19.jpg)
- 首先对安装源和安装目的地进行设置：安装目的地设置为之前格式化了的SSD；安装源就是U盘，这里选择最紧的镜像（可能会不一样）
- ![20](Linux.assets/20.jpg)
- 选择安装的软件：根据需要选择，这里选择的是带GUI的服务器
- ![21](Linux.assets/21.jpg)
- 下一步，设置网络时间等
- 在对用户进行设置，我一开始不懂，只创建了用户，没有设置ROOT密码，这个目前无影响，进入系统之后可以再设置
- ![22](Linux.assets/22.jpg)
- 都设置完成后，没有感叹号了，开始安装，进入下一步
- ![23](Linux.assets/23.jpg)
- 之后冒出来这个，不过问题不大/还会有接收许可证的警告，直接接收便可；
- ![24](Linux.assets/24.jpg)
- 安装！
- ![25](Linux.assets/25.jpg)
- 完成！
- ![26](Linux.assets/26.jpg)
- ![27](Linux.assets/27.jpg)
- ![28](Linux.assets/28.jpg)

# Linux—CentOS 7 安装记录

## 版本选择

在安装完CentOS 8.x之后，我**后悔**了！！！

物理机器的配置是Intel Core i3-3240；nVidia GT 620；8G内存；120GB SSD+300G HDD

因为一开始对Linux是基本不懂的，甚至有哪几种发行版都不知道，匆匆地就安装了CentOS8。但是，当我安装完成之后，又读了很多关于CentOS的文章，发现CentOS 8.x居然仅仅是两年前发布的系统，并且在今年就即将停止维护了。更要命的是，在我使用CentOS时遇到了很多的问题，在搜索的时候，答案的解决都是基于CentOS 7.x的，这让我很是崩溃！特别是在安装软件方面的问题，向日葵远程控制软件安装不了；截图工具flameshot安装不上；snap安装出错；坚果云网盘（*这个主要用来同步截图，因为主力机还是Windows，编程工作或文字工作等都在Windows上，所以需要把Linux上的截图同步到Windows上*）使用有问题等（原因可能是我不会用也可能是软件的适配性不好）！

>CentOS（Community Enterprise Operating System，中文意思是社区企业操作系统）是Linux发行版之一，它是来自于Red Hat Enterprise Linux依照开放源代码规定释出的源代码所编译而成。由于出自同样的源代码，因此有些要求高度稳定性的服务器以CentOS替代商业版的Red Hat Enterprise Linux使用。两者的不同，在于CentOS完全开源。

>CentOS 8是CentOS项目发布的开源类 服务器操作系统 ，于**2019年9月24日**正式发布。 CentOS 8是一个稳定、高预测性、高管理性、高重复性的 Linux 平台，由 RedHat 企业级Linux（ RHEL ）的源代码进行再发行。

>CentOS 8 和 RedHat Enterprise Linux 8 发行的版本是一致的,都是基于 Fedora 28 和 内核 4.18.
>
>支持传统的、新兴的工作负载的工具，为用户提供了稳定的、安全的、一致的基础、跨混合云部署。
>
>CentOS 完全遵守 Red Hat 的再发行政策，并且致力与上游产品在功能上完全兼容。 CentOS 对组件的修改主要是去除 Red Hat 的商标及美工图。
>
>该版本还包含全新的 CentOS Streams ，Centos Stream 是一个滚动发布的 Linux 发行版，它介于 Fedora Linux的上游开发和 RHEL 的下游开发之间而存在。 你可以把 CentOS Streams 当成是用来体验最新红帽系 Linux 特性的一个版本，而无需等太久。
>
>本次发布的版本重点主要包括：
>
>发行版 / 存储库
>
>- CentOS 8 主要通过两个存储库分发：1） BaseOS 2）应用程序流 AppStream ；
>- BaseOS 存储库：主要包括操作系统功能的核心，以 RPM 格式提供；
>- AppStream 存储库：主要包括用户空间应用程序，支持传统的 RPM 格式的新扩展模块，可安装多个版本的组件；
>
>软件管理
>
>- YUM 包管理器是基于 DNF 技术，在性能方面得到了提升，并支持模块化内容，提供了稳定的 API 和其他工具集成；
>
>Shell 脚本 和 命令行工具
>
>- RHEL 8 主要提供了版本控制工具：1）Git 2.18：分散架构分布式控制工具；2）Mercurial 4.8：轻量级分布式版本控制工具，能够有效的处理大型项目；3）Subversion 1.10：集中版本控制工具
>
>动态编程语言，Web和数据库服务器
>
>- Python 3.6 是 RHEL 8 中的默认 Python 环境，有限支持Python 2.7；
>- Node.js 是 RHEL 中的新功能，其他动态编程语言主要包括：PHP 7.2，红宝石2.5，Perl 5.26，SWIG 3.0；
>- RHEL 8 中提供了数据库服务器，其主要包括：MariaDB 10.3，MySQL 8.0，PostgreSQL 10，PostgreSQL 9.6和Redis 5。
>- RHEL 8 提供 Apache HTTP Server 2.4 以及引入了一个新的 Web 服务器：nginx 1.14。
>- Squid 版本已升级到 4.4，同时还提供了一个新的代理缓存服务器：Varnish Cache 6.0。
>
>桌面
>
>- GNOME Shell 已升级到 3.28。主要包括：1）GNOME Boxes 新功能；2）新屏幕键盘；3）扩展设备支持，集成了 Thunderbolt 3 接口；4）GNOME 软件，dconf-editor 和 GNOME 终端的改进；
>- GNOME 会话和 GNOME 显示管理器使用 Wayland 作为默认显示服务器，在 RHEL 7 的默认显示服务器还是可用的；
>
>安装程序和映像创建
>
>- Anaconda 安装程序可利用 LUKS2 磁盘加密，并在安装系统支持 NVDIMM 设备；
>- 图像生成器工具可创建包含其他程序包的自定义系统映像，可通过图形用户界面进行访问以及可输出多种格式；
>- RHEL 8 中支持使用 IBM Z 主机上的 硬件管理控制台 HMC 和 支持元素 SE 从 DVD 安装的功能；
>
>核心内核
>
>- 扩展功能可使用户空间能够将自定义程序附加到各种点，主要包括：（套接字，跟踪点，数据包接收）用于接收和处理数据；
>- BPF 是一种用于创建有效的内核跟踪和操纵程序的工具；
>
>文件系统和存储
>
>- LUKS2 格式替代了旧版 LUKS1 格式，dm-crypt 子系统和 cryptsetup 工具作为默认使用的 LUKS2 加密卷格式；
>
>安全
>
>- 默认应用系统范围的密码策略，主要覆盖 TLS，IPsec，SSH，DNSSEC 和 Kerberos 协议，管理员可使用该命令：update-crypto-policies 可轻松切换不同模式：default、legacy、future 和 fips ；
>- 支持智能卡和硬件安全模块（HSM用）PKCS＃11
>
>网络
>
>- nftables 框架替换了 iptables 默认网络数据包过滤工具；
>- firewalld 守护使用 nftables 作为默认后端；
>- 支持多个容器的网络连接的 IPVLAN 虚拟网络驱动程序；
>- eXpress Data Path (XDP), XDP for Traffic Control (tc), 以及 Address Family eXpress Data Path (AF_XDP), 可作为部分 Berkeley Packet Filtering (eBPF) 扩展特性；
>
> 虚拟化
>
>- 虚拟化支持现代的基于 PCI Express 的计算机类型，在 RHEL 8 中创建的虚拟机中自动对其进行配置，虚拟设备的功能和兼容性得到了逐步的改进；
>- 支持 RHEL 8 Web 控制台创建和管理虚拟机；
>- QEMU 仿真器引入了沙盒功能，调用 QEMU 可以执行可配置的限制哪些系统，使虚拟机更安全；
>
>编译器和开发工具
>
>- GCC 编译器更新到 8.2 版本，支持最新的 C ++ 语言标准版本，更好的优化，新的代码强化技术，改进的警告和新的硬件功能。
>- 现在，用于代码生成，操作和调试的各种工具可以实验性地处理DWARF5调试信息格式；
>- 内核支持 eBPF 跟踪可用于一些工具，如 BCC，PCP 和 SystemTap；
>- glibc 库升级到 2.28 支持 Unicode 11，更新的 Linux 系统调用，关键提升主要在 DNS stub resolver 、额外的安全加强和性能提升；
>- RHEL 8 提供 OpenJDK 11, OpenJDK 8, IcedTea-Web, 以及不同 Java 工具，如 Ant, Maven, 或 Scala；
>
>高可用和集群
>
>- 集群资源管理器已经升级到2.0.0版本，修复了一系列 bug 和改进；
>- 在RHEL 8中，pcs配置系统完全支持Corosync 3 knet，和节点名称；
>
>信息来源：[CentOS 8 正式发布！_JackTian-CSDN博客](https://blog.csdn.net/jake_tian/article/details/101444338)

>12 月 8 日，CentOS 开发团队在其官博宣布，CentOS 8 将在 2021 年底结束支持，CentOS 7 由于用户基数与用户贡献较多，因此会按照计划维护至生命周期结束即 2024 年 6 月 30 日，接下来一年会把重心放到 CentOS Stream 上。
>
>信息来源：[CentOS 8 将停止维护了！-CentOS-PHP中文网](https://www.php.cn/centos/466528.html)

在考虑一番后决定**重装CentOS 7.x**，并且上一次安装时，没有做好记录，这次安装再把记录写的详细一点，把博客写得更详细一些！

## 1.启动盘制作

准备材料：

[CentOS 7.x 的ISO文件]([Index of /centos/7.9.2009/isos/x86_64/ (aliyun.com)](https://mirrors.aliyun.com/centos/7.9.2009/isos/x86_64/))

[U深度](http://www.ushendu.com/)(原硬盘已经被格式化为空则不需要这个软件)

[UltraISO](https://cn.ultraiso.net/xiazai.html)

两个被空的U盘（建议8GB以上）（下面直接称其为Kingston和KIOXIA，以便区分二者）

![u1](Linux.assets/u1.png)

<img src="Linux.assets/u2.jpg" alt="u2" style="zoom:25%;" />

### 1.1格式化原的硬盘，删除系统（原硬盘已经被格式化为空则不需要做这一步）

1.1.1下载软件[U深度]([u盘启动盘_u盘启动盘制作工具软件下载_u盘装系统教程_u深度官网 (ushendu.com)](http://www.ushendu.com/))，并安装，将KIOXIA插入电脑并格式化，值作启动盘

<img src="Linux.assets/ushendu1.png" alt="ushendu1" style="zoom:50%;" />

<img src="Linux.assets/ushendu2.png" alt="ushendu2" style="zoom:50%;" />

1.1.2 将KIOXIA插入需要重装Linux的主机中，开机，进入BIOS（进入BIOS的方法不做赘述，网上搜便可解决）

首先设置第一启动项为插入的U盘（KIOXIA）

<img src="Linux.assets/BIOS1.jpg" alt="BIOS1" style="zoom:50%;" />

保存更改并重启

<img src="Linux.assets/BIOS2.jpg" alt="BIOS2" style="zoom:50%;" />

接下来便进入一个PE系统，选择DiskDenius硬盘分区工具，按回车键进入

<img src="Linux.assets/BIOS3.jpg" alt="BIOS3" style="zoom:50%;" />

我这台电脑有两个硬盘（120G SSD 和 300G HDD）

我选择将这两个硬盘全部格式化，因为里面没有什么重要资料，或者是只格式化需要安装系统的硬盘

首先删除所有分区，然后快速分区

<img src="Linux.assets/BIOS5.jpg" alt="BIOS5" style="zoom:50%;" />

<img src="Linux.assets/BIOS4.png" alt="BIOS4" style="zoom: 80%;" />

设置完成后，点击确定，然后关机，等待



### 1.2 重装系统的U盘制作

1.2.1下载ISO提取工具[UltraISO]([最新UltraISO官方免费下载 - UltraISO软碟通中文官方网站](https://cn.ultraiso.net/xiazai.html))

 下载合适的文件 [CentOS 7.x 的ISO文件]([Index of /centos/7.9.2009/isos/x86_64/ (aliyun.com)](https://mirrors.aliyun.com/centos/7.9.2009/isos/x86_64/))

>　　（A）、CentOS-7-DVD版本：DVD是标准安装盘，一般下载这个就可以了。
>
>　　（B）、CentOS-7-NetInstall版本：网络安装镜像。
>
>　　（C）、CentOS-7-Everything版本：对完整版安装盘的软件进行补充，集成所有软件。
>
>　　（D）、CentOS-7-LiveGnome版本：GNOME桌面版。
>
>　　（E）、CentOS-7-KdeLive版本：KDE桌面版。
>
>　　（F）、CentOS-7.0-livecd版本：光盘上运行的系统，类拟于winpe

![CentOS](Linux.assets/CentOS.png)

1.2.2下载完成之后，将U盘（Kingston）插入电脑（不是指安装系统的电脑）中，开始制作安装盘

![U11](Linux.assets/U11.png)

将ISO文件提取到该U盘中

![U22](Linux.assets/U22.png)

需要等待大约半个小时的时间

![U33](Linux.assets/U33.png)

## 2.系统安装

将安装盘设置为第一启动盘，保存修改并重启

<img src="Linux.assets/C1.jpg" alt="C1" style="zoom:50%;" />

进入如下界面后，快速按上下键，否则就会默认选择第一个选择；按动上下键后就会保持在这个界面，让我们有读完的时间；

<img src="Linux.assets/C2.jpg" alt="C2" style="zoom:50%;" />

之后选择得一个选项，按“E”键，进入设置界面，在这个界面我们会使得U盘（Kingston）成为安装介质，如果不做这一步的话，就不能正常安装

<img src="Linux.assets/C3.jpg" alt="C3" style="zoom:50%;" />

按照下面的图片进行更改

hd:LABEL=你的U盘的名字 quiet（这就是格式化的时候需要命名的原因）

<img src="Linux.assets/C4.jpg" alt="C4" style="zoom:50%;" />

在经过一大串英文后，就进入UI安装界面了

设置语言

<img src="Linux.assets/C5.jpg" alt="C5" style="zoom: 50%;" />

设置安装源为本地介质

软件选择根据需要自己选择，我选择的是待GUI的服务器

选择安装位置，我选择的是120GB的SSD

选择网络

<img src="Linux.assets/C6.jpg" alt="C6" style="zoom:50%;" />

设置用户名和密码

设置ROOT密码

<img src="Linux.assets/C7.jpg" alt="C7" style="zoom:50%;" />

自动安装完成后，重启

选择同意许可信息

<img src="Linux.assets/C8.jpg" alt="C8" style="zoom: 50%;" />

CentOS 7 就安装完成了！！

开启新的冒险吧

<img src="Linux.assets/C9.jpg" alt="C9" style="zoom:50%;" />













# Linux——Ubuntu 20.04 安装记录

虚拟机环境

