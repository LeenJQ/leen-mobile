# 缓存

## 离线功能

>HTML5 引入的缓存机制让我们可以在没有网络时进行访问

* 离线资源缓存
* 在线状态监测
* 本地数据存储

### 离线描述文件

 * .manifest
 * .appcache (推荐)

**mime-type**: text/cache-manifest

> 必须为 UTF-8

**例子**

.offline.appcache 文件
```
CACHE MANIFEST
#cache 之后的资源都会被缓存
CACHE:
main.html
style.css
main.js
#network之后的资源不会被缓存，总是从线上获取
NETWORK:
account/
```

HTML 文件
```html
<html manifest="./offline.appcache">
```

### js API
```js
// 判断是否上线
if(window.navigator.onLine)

/**
* online 和 onoffline 兼容性差
*/
// 监听上线事件
window.online = function(){}
// 监听离线事件
window.onoffline = function(){}
```

### 本地存储

使用 localStorage

```js
localStorage.addItem('data', value)
localStorage.removeItem('data')
```

[localStorage & sessionStorage 基础](./Basic.md#local-storage)

## 离线资源更新

### Service Worker
Service Worker 是一段运行在浏览器后台进程的脚本，独立于当前页面，
不参与DOM 操作，但是可以通过 postMessage 与页面通信

### Service Worker 功能
* 后台消息传递
* 网络代理
* 离线缓存
* 消息推送

[更多关于 Service Worker](./Basic.md#service-worker)