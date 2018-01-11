# 图片

## 工具
* [markman](http://www.getmarkman.com/): UI设计图元素大小，颜色等信息提取器

<img src="./img/markman.png" height="100">

* [TinyPng](https://tinypng.com/): 在线图片压缩
<img src="./img/tinypng.png" height="100">

## 图片清晰度问题

[参考链接](http://mobile.51cto.com/web-484304.htm)

> 在 dpr=2 的屏幕上，因为1个图片像素对应4个物理像素，所以图片会变得模糊，所以需要传x2的图片，可以通过图片服务器（如七牛），根据dpr，请求带大小参数的图片url，加载不同的图片

[详细说明](./Basic.md)