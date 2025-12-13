# 如何移植Linux软件到安卓
在root手机后，有些人可能就想要拓展自己手机的功能，由于安卓是基于Linux的，所以只要合适版本的Linux可执行文件放入手机的特定文件夹就可以使用了。

在Linux里，这种打包的多个或单个可执行文件，并且释放后会自动放的指定文件夹的归档文件叫软件包，一般以.deb结尾。但在安卓里，由于system文件夹在系统启动后会变为只读模式，即使是root用户也无权修改，所以magisk会创建一个自己的分区，把模块里对应路径的可执行文件通过符号链接的方式链接到对应的文件夹。所以magisk模块其实相当于安卓的软件包，而magisk相当于安卓上带GUI的root管理器和包管理器。

所以我们可以自己编写一个模块，把对应的Linux可执行文件放的对应的路径里，之后填写模块对应的信息制作成压缩包。这样我们的模块差不多就大功告成了，接下来只要来的magisk的模块板块，从本地安装自己做的模块就大功告成了。
# 教程
## 注解
1.模块模板和模块项目是一回事，模块模板是没写模块信息和放入二进制文件的模块项目
## 1.创建Magisk模块
先创建一个文件夹，作为所以magisk模块制作的地方，我这里在手机`内部存储空间`里新建了一个Projects文件夹，里面用于存放所有的magisk模块项目
```
当前目录结构：
Projects
```
之后创建模块的模板，先新建一个文件夹，名字是你模块的名字，这边我会拿curl做演示，在我的演示里，我就新建一个curl文件夹在Projects文件夹里
```
当前目录结构：
Projects
  |-curl
```
在模块的文件夹里面创建`module.prop`，而且一定不要把文件名字给写错了，写错magisk是不识别的
```
当前目录结构：
Projects
  |-curl
     |-module.prop
```
在`module.prop`里写入模块信息，下面是参考模板，在模块信息最后面一定要空一行，不然直接报错
```
id=模块id（全小写英文，建议是模块名字）
name=模块名字（建议全英文）
version=模块版本（可以填写任意内容，建议填写实际版本号，建议全英文）
versionCode=版本号（只能是无符号整数类型，只能是正整数，数值越大表示越新，magisk也就更会采用新版本）
author=模块作者名字
description=模块的描述

```
在演示里是curl，所有我就给大家看curl的`module.prop`
```
id=curl
name=Curl for Android
version=curl(8.17.0)+trurl(0.16.1)
versionCode=1
author=curl
description=curl(8.17.0) and trurl(0.16.1) for android

```
现在我们已经创建好了模块信息，接下来就是要指定可执行文件要放在什么位置，一般可执行文件放在手机的`/system/bin`下面，`/`表示是手机的根目录，在模块里，根目录就是我们的模板文件夹，在演示里就是`curl`文件夹，接下来就在模块模板文件夹下面创建system文件夹，在system文件夹下面创建bin文件夹
```
所有项目的文件夹
    |-模块模板
        |-module.prop
        |-system
            |-bin
```
在演示里就是curl，那么目录结构如下
```
当前目录结构：
Projects
  |-curl
     |-module.prop
     |-system
        |-bin
```
接下来我们要下载对应的二进制文件，二进制文件必须是静态链接的，因为静态链接的已经把所有需要的库都打包在二进制文件里了，所有不用担心因为手机上缺少对应库而导致报错，大部分静态链接的二进制文件在termux，但某些软件他依赖termux的库，所有就要去官网找对应的静态链接版本，下面是curl的演示。

> 接下来我们要下载curl的静态链接版本，静态链接的版本把自身需要的库都打包在可执行文件里了，所有不用担心因为手机上缺少对应库而导致报错
> 
> 这个链接是[使用静态链接的Curl for Linux Arm64的GitHub仓库](https://github.com/stunnel/static-curl)，点击即可跳转到对应的仓库
> 
> 点击[从官方仓库下载静态链接的Curl](https://github.com/stunnel/static-curl/releases/download/8.17.0-ech/curl-linux-armv7-musl-8.17.0-ech.tar.xz)即可从GitHub上下载
> 
> 如果下载速度太慢，可以使用下面的加速链接[加速下载静态链接的Curl](https://edgeone.gh-proxy.org/https://github.com/stunnel/static-curl/releases/download/8.17.0-ech/curl-linux-armv7-musl-8.17.0-ech.tar.xz)即可加速下载
> 
> 有需要还可以使用下面的链接打开GitHub加速器[github加速器](https://gh-proxy.com/)
> 
> 下载下来后我们会得到名字为`curl-linux-armv7-musl-8.17.0-ech.tar.xz`的文件，这是一个压缩文件，但是手机自动的文件管理器是解压不了的，这个时候就请使用第三方文件管理器进行解压缩
> 
> 解压缩完成后会得到下面两个文件
> ```
> curl
> SHA256UMS
> trurl
> ```
> 把里面的`curl`和`trurl`复制到模块项目里的`system/bin`里
> ```
> 当前目录结构：
> Projects
>   |-curl
>      |-module.prop
>      |-system
>         |-bin
>            |-curl
>            |-trurl
> ```
接下来就可以打包模块了，全选**模块项目文件夹里面的**全部文件和文件夹，然后压缩它们为zip格式，压缩好后我们就得到了模块，但是模块不安装的话是没用的，接下来我们要安装模块，接下来看下面的安装教程。
## 2.安装Magisk模块
首先手机里一定要有magisk和magisk环境，之后打开magisk，点击最下面的`模块`按钮，点击`从本地安装`按钮，选择我们刚做好的模块，之后就应该可以看到模块出现在magisk里面，不过现在对应模块还是灰的，只有重启手机后模块才会真正被安装和启用

重启手机后，模块就启用了，一般输入一些指令就可以验证模块是否有效，在我们的演示里就是curl，接下来以curl为例子，看看如何检测模块安装成功

> 打开电脑，电脑里要有adb环境
> 打开cmd，输入`adb shell`打开安卓的shell
> 在shell里输入`su`授权shell超级用户权限（root）
> 使用`curl --version`查看curl版本，验证是否安装成功，如果安装成功应该返回如下信息
> ```
> curl 8.17.0 (armv7-pc-linux-gnu) libcurl/8.17.0 OpenSSL/3.6.0 zlib/1.3.1 brotli/1.2.0 zstd/1.5.7 c-ares/1.34.5 libidn2/2.3.8 libpsl/0.21.5 libssh2/1.11.1 nghttp2/1.68.0 nghttp3/1.12.0
> Release-Date: 2025-11-05
> Protocols: dict file ftp ftps gopher gophers http https imap imaps ipfs ipns mqtt pop3 pop3s rtsp scp sftp smb smbs smtp smtps telnet tftp ws wss
> Features: alt-svc asyn-rr AsynchDNS brotli HSTS HTTP2 HTTP3 HTTPS-proxy HTTPSRR IDN IPv6 Largefile libz NTLM PSL SSL SSLS-EXPORT threadsafe TLS-SRP TrackMemory UnixSockets zstd
> ```
> 继续使用`trurl --version`查看trurl版本，看看trurl是否安装成功，如果安装成功应返回如下内容
> ```
> trurl version 0.16.1 libcurl/8.17.0 [built-with 8.17.0]
> features: get-empty imap-options no-guess-scheme normalize-ipv4 punycode punycode2idn url-strerror white-space zone-id
> ```
> 如果都返回正确，那么恭喜你模块安装成功

到这里就大功告成，但大部分情况通过模块安装的软件要使用超级用户权限下的shell才可以使用

同时我测试nvim时发现nvim移植后的兼容性不太好，给大家提个醒
