# 调试

## 手机远程调试工具

工具名 | 说明 | 连接 |
----- | ---- |----
Fiddler | 一个http监听工具，可以设置手机代理为计算机IP，然后使用Fiddler 去监听请求, 主要用在查看http|[网站](https://www.telerik.com/fiddler)
Chrome Inspect | 手机USB插入到电脑，并开启开发者模式，浏览器里输入chrome://inspect/#devices 就可以看到手机访问浏览器时的监控画面，之前项目用这个调试很好用，但是后来经常不好用，只有空白页面，听说需要翻墙，总之是一个可选方案(似乎还可以通过无限ip和端口号监听网页和node服务器，有机会再研究下)| [教程](http://www.siyuweb.com/tool/2557.html) 
vconsole | 一个 js代码库，安装方便，只要在代码里运行一行代码即可，能监控console,http,查看DOM 元素等 | [github](https://github.com/Tencent/vConsole/blob/dev/README_CN.md)