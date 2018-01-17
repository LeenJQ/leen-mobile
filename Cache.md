# 缓存

HTML5 引入的缓存机制让我们可以在没有网络时进行访问

## 离线功能

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