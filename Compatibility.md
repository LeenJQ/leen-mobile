# 兼容性
___

## 2018年1月截止主流测试浏览器（中国）
> IOS 8+ 
 Android 5+

![移动端](./img/mobile_comp.png)


## 常见问题解决方案

### 清除输入框内阴影
iOS上的几乎任何浏览器输入框（input, textarea）默认有内部阴影，但无法使用 box-shadow 来清除，如果不需要阴影，可以这样关闭：

```css
input,
textarea {
	/* 方法1: 去掉边框 */
	border: 0;

	/* 方法2: 边框色透明 */
	border-color: transparent;

	/* 方法3: 重置输入框默认外观 */
	-webkit-appearance: none;
	appearance: none;
}
```

<a href="retina-border-1px">

### retina 屏幕 border:1px 问题

[问题说明](http://mobile.51cto.com/web-484304.htm)

主要是分辨率高的屏幕下 1px的线会变得粗一点

[解决方案](https://www.jianshu.com/p/7e63f5a32636)


推荐: 
* viewport + rem 实现(淘宝方案)
* 伪类 + transform 实现

```css
.scale-1px{
  position: relative;
  border:none;
}
.scale-1px:after{
  content: '';
  position: absolute;
  bottom: 0;
  background: #000;
  width: 100%;
  height: 1px;
  -webkit-transform: scaleY(0.5);
  transform: scaleY(0.5);
  -webkit-transform-origin: 0 0;
  transform-origin: 0 0;
}
```

```javascript
if(window.devicePixelRatio && devicePixelRatio >= 2){
  document.querySelector('ul').className = 'scale-1px';
}
```