# 2020初 Arch Linux安装指北


Arch Linux是一个Linux发行版。Linux拥有很多发行版，像很多人熟知的Ubuntu，
Elementary OS，和很多黑客使用的Kali Linux，都是Linux发行版(Distribution). 你可能会疑惑，发行版和Linux之间的关系。 简单来说，Linux系统本身，是一个设计精巧但是不能做很多事情的东西。当年Linus先生孤身一人，为了抵抗Unix的霸权，写出了Linux Kernel，构建起了软件和硬件的连接。Linux本身是一个内核，仅仅包含了有限量的软件。
比如，~sudo su~　这个命令我们已经习以为常，认为这就是Linux系统本身的feature，但其实，~sudo~ 这个命令是作为一个软件存在的。在盘古开天地之时，或者说在Linux系统诞生之初，root用户是理所当然。这里也涉及到了Linux中“一切皆文件”的思想。

<!--more-->

Arch Linux，正如他的名字所表达出来的一样，这是一个需要用户自己去搭建的系统。换句话说，这是一个自由度很高的，可以任意由用户tweak的系统。这里可能有gangjing出来叨叨，说你想要自由你自己把linux从头编译起来，自己写桌面环境，窗口管理。我说你怎么不自己到沙滩上搬沙子回家自己提纯硅造志强呢。Arch的优越性在于他在操作性和原理性两方面达到了一个能够让人接受的平衡。操作性在于用户尝试tweak系统时的简便性，源理性在于向用户展现Linux操作系统的原貌。

论操作性，以Geetoo为代表的发行版，安装及其繁琐，需要自己一步一步编译二进制文件。论原理性，以Ubuntu为代表的商业发行版，会自带很多累赘的软件，比如Ubuntu里的麻将连连看，虽然很好玩（大雾，但他毕竟不是我们想要的。

关于为什么选择Arch作为自己的操作系统，有很多人已经有过论述了，大家大可直接google。但更额外的是，我推荐每个第一次使用Linux的人，或者需要跟Linux打交道的人，都需要仔细研究Arch Linux。

Arch有着及其强大的社区，Arch使用者的群像也是一群热爱折腾的人，相关信息自行google。

但Arch的安装是很复杂的，其中一个特点就是，即使arch被安装好了，他也只有一个命令行界面，所有的图形相关，都是需要用户自行决定安装的。这也印证的Arch的特点，让用户明白桌面环境（DE）并不是某一个系统的原生。

**安装踩坑**
下面是我在上一次安装过程中的一些快速记录，每一点都是很重要的，同时附上相关文章链接。


## 准备 {#准备}

-   系统安装盘（下文有介绍，USB Driver和HDD均可）
-   合法上网工具（QV2ray and SwitchyOmega: a chrome extension）(别问我这个为什么重
    要)


## Prepare the installation driver {#prepare-the-installation-driver}

<https://wiki.archlinux.org/index.php/USB%5Fflash%5Finstallation%5Fmedia%5F(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)>#macOS
Use 'dd' command on macos

1.  Use `diskutil list` to check the  driver
2.  Unmount the device
3.  sudo dd if=/Users/tianchangwang/Downloads/Installation\\
    Source/archlinux-2019.12.01-x86\_64.iso of=/dev/rdisk2 bs=1m
4.  Enject the device


## Plug the source disk to the destination device and lead to BIOS setting {#plug-the-source-disk-to-the-destination-device-and-lead-to-bios-setting}


### Choose to use the HDD as the highest proority {#choose-to-use-the-hdd-as-the-highest-proority}

Use UEFI lead will make you see a simple GUI, you should do it. If you see a
good looking GUI you should check your BIOS, for the info of BIOS, you'd google
it by yourself.


## Follow the installation guide. {#follow-the-installation-guide-dot}

一定要细细阅读[官方安装手
册](<https://wiki.archlinux.org/index.php/Installation%5Fguide>)

推荐阅读文章：<https://www.viseator.com/2017/05/17/arch%5Finstall/>　
推荐视频：<https://www.youtube.com/watch?v=-zb8220uUiA>
上面这个视频几乎可以完全follow，但是要注意在reboot前额外安装dialog和更改镜像。


## Check network. use `ping` {#check-network-dot-use-ping}


## Connect to internet use wifi-menu {#connect-to-internet-use-wifi-menu}

在命令行里连接wifi，使用 `wifi-menu` 即可，注意这个包依赖于 ~dialog~，请务必保证
安装好。


## Mirror: Choose the China area mirror {#mirror-choose-the-china-area-mirror}

选择中国镜像，推荐清华（tuna）和中科大（ustc），能让你的包安装达到满速。


## Disk Partition {#disk-partition}


## Format the disk {#format-the-disk}


## Mount the disk {#mount-the-disk}

You need to create /mnt/boot and mount the sda1 to it.
Rememeber to install vim and dialog


## Chroot {#chroot}

需要在这个时候额外安装这些软件
pacman -S vim dialog wpa\_supplicant ntfs-3g networkmanager


## Set the loader {#set-the-loader}

这是很重要的一步，一旦你没有设置好boot顺序，可能直接导致系统安装失败，前功尽弃。


## Post Installation {#post-installation}

安装完之后，相信相关的图形界面对你来说也是小菜一碟了。xorg＋kde是目前较为流行的
组合。

HAPPY HACKING！


