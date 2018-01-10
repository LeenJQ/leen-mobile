# 手势

## 替换click 300ms 延迟

### 使用 fastclick 库
https://github.com/ftlabs/fastclick

> fastclick 既可以绑定在全局body，也可以绑定在指定的 DOM click事件上

### 原声简单实现

```javascript
document.addEventListener('touchstart',function (event) {  
  if(event.touches.length>1){  
      event.preventDefault();  
  }  
})  
var lastTouchEnd=0;  
document.addEventListener('touchend',function (event) {  
  var now=(new Date()).getTime();  
  if(now-lastTouchEnd<=300){  
      event.preventDefault();  
  }  
  lastTouchEnd=now;  
},false)  
```