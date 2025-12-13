# Magisk如何和TWRP共存
有不少人在玩机时都想同时在自己手机上同时拥有magsik和TWRP，但在安卓引入AB分区不就，手机的recovery就不再是个单独的分区，而是和boot分区合并了，这里我将教大家如何让magisk和TWRP共存
# 注意
**本教程只针对AB分区的手机，非AB分区或有独立recovery的手机请问使用本教程的方法**

**手机必须已经OME解锁，OME解锁会清空手机数据**
# 教程
1.下载适用于自己手机的TWRP的img镜像，不要选zip

2.把下载下来的镜像拷贝一份到手机

3.下载并安装Magisk，Magisk一定要是官方渠道下载

4.打开magisk，点`安装`按钮，点击`选择并修补一个文件`

5.选择拷贝到手机的TWRP镜像，对其进行修补

6.修补后的镜像一般在`Download`文件夹里面

7.打开cmd，电脑要有adb和fastboot环境，使用`adb reboot fastboot`重启到fastboot模式，有的手机bootloader也支持fastboot，比如pixel3，像这种手机既可以用`adb reboot fastboot`，也可以用`abd reboot bootloader`

8.进入fastboot后，在终端使用`fastboot boot 原版TWRP镜像.img`临时刷入TWRP

9.如果你的手机有密码锁，那么要等待一两分钟，一两分钟后会让你输入密码或输入图案解锁，使用正确的密码或图案后就可以解开data分区的加密

10.先备份原版boot分区，点击`Backup（备份）`滑动下方滑条确认备份

11.在电脑上的文件资源管理器里会显示你的设备，打开`Internal Storage\TWRP\BACKUPS\XXXXXXXX`,打开里面的第一个文件夹，复制`boot.emmc.win`到电脑并改名为`boot.img`

12.回到TWRP首页，点`Advanced（高级）`，点击`Install Recovery Ramdisk（安装Recovery Ramdisk）`，选择被magisk修补后的镜像，滑动滑条确认安装，之后重启即可
