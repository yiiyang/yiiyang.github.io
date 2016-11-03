---
layout:     post
title:      "PHP获取Cookie模拟登录CURL"
date:       2015-01-15
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
- PHP获取Cookie模拟登录CURL
---
<div class="main">
    <div class="container">
        <div class="row">

            <div class="col-md-9">

                <div class="panel panel-default">
                    <div class="panel-body">
                        <h1 style="margin-top:0;">PHP获取Cookie模拟登录CURL</h1>
                        <blockquote>
                            <p>[导读] 要提取google搜索的部分数据，发现google对于软件抓取它的数据屏蔽的厉害，以前伪造下 USER-AGENT就可以抓数据，但是现在却不行了。利用抓包数据发现，Google判断了cookies，当你没有cookies的时候，直接返回30 </p>
                        </blockquote>
                        <div class="php-content">
                            <p>要提取google搜索的部分数据，发现google对于软件抓取它的数据屏蔽的厉害，以前伪造下 USER-AGENT&nbsp;就可以抓数据，但是现在却不行了。利用抓包数据发现，Google&nbsp;判断了&nbsp;cookies，当你没有cookies的时候，直接返回&nbsp;302&nbsp;跳转，而且是连续几十个302跳转，根本抓不了数据。<br />
                                <br />
                                <img src="http://www.php100.com/uploadfile/2013/0912/20130912080213684.jpg" />因此，在发送搜索命令时，需要先提取&nbsp;cookies&nbsp;并保存，然后利用保存下来的这个cookies再次发送搜索命令即可正常抓数据了。这其实和论坛的模拟登录一个道理，先POST登录，获取cookies并保存，然后利用这个cookies访问就可以了。</p>
                            <p>&nbsp;</p>
                            <br />
                            一、定义Cookie存储路径<br />
                            <br />
                            必须使用绝对路径<br />
                            <br />
<pre class="brush:php;">
$cookie_jar = dirname(__FILE__).&quot;/pic.cookie&quot;;</pre>
                            <br />
                            <br />
                            <br />
                            二、获取Cookie<br />
                            <br />
                            将cookie存入文件<br />
                            <br />
<pre class="brush:php;">
$url = &quot;http://1.2.3.4/&quot;;
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_COOKIEJAR, $cookie_jar);
$content = curl_exec($ch);
curl_close($ch);</pre>
                            <br />
                            <br />
                            <br />
                            <br />
                            三、模拟浏览器获取验证码<br />
                            <br />
                            该服务器验证码有漏洞，可以自己指定<br />
                            <br />
                            取出cookie，一起提交给服务器，让服务器以为是浏览器打开登陆页面<br />
                            <br />
<pre class="brush:php;">
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, &#39;http://1.2.3.4/getCheckpic.action?rand=6836.185874812305&#39;);
curl_setopt($ch, CURLOPT_COOKIEFILE, $cookie_jar);
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$ret = curl_exec($ch);
curl_close($ch);</pre>
                            <br />
                            <br />
                            <br />
                            <br />
                            四、POST提交<br />
                            <br />
<pre class="brush:php;">
$post = &quot;name=2&amp;userType=1&amp;passwd=asdf&amp;loginType=1&amp;rand=6836&amp;imageField.x=25&amp;imageField.y=7&quot;;
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, &quot;http://1.2.3.4/loginstudent.action&quot;);
curl_setopt($ch, CURLOPT_HEADER, false);
curl_setopt($ch, CURLOPT_RETURNTRANSFER,1);
curl_setopt($ch, CURLOPT_POSTFIELDS, $post);
curl_setopt($ch, CURLOPT_COOKIEFILE, $cookie_jar);
$result=curl_exec($ch);
curl_close($ch);</pre>
                            <br />
                            <br />
                            <br />
                            <br />
                            五、到指定页面获取数据<br />
                            <br />
<pre class="brush:php;">
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, &quot;http://1.2.3.4/accountcardUser.action&quot;);
curl_setopt($ch, CURLOPT_HEADER, false);
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_setopt($ch, CURLOPT_RETURNTRANSFER,0);
curl_setopt($ch, CURLOPT_COOKIEFILE, $cookie_jar);
$html=curl_exec($ch);
// var_dump($html);
curl_close($ch);</pre>
                        </div>
                        <div class="text-right">
                        </div>
                    </div>
                </div>
            </div>
        </div>
        </div>