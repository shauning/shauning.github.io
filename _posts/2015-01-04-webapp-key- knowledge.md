---
layout: post
title: Webapp Key Knowledge
description: "移动页面制作一些点"
modified: 2015-01-04
tags: [mobile]
image:
  feature: abstract-3.jpg
  credit: Shaun
  creditlink: https://500px.com/photo/81228191/shenzhen-bay-by-shaun-huang
---
1.Meta:

{% highlight html linenos %}
{% raw %}
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta name="viewport" content="device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no;" />
<meta name="apple-mobile-web-app-capable" content="yes" /> <!-- 添加到桌面后打开是否启用全屏 -->       
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
<!-- 
	指定的iphone中safari顶端的状态条的样式
	default 默认值。
	black 状态栏背景是黑色。
	black-translucent 状态栏背景是黑色半透明。
	如果设置为 default 或 black ,网页内容从状态栏底部开始。
	如果设置为 black-translucent ,网页内容充满整个屏幕，顶部会被状态栏遮挡。
-->        
<meta name="format-detection" content="telephone=no" /> <!-- 忽略将页面中的数字识别为电话号码 -->    
<meta name="Author" contect="Mr.He"/ > <!-- 作者 -->
{% endraw %}
{% endhighlight %}

2.Touch icon:

apple-touch-icon 图片自动处理成圆角和高光等效果；
apple-touch-icon-precomposed 禁止系统自动添加效果，直接显示设计原图。
{% highlight html linenos %}
{% raw %}
<!-- iPhone 和 iTouch，默认 57x57 像素，必须有 -->
<link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png" />

<!-- iPad，72×72 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" sizes="72x72" href="/apple-touch-icon-72x72-precomposed.png" />

<!-- Retina iPhone 和 Retina iTouch，114×114 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="/apple-touch-icon-114x114-precomposed.png" />

<!-- Retina iPad，144×144 像素，可以没有，但推荐有 -->
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="/apple-touch-icon-144x144-precomposed.png" />
{% endraw %}
{% endhighlight %}

3.Startup:

iPad 的启动画面是不包括状态栏区域的;
iPhone 和 iPod touch 的启动画面是包含状态栏区域的。
{% highlight html linenos %}
{% raw %}
<!-- iPad 竖屏 768 x 1004（标准分辨率） -->
<link rel="apple-touch-startup-image" sizes="768x1004" href="/splash-screen-768x1004.png" /> 

<!-- iPad 竖屏 1536x2008（Retina） -->
<link rel="apple-touch-startup-image" sizes="1536x2008" href="/splash-screen-1536x2008.png" />

<!-- iPad 横屏 1024x748（标准分辨率） -->
<link rel="apple-touch-startup-image" sizes="1024x748" href="/Default-Portrait-1024x748.png" />

<!-- iPad 横屏 2048×1496（Retina） -->
<link rel="apple-touch-startup-image" sizes="2048x1496" href="/splash-screen-2048x1496.png" />

<!-- iPhone/iPod Touch 竖屏 320×480 (标准分辨率) -->
<link rel="apple-touch-startup-image" href="/splash-screen-320x480.png" />

<!-- iPhone/iPod Touch 竖屏 640×960 (Retina) -->
<link rel="apple-touch-startup-image" sizes="640x960" href="/splash-screen-640x960.png" />

<!-- iPhone 5/iPod Touch 5 竖屏 640×1136 (Retina) -->
<link rel="apple-touch-startup-image" sizes="640x1136" href="/splash-screen-640x1136.png" />
{% endraw %}
{% endhighlight %}

4.App banner:

添加智能 App 广告条 Smart App Banner（iOS 6+ Safari）。
{% highlight html linenos %}
{% raw %}
<meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL">
{% endraw %}
{% endhighlight %}

