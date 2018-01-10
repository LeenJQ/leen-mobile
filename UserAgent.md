# 手机浏览器信息

```javascript
// 是否为浏览器
export const inBrowser = typeof window !== 'undefined'
// 是否在微信
export const inWeex = typeof WXEnvironment !== 'undefined' && !!WXEnvironment.platform
// 是否为小程序
export const weexPlatform = inWeex && WXEnvironment.platform.toLowerCase()
// user agent
export const UA = inBrowser && window.navigator.userAgent.toLowerCase()
// 是否为IE浏览器
export const isIE = UA && /msie|trident/.test(UA)
export const isIE9 = UA && UA.indexOf('msie 9.0') > 0
export const isEdge = UA && UA.indexOf('edge/') > 0
// 是否为安卓系统
export const isAndroid = (UA && UA.indexOf('android') > 0) || (weexPlatform === 'android')
// 是否为IOS系统
export const isIOS = (UA && /iphone|ipad|ipod|ios/.test(UA)) || (weexPlatform === 'ios')
// 是否为Chrome
export const isChrome = UA && /chrome\/\d+/.test(UA) && !isEdge

```