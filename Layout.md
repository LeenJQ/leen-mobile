# 布局

## rem 布局

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