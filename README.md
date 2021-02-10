# wx-wow


该项目为提供微信小程序一套便捷好用动画执行方案， 通过添加简单的动画类名和一些简单的参数，即可实现想要的动画效果。灵感来源 [WOW.js](https://github.com/matthieua/WOW)

wx-wow 需要 调试小程序基础库  `>2.5`

仓库地址： [@Five-great/wx-wow](https://github.com/Five-great/wx-wow)

# 下载

直接通过 `git` 下载 `wx-wow` 源代码，并将 `src` 目录拷贝到自己的项目中
```bash
git clone https://github.com/Five-great/wx-wow.git
```

通过 `npm`  或 `cnpm` 下载

 ```bash
  npm install --save wx-wow
 ```
 下载后目录结构为
```javscript

|-- miniprogram_npm
|   |-- wx-wow
|   |   |-- index.js
|   |   |-- index.map
|   |   |-- wxWOW.wxs
|   |   |-- wxWOW.wxss
|-- src
|   |-- wxWOW.js
|   |-- wxWOW.wxss
|   |-- wxWOW.wxss
|-- package-lock.json
|-- package.json
|-- README.md

```

# 使用
将 `src` 目录中所有文件复制到微信小程序目录`utils`中（`wxWOW.js`，`wxWOW.wxss`，`wxWOW.wxss`）


### 1. 在 `app.js` 中引入 `wxWOW.js`
```javascript
  Page = require('./utils/wxWOW')
  App({
     ...
  })
```

### 2. 在 `app.wxss` 引入`wxWOW.wxss` ( 动效样式来源自 [animate.css(点击查看动效名与效果)](https://animate.style)  )

```css
 /**app.wxss**/
 @import "./utils/wxWOW.wxss";

```

### 3. 在需要的页面引入 `wxWOW.wxs` 并导出模块 命名为 `"wx"` 同时监听绑定 `{{ wxwow }} ` 改变时触发 `WOWChange` 函数 执行动画渲染。

```javascript

  <wxs src="../../utils/wxWOW.wxs" module="wx" />
  <view change:prop="{{wx.WOWChange}}" prop="{{wxwow}}" >
       ...
 </view>

```

### 4. 在需要加入动效的地方的 `class` 加入 `" {{wx.WOW()}}   <动效名称>"`， 例如 `" {{wx.WOW()}} bounceInUp "`， 同时需要给该动效分配一个 `id `具体通过  `{{wx.WOWId()}}`  去自动分配到 `data-wx-wow-id` 上 ，并且确保添加动画的display 属性为 块状 或行块状，不能为行类样式 如下面的例子1。

```html
 //例子1：
 <view class=" {{wx.WOW()}} bounceInUp"  data-wx-wow-id="{{wx.WOWId()}}" > ... </view>
```

#### 额外参数

 此外还可以控制动效的一些过程例如:
  
  动效名称: `data-wx-wow-name`    (bounceInUp , fadeInLeft,...)
  
  动效延时： `data-wx-wow-delay `         （ 300ms , 0.3s, 4s ...）

  动效持续时间：`data-wx-wow-duration`    （ 300ms , 0.3s, 4s ...）
  
  距离可视区域多少开始执行动效:  `data-wx-wow-offset` (整数) （ 0 , 100, 50 ...）

  动效执行次数: `data-wx-wow-iteration`   ( 1, 5, infinite, ...)


```html
 <view class="{{wx.WOW()}} bounceInUp"  data-wx-wow-id="{{wx.WOWId()}}"  data-wx-wow-delay="0.8s" data-wx-wow-offset="500" > ... </view>
 
 <image src="xxxx.png" class="{{wx.WOW()}} swing"  data-wx-wow-id="{{wx.WOWId()}}"  data-wx-wow-delay="0.8s" data-wx-wow-offset="500" data-wx-wow-iteration="5" />

<view class="{{wx.WOW()}} fadeOut"  data-wx-wow-id="{{wx.WOWId()}}"  data-wx-wow-delay="0.8s"  data-wx-wow-duration="3s" > ... </view>
```
## 升阶配置

 #### 若需升阶配置 则需改变设置方式，在 `class` 加入 `" {{wx.WOW()}}"` ,同时加入 data-wx-wow-name="`<动效名>`" 同时需要给该动效分配一个 `id `具体通过  `{{wx.WOWId()}}`  去自动分配到 `data-wx-wow-id` 上 ，并且确保添加动画的display 属性为 块状 或行块状，不能为行类样式 如下面的例子2

 ```html
 //例2：
  <view class=" {{wx.WOW()}} " data-wx-wow-name="bounceInUp" data-wx-wow-id="{{wx.WOWId()}}" > ... </view>
```
#### 触发实现离场动效
 ##### 通过触发 `wx.WOWOut()` 函数，来触发离场动效，需保证 `data-wx-wow-name`有值，默认为 `data-wx-wow-name`中相反的动效名（例如 bounceInUp 相反动效为 bounceOutUp）。触发回调对应逻辑层 `wxWOWTap`（可以执行跳转页面或其他处理）

 ```html
  <view class=" {{wx.WOW()}} " data-wx-wow-name="bounceInUp" data-wx-wow-id="{{wx.WOWId()}}"  catchtap="{{wx.WOWOut}}" > ... </view>
```

```js
Page({
  ...
  wxWOWTap: function(event){
      console.log(event)
     setTimeout(()=>{
      event.target.dataset.idx?wx.navigateTo({url: '/pages/xxx/xxx?idx='+event.target.dataset.idx}):''
     },600)
  }
  ...
})
```
##### 可选配置

 此外还可以控制动效的一些过程例如:
  
  动效名称: `data-wx-wow-outName` [默认`data-wx-wow-name`取相反动效 ]    (bounceOutUp , fadeOutLeft,...)
  
  动效延时： `data-wx-wow-outDelay` [默认与 `data-wx-wow-delay` 相同 ]         （ 300ms , 0.3s, 4s ...）

  动效持续时间：`data-wx-wow-outDuration`    [默认与 `data-wx-wow-duration` 相同 ]   （ 300ms , 0.3s, 4s ...）

  动效执行次数: `data-wx-wow-outIteration`  [默认与 `data-wx-wow-iteration` 相同 ] ( 1, 5, infinite, ...)

#### 设置页面重复动效 （进入页面重新刷新执行动效）

```js
Page({
   data: {
      wxwowConfig: {
          repeat: true //是否重复刷新开启动画 默认 true , 当设为 false，则该页面未销毁前，只会执行一次动效
      }
   }
})
```

#### 其他设置
###### 设置某单个动效，重复执行（优先级高于设置页面重复动效），给 类名 `class` 加入 `wxwow-repeat`

```html
  <view class=" {{wx.WOW()}} wxwow-repeat " data-wx-wow-name="bounceInUp" data-wx-wow-id="{{wx.WOWId()}}"  catchtap="{{wx.WOWOut}}" > ... </view>
```

###### 设置某单个动效，仅仅执行一次（优先级高于设置页面重复动效），给 类名 `class` 加入 `wxwow-once`

```html
  <view class=" {{wx.WOW()}} wxwow-once" data-wx-wow-name="bounceInUp" data-wx-wow-id="{{wx.WOWId()}}"  catchtap="{{wx.WOWOut}}" > ... </view>
```

## Demo
[点击查看代码片段](https://developers.weixin.qq.com/s/llE4M7m67rnC)
## 支持


## 欢迎 点赞 ，Fork , 提 Issues

qq邮箱： fivecc@qq.com
