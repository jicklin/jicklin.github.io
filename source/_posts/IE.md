---
title: JAVA下载文件IE乱码
date: 2017-05-10 16:08:59
tags:
categories:
---

> 今天写了一个freemaker导出word的工程，导出的文件名中有中文，比较习惯在测试时用Chrome浏览器，快要把更新发给现场了，想起来现场用的是IE浏览器，保险起见还是也测试下，一测试发现糟了乱码了。
> 有网有百度不怕，然后查查查发现了还挺多人有这个问题的，应该是由于内核不一样吧
> 发现都是通过判断请求的头来进行浏览器判断，虽然网上有大神写出来的但是还是想自己按照步骤走一下。
> 现在Chrome中跟踪到了请求的头在`network`中很容易看出来大概是这个样子
```
User-Agent:Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/57.0.2987.133 Safari/537.36
```
再去IE看看呗，一看蒙蔽了，这网络中怎么不管怎么请求都是屁都看不到，纠结了，还是用工具吧，安利一款工具呀 [Fiddler](http://www.telerik.com/fiddler) 跟踪请求特好用
`User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko`

后边这个`like Gecko`就是关键字啦 据说老的IE还有`msie`这个东东
程序就这样写就行啦
```
String userAgent=request.getHeader("User-Agent").toLowerCase();
            //如果是IE
            if(userAgent.contains("msie") || userAgent.contains("like gecko")){
                fileName= URLEncoder.encode(fileName,"utf-8");
            }else{
                fileName=new String(fileName.getBytes("utf-8"),"ISO-8859-1");
            }
```