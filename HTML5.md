# HTML5

## 离线和存储
[查看缓存章节](./Cache.md)

## 中立感应

### 方向事件

**deviceorientation 事件**

手机围绕 
* X轴: Beta
* Y轴: Gamma
* Z轴: Alpha

```js
window.addEventListener('deviceorientation', handler, true)

function handler(DeviceOrientationEvent) {
  /* 
  DeviceOrientationEvent {
    absolute,
    alpha,
    beta,
    gamma
  }
  */
}
```

### 移动事件

**devicemotion 事件**

```js
window.addEventListener('devicemotion', handler, false);

function handler(DeviceMotionEvent) {
  /*
  DeviceMotionEvent {
    acceleration, // 设备在X,Y,Z 轴方向上移动的距离，已抵消（不包含）重力加速
    accelerationIncludingGravity, // 设备在X，Y，Z 方向上移动的距离，包含重力加速
    rotationRate, // 设备在 Alpha, Beta, Gamma 三个方向旋转的角度
    interval, // 从设备获取数据的频率，单位是毫秒
  }
  */
}
```

### 摇一摇实例

```js
var SHAKE_SPEED_THRESHOLD = 300;// 摇动速度阈值
var lastTime = 0;// 上次变化的时间
var x = y = z = lastX = lastY = lastZ = 0;// 位置变量初始化

function motionHandler(evt) {
  var acceleration = evt.accelerationIncludingGravity;// 取得包含重力加速的位置信息
  var curTime = Date.now();// 取得当前时间
  if ((curTime - lastTime) > 120) {// 判断
    var diffTime = curTime - lastTime;// 两次变化时间差
    lastTime = curTime;// 保存此次变化的时间
    x = acceleration.x;
    y = acceleration.y;
    z = acceleration.z;
    var speed = Math.abs(x + y + z - lastX - lastY - lastZ) / diffTime * 1000;// 计算速度
    if (speed > SHAKE_SPEED_THRESHOLD) {// 速度是否大于预设速度
      alert("你摇动了手机");
    }
    lastX = x; // 保存此次变化的位置x
    lastY = y; // 保存此次变化的位置y
    lastZ = z; // 保存此次变化的位置z
  }
}
if (window.DeviceMotionEvent) {
  window.addEventListener('devicemotion', motionHandler, false);
} else {
  alert('您的设备不支持位置感应');
}
```
## 地理位置

```html
<div>
    <div>我的位置是：<span id="pos"></span></div>
    <div id="map"></div>
  </div>
  <script type="text/javascript">
    function showPosition(position) {
      var latlon = position.coords.latitude + ',' + position.coords.longitude;
      var img_url = 'http://maps.googleapis.com/maps/api/staticmap?center='
      + latlon + '&zoom=14&size=400x300&sensor=false';
      document.getElementById('pos').innerHTML = latlon;
      document.getElementById('map').innerHTML = '<img src="' + img_url + '" />';
    }
    function success(position){
      console.log('获取位置成功：', position.coords);
      showPosition(position);
    }
    function error(positionError){
      console.log('获取位置失败：', positionError);
    }
    var options = {
      enableHighAccuracy: false,
      timeout: 30000,
      maximumAge: 0
    }
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(success, error, options);
    } else {
      alert('您的浏览器不支持Geolocatioin!')
    }

    // var watchId = navigator.geolocation.watchPosition(success, error, options);
    // navigator.geolocation.clearWatch(watchId)
  </script>
```

## 视频

```html
<audio controls>
    <source src="vincent.ogg" />
    <source src="vincent.mp3" /> 你的浏览器不支持Audio标记
</audio>

<section>
    <h3>自定义播放行为</h3>
    <audio id="audio">
        <source src="vincent.ogg" />
        <source src="vincent.mp3" /> 你的浏览器不支持Audio标记
    </audio>
    <p>
        <button id="btnPlay">Play</button>
        <button id="btnPause">Pause</button>
    </p>
    <script>
        var audio = document.getElementById("audio")
        document.getElementById("btnPlay").addEventListener("click", function(){
            audio.play()
        })
        document.getElementById("btnPause").addEventListener("click", function(){
            audio.pause()
        })
    </script>
</section>
```

## 摄像头

[MDN 文档](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)

```js
navigator.mediaDevices.getUserMedia(constraints)
.then(function(stream) {
  /* use the stream */
})
.catch(function(err) {
  /* handle the error */
});
```

### 兼容代码库
[adapter.js](https://github.com/webrtc/adapter)


## 参考
  * MDN
  * 《 移动 Web 前端高校开发实践 》