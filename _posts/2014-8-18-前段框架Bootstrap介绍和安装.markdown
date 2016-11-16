---
layout:     post
title:      "前段框架Bootstrap介绍和安装"
date:       2014-08-18
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
-   前段框架Bootstrap介绍和安装
---
<div id="article_content" class="article_content">

    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-size:14px; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
    </p>
    <h2 class="tutheader" style="border-width:1px 0px 0px; border-top-style:solid; border-top-color:rgb(212,212,212); margin:0px; padding:5px 0px 0px; font-size:1.8em; line-height:1.8em; clear:both; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        什么是 Bootstrap？</h2>
    <p></p>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        Bootstrap 是一个用于快速开发 Web 应用程序和网站的前端框架。Bootstrap 是基于 HTML、CSS、JAVASCRIPT 的。</p>
    <h2 class="tutheader" style="border-width:1px 0px 0px; border-top-style:solid; border-top-color:rgb(212,212,212); margin:0px; padding:5px 0px 0px; font-size:1.8em; line-height:1.8em; clear:both; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        为什么使用 Bootstrap？</h2>
    <ul class="list" style="border:0px; margin:1em 0px; padding:0px; line-height:16.8px; list-style-type:none; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        <li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>移动设备优先</strong>：自 Bootstrap 3 起，框架包含了贯穿于整个库的移动设备优先的样式。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>浏览器支持</strong>：所有的主流浏览器都支持 Bootstrap。
            <p style="border:0px; margin-top:0px; margin-bottom:0px; padding:0px 10px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif">
                <img src="http://www.dnzs.com.cn/w3cschool/images/compatible_ie.gif" width="31" height="30" alt="Internet Explorer" title="Internet Explorer" style="border:0px; margin:0px; padding:0px; max-width:100%; height:auto">&nbsp;<img src="http://www.dnzs.com.cn/w3cschool/images/compatible_firefox.gif" width="31" height="30" alt="Firefox" title="Firefox" style="border:0px; margin:0px; padding:0px; max-width:100%; height:auto">&nbsp;<img src="http://www.dnzs.com.cn/w3cschool/images/compatible_opera.gif" width="28" height="30" alt="Opera" title="Opera" style="border:0px; margin:0px; padding:0px; max-width:100%; height:auto">&nbsp;<img src="http://www.dnzs.com.cn/w3cschool/images/compatible_chrome.gif" width="31" height="30" alt="Google Chrome" title="Google Chrome" style="border:0px; margin:0px; padding:0px; max-width:100%; height:auto">&nbsp;<img src="http://www.dnzs.com.cn/w3cschool/images/compatible_safari.gif" width="28" height="30" alt="Safari" title="Safari" style="border:0px; margin:0px; padding:0px; max-width:100%; height:auto"></p>
        </li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>容易上手</strong>：只要您具备 HTML 和 CSS 的基础知识，您就可以开始学习 Bootstrap。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>响应式设计</strong>：Bootstrap 的响应式 CSS 能够自适应于台式机、平板电脑和手机。更多有关响应式设计的内容详见&nbsp;<a target="_blank" href="http://www.dnzs.com.cn/w3cschool/bootstrap/bootstrap-responsive-design.html" style="border:0px; margin:0px; padding:0px; color:rgb(0,114,188); text-decoration:none">Bootstrap
                响应式设</a></li></ul>
    <ul class="list" style="border:0px; margin:1em 0px; padding:0px; line-height:16.8px; list-style-type:none; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        <li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            它为开发人员创建接口提供了一个简洁统一的解决方案。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            它包含了功能强大的内置组件，易于定制。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            它还提供了基于 Web 的定制。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            它是开源的。</li></ul>
    <h2 class="tutheader" style="border-width:1px 0px 0px; border-top-style:solid; border-top-color:rgb(212,212,212); margin:0px; padding:5px 0px 0px; font-size:1.8em; line-height:1.8em; clear:both; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        Bootstrap 包的内容</h2>
    <ul class="list" style="border:0px; margin:1em 0px; padding:0px; line-height:16.8px; list-style-type:none; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        <li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>基本结构</strong>：Bootstrap 提供了一个带有网&#26684;系统、链接样式、背景的基本结构。这将在&nbsp;<strong>Bootstrap 基本结构</strong>&nbsp;部分详细讲解。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>CSS</strong>：Bootstrap 自带以下特性：全局的 CSS 设置、定义基本的 HTML 元素样式、可扩展的 class，以及一个先进的网&#26684;系统。这将在&nbsp;<strong>Bootstrap CSS</strong>&nbsp;部分详细讲解。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>组件</strong>：Bootstrap 包含了十几个可重用的组件，用于创建图像、下拉菜单、导航、警告框、弹出框等等。这将在&nbsp;<strong>布局组件</strong>&nbsp;部分详细讲解。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>JavaScript 插件</strong>：Bootstrap 包含了十几个自定义的 jQuery 插件。您可以直接包含所有的插件，也可以逐个包含这些插件。这将在<strong>Bootstrap 插件</strong>&nbsp;部分详细讲解。
            <p style="border:0px; margin-top:0px; margin-bottom:0px; padding:0px 10px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif">
            </p>
        </li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <strong>定制</strong>：您可以定制 Bootstrap 的组件、LESS 变量和 jQuery 插件来得到您自己的版本。</li></ul>
    <h1 style="border:0px; margin:0px 0px 10px; padding:0px; font-size:2.1em; font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        Bootstrap&nbsp;<span class="color_h1" style="border:0px; margin:0px; padding:0px; color:rgb(100,133,76)">环境安装</span></h1>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        Bootstrap 安装是非常容易的。本章将讲解如何下载并安装 Bootstrap，讨论 Bootstrap 文件结构，并通过一个实例演示它的用法。</p>
    <h2 class="tutheader" style="border-width:1px 0px 0px; border-top-style:solid; border-top-color:rgb(212,212,212); margin:0px; padding:5px 0px 0px; font-size:1.8em; line-height:1.8em; clear:both; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        下载 Bootstrap</h2>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        您可以从&nbsp;<a target="_blank" target="_blank" rel="nofollow" href="http://getbootstrap.com/" style="border:0px; margin:0px; padding:0px; color:rgb(100,133,76)">http://getbootstrap.com/</a>&nbsp;上下载 Bootstrap 的最新版本。当您点击这个链接时，您将看到如下所示的网页：</p>
    <img src="http://www.runoob.com/wp-content/uploads/2014/06/bootstrapdowloadscreen.jpg" alt="Bootstrap 下载" style="border:0px; margin:0px; padding:0px; max-width:100%; height:auto; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif"><span style="color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif"></span>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        您会看到两个按钮：</p>
    <ul class="list" style="border:0px; margin:1em 0px; padding:0px; line-height:16.8px; list-style-type:none; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        <li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <em>Download Bootstrap</em>：下载 Bootstrap。点击该按钮，您可以下载 Bootstrap CSS、JavaScript 和字体的预编译的压缩版本。不包含文档和最初的源代码文件。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <em>Download Source</em>：下载源代码。点击该按钮，您可以直接从 from 上得到最新的 Bootstrap LESS 和 JavaScript 源代码。</li></ul>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        如果您使用的是未编译的源代码，您需要编译 LESS 文件来生成可重用的 CSS 文件。对于编译 LESS 文件，Bootstrap 官方只支持<a target="_blank" target="_blank" rel="nofollow" href="http://twitter.github.io/recess/" style="border:0px; margin:0px; padding:0px; color:rgb(100,133,76)">Recess</a>，这是 Twitter 的基于&nbsp;<a target="_blank" target="_blank" rel="nofollow" href="http://lesscss.org/" style="border:0px; margin:0px; padding:0px; color:rgb(100,133,76)">less.js</a>&nbsp;的
        CSS 提示。</p>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        为了更好的了解和更方便的使用，我们将在本教程中使用 Bootstrap 的预编译版本。</p>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        由于文件是被编译过和压缩过的，在独立的功能开发中，您不必每次都包含这些独立的文件。</p>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        本教程编写时，使用的是最新版（Bootstrap 3）。</p>
    <h2 class="tutheader" style="border-width:1px 0px 0px; border-top-style:solid; border-top-color:rgb(212,212,212); margin:0px; padding:5px 0px 0px; font-size:1.8em; line-height:1.8em; clear:both; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        文件结构</h2>
    <h3 style="border:0px; margin:8px 0px; padding:0px; font-size:1.4em; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        预编译的 Bootstrap</h3>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        当您下载了 Bootstrap 的已编译的版本，解压缩 ZIP 文件，您将看到下面的文件/目录结构：</p>
    <img src="http://www.runoob.com/wp-content/uploads/2014/06/compiledfilestructure.jpg" alt="已编译的 Bootstrap 文件结构" style="border:0px; margin:0px; padding:0px; max-width:100%; height:auto; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif"><span style="color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif"></span>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        如上图所示，可以看到已编译的 CSS 和 JS（bootstrap.*），以及已编译压缩的 CSS 和 JS（bootstrap.min.*）。同时也包含了 Glyphicons 的字体，这是一个可选的 Bootstrap 主题。</p>
    <h3 style="border:0px; margin:8px 0px; padding:0px; font-size:1.4em; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        Bootstrap 源代码</h3>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        如果您下载了 Bootstrap 源代码，那么文件结构将如下所示：</p>
    <img src="http://www.runoob.com/wp-content/uploads/2014/06/sourcecodefilestructure.jpg" alt="Bootstrap 源代码结构" style="border:0px; margin:0px; padding:0px; max-width:100%; height:auto; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif"><span style="color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif"></span>
    <ul class="list" style="border:0px; margin:1em 0px; padding:0px; line-height:16.8px; list-style-type:none; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        <li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <em>less/</em>、<em>js/</em>&nbsp;和&nbsp;<em>fonts/</em>&nbsp;下的文件分别是 Bootstrap CSS、JS 和图标字体的源代码。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <em>dist/</em>&nbsp;文件夹包含了上面预编译下载部分中所列的文件和文件夹。</li><li style="border:0px; margin:0px 0px 1em 1em; padding:0px 0px 0px 1.5em; line-height:1.5em; font-size:1em">
            <em>docs-assets/</em>、<em>examples/</em>&nbsp;和所有的&nbsp;<em>*.html</em>&nbsp;文件是 Bootstrap 文档。</li></ul>
    <h2 class="tutheader" style="border-width:1px 0px 0px; border-top-style:solid; border-top-color:rgb(212,212,212); margin:0px; padding:5px 0px 0px; font-size:1.8em; line-height:1.8em; clear:both; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        HTML 模板</h2>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        一个使用了 Bootstrap 的基本的 HTML 模板如下所示：</p>
<pre name="code" class="html">&lt;!DOCTYPE html&gt;
&lt;html&gt;
   &lt;head&gt;
      &lt;title&gt;Bootstrap 模板&lt;/title&gt;
      &lt;meta name=&quot;viewport&quot; content=&quot;width=device-width, initial-scale=1.0&quot;&gt;
      &lt;!-- 引入 Bootstrap --&gt;
      &lt;link href=&quot;http://cdn.static.runoob.com/libs/bootstrap/3.3.7/css/bootstrap.min.css&quot; rel=&quot;stylesheet&quot;&gt;

      &lt;!-- HTML5 Shim 和 Respond.js 用于让 IE8 支持 HTML5元素和媒体查询 --&gt;
      &lt;!-- 注意： 如果通过 file://  引入 Respond.js 文件，则该文件无法起效果 --&gt;
      &lt;!--[if lt IE 9]&gt;
         &lt;script src=&quot;https://oss.maxcdn.com/libs/html5shiv/3.7.0/html5shiv.js&quot;&gt;&lt;/script&gt;
         &lt;script src=&quot;https://oss.maxcdn.com/libs/respond.js/1.3.0/respond.min.js&quot;&gt;&lt;/script&gt;
      &lt;![endif]--&gt;
   &lt;/head&gt;
   &lt;body&gt;
      &lt;h1&gt;Hello, world!&lt;/h1&gt;

      &lt;!-- jQuery (Bootstrap 的 JavaScript 插件需要引入 jQuery) --&gt;
      &lt;script src=&quot;https://code.jquery.com/jquery.js&quot;&gt;&lt;/script&gt;
      &lt;!-- 包括所有已编译的插件 --&gt;
      &lt;script src=&quot;js/bootstrap.min.js&quot;&gt;&lt;/script&gt;
   &lt;/body&gt;
&lt;/html&gt;</pre><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; line-height:24px">在这里，您可以看到包含了&nbsp;</span><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; line-height:24px">jquery.js</span><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; line-height:24px">、</span><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; line-height:24px">bootstrap.min.js</span><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; line-height:24px">&nbsp;和&nbsp;</span><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; line-height:24px">bootstrap.min.css</span><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; line-height:24px">&nbsp;文件，用于让一个常规的
 HTML 文件变为使用了 Bootstrap 的模板。</span><br>
    <h2 style="border:0px; margin:2px 0px; padding:0px; font-size:1.8em; line-height:1.8em; color:rgb(51,51,51); font-family:&quot;Open Sans&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,STHeiti,&quot;Microsoft Yahei&quot;,sans-serif">
        Bootstrap CDN推荐</h2>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        本站实例采用的是百度的静态资源库上的Bootstrap资源。</p>
    <p style="border:0px; margin-top:0px; margin-bottom:0px; padding-top:0px; padding-bottom:0px; line-height:2em; font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; color:rgb(51,51,51)">
        百度的静态资源库的 CDN 服务，访问速度更快、加速效果更明显、没有速度和带宽限制、永久免费,引入代码如下：</p>
<pre name="code" class="html">&lt;!-- 新 Bootstrap 核心 CSS 文件 --&gt;
&lt;link href=&quot;http://cdn.static.runoob.com/libs/bootstrap/3.3.7/css/bootstrap.min.css&quot; rel=&quot;stylesheet&quot;&gt;

&lt;!-- 可选的Bootstrap主题文件（一般不使用） --&gt;
&lt;script src=&quot;http://cdn.static.runoob.com/libs/bootstrap/3.3.7/css/bootstrap-theme.min.css&quot;&gt;&lt;/script&gt;

&lt;!-- jQuery文件。务必在bootstrap.min.js 之前引入 --&gt;
&lt;script src=&quot;http://cdn.static.runoob.com/libs/jquery/2.1.1/jquery.min.js&quot;&gt;&lt;/script&gt;

&lt;!-- 最新的 Bootstrap 核心 JavaScript 文件 --&gt;
&lt;script src=&quot;http://cdn.static.runoob.com/libs/bootstrap/3.3.7/js/bootstrap.min.js&quot;&gt;&lt;/script&gt;</pre><br>

</div>

