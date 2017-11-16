---
title: CocoaPods最新镜像安装方式和常用相关命令（卸载，降级）
date: 2017-11-15 23:04:43
tags:
---
###安装顺序
> 1、安装brew，安装链接如若更新，请点击[此链接](http://brew.sh)查看
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" 
```
***
> 2、安装Ruby
```
$ brew install ruby
```
***
> 3、安装CocoaPods
  1.  移除现有 Ruby 默认源
```
$ gem sources --remove https://rubygems.org/
```
  2. 使用新的镜像源（非网络上的Taobao源）
```
 $ gem sources -a https://gems.ruby-china.org/
```
  3.  验证是否成功
```
$ gem sources -l
```
  4. 安装CocoaPods
```
$ sudo gem install cocoapods
$ pod setup
```


![等待中](http://upload-images.jianshu.io/upload_images/1505288-d60693d4056982e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---

###监测下载进度

>1、跳转指定文件夹
```
$ cd ~/.cocoapods   
```
2、监测网络下载进度
```
$ du -sh *
```

![监测界面](http://upload-images.jianshu.io/upload_images/1505288-47ff3ae7ec8ccfdf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

ps： 再执行安装CocoaPods时 执行``` $ pod setup```需要等待大约半个多小时时间，有时等待了也会报错，此处可以偷鸡
***
###偷鸡教学

> 1、[点击此处下载文件](http://pan.baidu.com/s/1hsr24uS)```提取密码为52r5 ```下载Repos文件并解压

> 2、打开Terminal，输入命令行 ```open ~/.cocoapods```

> 3、将解压文件替换文件夹Repos

> 4、再次打开Terminal，输入命令行```pod search afn```
> 
> 5、如果出现下图为安装完成


![成功界面](http://upload-images.jianshu.io/upload_images/1505288-751aad7106fdcc8f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



> 查看CocoaPods版本
```
$ pod --version
```

###卸载CocoaPods
> 1. 查看CocoaPods路径
```
$ which pod
```
> 2. 查看CocoaPods位置
```
$ sudo rm -rf 路径 
```
> 3. 查看CocoaPods版本（```-bash: /usr/local/bin/pod: No such file or directory```即删除成功）
```
$ pod --version
```
> 4. 打印gem 下的所有包查看cocoapods版本号
```
$ gem list
```
> 5. 移除程序包(如果要删除依赖包只需要更改“cocoapods”即可)
```
$ sudo gem uninstall cocoapods -v 版本号
```
> 6. 删除repos包（大约300+M）
```
$ rmdir ~/.cocoapods
```

###多版本共存与使用
> 1. 安装指定版本Cocoapods
```
$ sudo gem install cocoapods -v 0.35.0
```
> 2. 使用指定版本Cocoapods
 ```
$ pod _0.35.0_ install,    pod _0.38.2_ install
```