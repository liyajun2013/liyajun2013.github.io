---
title: apk打包流程
date: 2017-04-18 14:38:40
tags:
---
###流程
``` bash
编译src文件，生成class文件
将class文件编译成dex文件
编译资源文件（不包括assets，raw和so等文件），成功R文件
将上述两个以及一些依赖进行联合编译成为一个apk
压平
签名
```

###小结
``` bash
除了assets和res/raw资源被原装不动地打包进APK之外，其它的资源都会被编译或者处理；
除了assets资源之外，其它的资源都会被赋予一个资源ID；
打包工具负责编译和打包资源，编译完成之后，会生成一个resources.arsc文件和一个R.java，前者保存的是一个资源索引表，后者定义了各个资源ID常量。
应用程序配置文件AndroidManifest.xml同样会被编译成二进制的XML文件，然后再打包到APK里面去。
应用程序在运行时通过AssetManager来访问资源，或通过资源ID来访问，或通过文件名来访问。
```