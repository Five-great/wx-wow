# -wx-wow

##使用方法：
 主要用到 wxWOW.js , wxWOW.wxs, wxWOW.wxss，共计3个部分。
 
 wxWOW.js  需在全局应用（app）
 
```javascript
  Page = require('./utils/wxWOW')
  App({
     ...
  })
```

<h1><a id="user-content-wx-wow" class="anchor" aria-hidden="true" href="#wx-wow"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>wx-wow</h1>
<p>该项目为提供微信小程序一套便捷好用动画执行方案， 通过添加简单的动画类名和一些简单的参数，即可实现想要的动画效果。灵感来源 <a href="https://github.com/matthieua/WOW">WOW.js</a></p>
<p>wx-wow 需要 调试小程序基础库  <code>&gt;2.5</code></p>
<p>仓库地址： <a href="https://github.com/Five-great/wx-wow">@Five-great/wx-wow</a></p>
<h1><a id="user-content-下载" class="anchor" aria-hidden="true" href="#下载"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>下载</h1>
<p>直接通过 <code>git</code> 下载 <code>wx-wow</code> 源代码，并将 <code>src</code> 目录拷贝到自己的项目中</p>
<div class="highlight highlight-source-shell"><pre>git clone https://github.com/Five-great/wx-wow.git</pre></div>
<p>通过 <code>npm</code>  或 <code>cnpm</code> 下载</p>
<div class="highlight highlight-source-shell"><pre> npm install --save wx-wow</pre></div>
<p>下载后目录结构为</p>
<pre lang="javscript"><code>

+-- src
|   |-- wxWOW.js
|   |-- wxWOW.wxs
|   |-- wxWOW.wxss
|   |-- wxWOW.min.js
|   |-- wxWOW.min.wxs
|   |-- wxWOW.min.wxss
|-- package-lock.json
|-- package.json
+-- README.md

</code></pre>
<h1><a id="user-content-使用" class="anchor" aria-hidden="true" href="#使用"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>使用</h1>
<p>将 <code>src</code> 目录中所有文件复制到微信小程序目录<code>utils</code>中（<code>wxWOW.js</code>，<code>wxWOW.wxss</code>，<code>wxWOW.wxss</code>）</p>
<h3><a id="user-content-1-在-appjs-中引入-wxwowjs" class="anchor" aria-hidden="true" href="#1-在-appjs-中引入-wxwowjs"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>1. 在 <code>app.js</code> 中引入 <code>wxWOW.js</code></h3>
<div class="highlight highlight-source-js"><pre>  <span class="pl-v">Page</span> <span class="pl-c1">=</span> <span class="pl-en">require</span><span class="pl-kos">(</span><span class="pl-s">'./utils/wxWOW'</span><span class="pl-kos">)</span>
  <span class="pl-v">App</span><span class="pl-kos">(</span><span class="pl-kos">{</span>
     ...
  <span class="pl-kos">}</span><span class="pl-kos">)</span></pre></div>
<h3><a id="user-content-2-在-appwxss-引入wxwowwxss--动效样式来源自-animatecss点击查看动效名与效果--" class="anchor" aria-hidden="true" href="#2-在-appwxss-引入wxwowwxss--动效样式来源自-animatecss点击查看动效名与效果--"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>2. 在 <code>app.wxss</code> 引入<code>wxWOW.wxss</code> ( 动效样式来源自 <a href="https://animate.style" rel="nofollow">animate.css(点击查看动效名与效果)</a>  )</h3>
<div class="highlight highlight-source-css"><pre> <span class="pl-c">/**app.wxss**/</span>
 <span class="pl-k">@import</span> <span class="pl-s">"./utils/wxWOW.wxss"</span>;</pre></div>
<h3><a id="user-content-3-在需要的页面引入-wxwowwxs-并导出模块-命名为-wx-同时监听绑定--wxwow---改变时触发-wowchange-函数-执行动画渲染" class="anchor" aria-hidden="true" href="#3-在需要的页面引入-wxwowwxs-并导出模块-命名为-wx-同时监听绑定--wxwow---改变时触发-wowchange-函数-执行动画渲染"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>3. 在需要的页面引入 <code>wxWOW.wxs</code> 并导出模块 命名为 <code>"wx"</code> 同时监听绑定 <code>{{ wxwow }} </code> 改变时触发 <code>WOWChange</code> 函数 执行动画渲染。</h3>
<div class="highlight highlight-source-js"><pre>  <span class="pl-c1">&lt;</span><span class="pl-ent">wxs</span> <span class="pl-c1">src</span><span class="pl-c1">=</span><span class="pl-s">"../../utils/wxWOW.wxs"</span> <span class="pl-c1">module</span><span class="pl-c1">=</span><span class="pl-s">"wx"</span> /<span class="pl-c1">&gt;</span>
  <span class="pl-c1">&lt;</span><span class="pl-s1">view</span><span class="pl-kos"></span> change:<span class="pl-s1">prop</span><span class="pl-c1">=</span><span class="pl-s">"{{wx.WOWChange}}"</span><span class="pl-kos"></span> <span class="pl-s1">prop</span><span class="pl-c1">=</span><span class="pl-s">"{{wxwow}}"</span> <span class="pl-c1">&gt;</span>
       ...
 <span class="pl-c1">&lt;</span>/<span class="pl-ent">view</span><span class="pl-c1">&gt;</span></pre></div>
<h3><a id="user-content-4-在需要加入动效的地方的-class-加入--wxwow---动效名称-例如--wxwow-bounceinup--同时需要给该动效分配一个-id-具体通过--wxwowid--去自动分配到-data-wx-wow-id-上-并且确保添加动画的display-属性为-块状-或行块状不能为行类样式-如下面的例子" class="anchor" aria-hidden="true" href="#4-在需要加入动效的地方的-class-加入--wxwow---动效名称-例如--wxwow-bounceinup--同时需要给该动效分配一个-id-具体通过--wxwowid--去自动分配到-data-wx-wow-id-上-并且确保添加动画的display-属性为-块状-或行块状不能为行类样式-如下面的例子"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>4. 在需要加入动效的地方的 <code>class</code> 加入 <code>" {{wx.WOW()}}   &lt;动效名称&gt;"</code>， 例如 <code>" {{wx.WOW()}} bounceInUp "</code>， 同时需要给该动效分配一个 <code>id </code>具体通过  <code>{{wx.WOWId()}}</code>  去自动分配到 <code>data-wx-wow-id</code> 上 ，并且确保添加动画的display 属性为 块状 或行块状，不能为行类样式 如下面的例子。</h3>
<div class="highlight highlight-text-html-basic"><pre> <span class="pl-kos">&lt;</span><span class="pl-ent">view</span> <span class="pl-c1">class</span>="<span class="pl-s"> {{wx.WOW()}} bounceInUp</span>"  <span class="pl-c1">data-wx-wow-id</span>="<span class="pl-s">{{wx.WOWId()}}</span>" <span class="pl-kos">&gt;</span> ... <span class="pl-kos">&lt;/</span><span class="pl-ent">view</span><span class="pl-kos">&gt;</span></pre></div>
<h4><a id="user-content-额外参数" class="anchor" aria-hidden="true" href="#额外参数"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>额外参数</h4>
<p>此外还可以控制动效的一些过程例如:</p>
<p>动画延时： <code>data-wx-wow-delay </code>         （ 300ms , 0.3s, 4s ...）</p>
<p>动画持续时间：<code>data-wx-wow-duration</code>    （ 300ms , 0.3s, 4s ...）</p>
<p>距离可视区域多少开始执行动画:  <code>data-wx-wow-offset</code> (整数) （ 0 , 100, 50 ...）</p>
<p>动画执行次数: <code>data-wx-wow-iteration</code>   ( 1, 5, infinite, ...)</p>
<div class="highlight highlight-text-html-basic"><pre> <span class="pl-kos">&lt;</span><span class="pl-ent">view</span> <span class="pl-c1">class</span>="<span class="pl-s">{{wx.WOW()}} bounceInUp</span>"  <span class="pl-c1">data-wx-wow-id</span>="<span class="pl-s">{{wx.WOWId()}}</span>"  <span class="pl-c1">data-wx-wow-delay</span>="<span class="pl-s">0.8s</span>" <span class="pl-c1">data-wx-wow-offset</span>="<span class="pl-s">500</span>" <span class="pl-kos">&gt;</span> ... <span class="pl-kos">&lt;/</span><span class="pl-ent">view</span><span class="pl-kos">&gt;</span>
 
 <span class="pl-kos">&lt;</span><span class="pl-ent">image</span> <span class="pl-c1">src</span>="<span class="pl-s">xxxx.png</span>" <span class="pl-c1">class</span>="<span class="pl-s">{{wx.WOW()}} swing</span>"  <span class="pl-c1">data-wx-wow-id</span>="<span class="pl-s">{{wx.WOWId()}}</span>"  <span class="pl-c1">data-wx-wow-delay</span>="<span class="pl-s">0.8s</span>" <span class="pl-c1">data-wx-wow-offset</span>="<span class="pl-s">500</span>" <span class="pl-c1">data-wx-wow-iteration</span>="<span class="pl-s">5</span>" /&gt;

<span class="pl-kos">&lt;</span><span class="pl-ent">view</span> <span class="pl-c1">class</span>="<span class="pl-s">{{wx.WOW()}} fadeOut</span>"  <span class="pl-c1">data-wx-wow-id</span>="<span class="pl-s">{{wx.WOWId()}}</span>"  <span class="pl-c1">data-wx-wow-delay</span>="<span class="pl-s">0.8s</span>"  <span class="pl-c1">data-wx-wow-duration</span>="<span class="pl-s">3s</span>" <span class="pl-kos">&gt;</span> ... <span class="pl-kos">&lt;/</span><span class="pl-ent">view</span><span class="pl-kos">&gt;</span></pre></div>
<h2><a id="user-content-demo" class="anchor" aria-hidden="true" href="#demo"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Demo</h2>
<p><a href="https://developers.weixin.qq.com/s/llE4M7m67rnC" rel="nofollow">点击查看代码片段</a></p>
<h2>应用实列</h2>
<p style="text-align: center;" >
<img style="display: inline-block;" src="https://s3.ax1x.com/2021/03/11/6Y53a4.gif"/>
<img  style="display: inline-block;" src="https://s3.ax1x.com/2021/03/11/6tisR1.jpg" />
</p>
<h2><a id="user-content-支持" class="anchor" aria-hidden="true" href="#支持"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>支持</h2>
<h2><a id="user-content-欢迎-点赞-fork--提-issues" class="anchor" aria-hidden="true" href="#欢迎-点赞-fork--提-issues"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>欢迎 点赞 ，Fork , 提 Issues</h2>
<p>qq邮箱： <a href="mailto:fivecc@qq.com">fivecc@qq.com</a></p>