---
title: mvp使用理解
date: 2016-08-05 15:51:01
tags:
---
最近新做了一个项目，尝试了mvp（model，view，presenter）框架。以前一直都使用mvc（model，view，control）的框架开发，activity一直做为上帝类一般的存在，导致这个类越来越臃肿。
比较下了mvc和mvp的区别：

### 优势：
``` bash
降低了耦合度，实现model和view的分离，减少activity的压力。
presenter可以复用，一个presenter可以用于多个view。
view可以进行组件化，从业务场景中脱离出来，可以说view可以做到对业务完全无知，只需要提供一系列的接口给presenter调用即可。
```

### 不足之处：
``` bash
接口和类的暴涨,将Activity中除V之外的繁杂操作搬到P之后依然臃肿不堪。
如果presenter过多地渲染了视图，往往会使得它与特定的视图的联系过于紧密。一旦视图需要变更，那么presenter也需要变更了
```
所以感觉MVP从来都不是救命稻草，只能锦上添花，不能雪中送炭。[附上github上一个比较不错的mvp写的demo](https://github.com/north2014/T-MVP)