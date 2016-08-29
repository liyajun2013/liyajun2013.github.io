---
title: 沉浸式（Translucent）状态栏
date: 2016-08-29 15:20:26
tags:
---
沉浸式状态栏在4.4（api=19）一下没法实现，在4.4~4.x上的显示有一点渐变的效果，在5.x(api=21)以上可以实现一体色。不过在4.4上和5.x以上的实现方式不同。[附上git上为我们实现的很完美的一个工具](https://github.com/laobie/StatusBarUtil)
``` bash
StatusBarUtil.setColor(this, getResources().getColor(R.color.colorPrimaryDark),0);
```
代码中主要设置上面这句函数，要在setContentView()后面，在BaseActivity里写可以写到onResume()里面

``` bash
activity.getWindow().addFlags(WindowManager.LayoutParams.FLAG_TRANSLUCENT_STATUS)
```
4.4上设置可以使得状态栏透明，再添加一块自己的view在标题栏后面，状态栏透明后就能显示自定义的view。最后设置根布局setFitsSystemWindows(true)（使根布局从状态栏下面开始）和setClipToPadding(true)（listview滑动的时候不会滑到状态栏后面）

``` bash
activity.getWindow().addFlags(WindowManager.LayoutParams.FLAG_DRAWS_SYSTEM_BAR_BACKGROUNDS);
activity.getWindow().clearFlags(WindowManager.LayoutParams.FLAG_TRANSLUCENT_STATUS);
activity.getWindow().setStatusBarColor(Color.TRANSPARENT);
```
5.x上比较简单，设置上面3句函数就可以了，不过要注意的是6.0上状态栏有灰条盖住状态栏颜色，使得看上去颜色变深，不过StatusBarUtil这个工具里面提供我们alpha值得设置，设置为0就可以显示统一的颜色。

