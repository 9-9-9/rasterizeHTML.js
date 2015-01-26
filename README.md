rasterizeHTML.js
================

<a href="https://www.npmjs.org/package/rasterizehtml">
    <img src="https://badge.fury.io/js/rasterizehtml.svg"
        align="right" alt="NPM version" height="18">
</a>

呈现HTML到浏览器的画布。


参见[API](https://github.com/cburgmer/rasterizeHTML.js/wiki/API).

安装
-------

    $ npm install rasterizehtml

然后包括与 `node_modules/rasterizehtml/dist/rasterizeHTML.allinone.js` or require through [browserify](https://github.com/substack/node-browserify).

例
-------

```js
var canvas = document.getElementById("canvas");
rasterizeHTML.drawHTML('Some <span style="color: green; font-size: 20px;">HTML</span> with an image <img src="someimg.png" />', canvas);
```

参见[示例页面](https://github.com/cburgmer/rasterizeHTML.js/wiki/Examples) and [the examples shipped with the code](https://github.com/cburgmer/rasterizeHTML.js/tree/master/examples).

它是如何工作的
----------------

出于安全原因，渲染HTML到画布量剧烈有限。火狐通过`ctx.drawWindow提供这样的功能（）`，但只能用镀铬特权（见https://developer.mozilla.org/en/Drawing_Graphics_with_Canvas）。

如在http://robert.ocallahan.org/2011/11/drawing-dom-content-to-canvas.html和https://developer.mozilla.org/en/HTML/Canvas/Drawing_DOM_objects_into_a_canvas描述但是也可以通过嵌入HTML成SVG图像作为`<foreignObject>`然后通过`ctx.drawImage绘制生成的图像（）`。

在另外的SVG不允许链接到外部资源等rasterizeHTML.js将加载外部图像，字体和样式表，并通过内嵌存储它们[数据：URI的]（http://en.wikipedia.org/wiki/Data_URI_scheme）（分别或内嵌式的元素）。

限制
-----------

所有资源（HTML页面，CSS，图片，字体和JS）需要绘制的页面只能如果加载从[同源]（https://developer.mozilla.org/en-US/docs/Web / JavaScript/ Same_origin_policy_for_JavaScript），除非像[CORS]技术（http://enable-cors.org）被使用。 I.E. `drawURL（）`只能从同一个域作为当前页面加载网页和所有借鉴该域的方法同样可以只嵌入的造型和形象。

该代码是在火狐，Chrome和Safari浏览器进行测试。然而[IE最高版本为11不兑现`<foreignObject>`]（https://status.modern.ie/svgforeignobjectelement）是不支持的。

在写它的时候似乎是个人的浏览器仍然有渲染SVGs嵌入式HTML到画布上的一些问题。请参阅[维基的已知问题列表]（https://github.com/cburgmer/rasterizeHTML.js/wiki/Browser-issues），并在那里做补充你的发现。

发展
-----------

对于掉毛，测试和微小Node.js的安装和运行

    $./go

对于Chrome和Safari浏览器下的集成测试打开`测试/ manualIntegrationTestForWebkit.html`（铬下，你要么需要启动浏览器传递选项`--allow文件存取的-files`或通过加载页面本地网络服务器）。

[！[构建Status](https://travis-ci.org/cburgmer/rasterizeHTML.js.svg?branch=master)](https://travis-ci.org/cburgmer/rasterizeHTML.js)

它在哪里使用？
-----------------

* [CSS评论家]（https://github.com/cburgmer/csscritic），用于层叠样式表回归测试一个轻量级的框架
*...

笔者
------
克里斯托夫Burgmer。 MIT许可。伸手[在Twitter]（https://twitter.com/cburgmer）。
