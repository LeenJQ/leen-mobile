# 布局

## rem 布局

[参考连接](https://segmentfault.com/a/1190000007526917)

### 方法1： 1rem=100px 布局
先在 header 里定义 meta-view 让页面不可缩放

```html
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no, shrink-to-fit=no">
```
然后在js代码里面写入下面代码

> 这个代码会根据手机屏幕宽度计算全局font-size，这个size能让我们用 1rem = 100px 的比例写css里的大小

> ***750是UI设计图的宽度，这里如果不一样需要替换***

```javascript
(function (doc, win) {
  var docEl = doc.documentElement,
      resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
      recalc = function () {
          var clientWidth = docEl.clientWidth;
          if (!clientWidth) return;
          if(clientWidth>=750){
              docEl.style.fontSize = '100px';
          }else{
              docEl.style.fontSize = 100 * (clientWidth / 750) + 'px';
          }
      };
  if (!doc.addEventListener) return;
  win.addEventListener(resizeEvt, recalc, false);
  doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);  
```
这样就可以在 css 里方便的计算 rem 了

```css
input {
  width: 100%;
  height: 1.3rem; /* 1rem = 100px */
  font-size: 0.32rem;
}
```

### 方案2：dpr 设置缩放比

[淘宝方案参考链接](https://github.com/amfe/lib-flexible/blob/2.0/index.js)

```javascript
// 获取 dpr
var scale = 1 / devicePixelRatio;  

// 设置页面缩放比
 document.querySelector('meta[name="viewport"]').setAttribute('content','initial-scale='+ scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');

 // 动态计算html 的 font-size
 document.documentElement.style.fontSize = document.documentElement.clientWidth / 10 + 'px'；
```

### 旧的方案

***不推荐***, 使用 sass 编写函数 px2rem, 然后每次调用 px2rem 转换

```scss
$designWidth: 750; 
@function px2rem( $px ){
	@return $px*320/$designWidth/20 + rem;
}

#header{
	width: px2rem(640);
}
```
