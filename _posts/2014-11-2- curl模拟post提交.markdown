---
layout:     post
title:      " curl模拟post提交"
date:       2014-11-2
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
-    curl模拟post提交
---
<div id="article_content" class="article_content">

<pre name="code" class="php">    header(&#39;content-type:text/html;charset=utf-8&#39;);
    function curlPost($url,$data,$method){
        $ch = curl_init();   //1.初始化
        curl_setopt($ch, CURLOPT_URL, $url); //2.请求地址
        curl_setopt($ch, CURLOPT_CUSTOMREQUEST, $method);//3.请求方式
        //4.参数如下
        curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);//https
        curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);
        curl_setopt($ch, CURLOPT_USERAGENT, &#39;Mozilla/5.0 (compatible; MSIE 5.01; Windows NT 5.0)&#39;);//模拟浏览器
        curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
        curl_setopt($ch, CURLOPT_AUTOREFERER, 1);
            curl_setopt($ch, CURLOPT_HTTPHEADER,array(&#39;Accept-Encoding: gzip, deflate&#39;));//gzip解压内容
            curl_setopt($ch, CURLOPT_ENCODING, &#39;gzip,deflate&#39;);

        if($method==&quot;POST&quot;){//5.post方式的时候添加数据
            curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
        }
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
        $tmpInfo = curl_exec($ch);//6.执行

        if (curl_errno($ch)) {//7.如果出错
            return curl_error($ch);
        }
        curl_close($ch);//8.关闭
        return $tmpInfo;
    }
    $data=array(&#39;name&#39; =&gt; &#39;1234&#39;);
    $url=&quot;http://www.sohu.com/&quot;;

    $method=&quot;GET&quot;;
    $file=curlPost($url,$data,$method);
    $file=mb_convert_encoding($file,&#39;UTF-8&#39;,&#39;GBK&#39;);
    echo $file;  </pre><br>
    <p>当cookie认证登陆的时候</p>
    <p><pre name="code" class="php">    &lt;?php
        $cookie_file = tempnam(&#39;./temp&#39;,&#39;cookie&#39;);
        function weixinPost($url,$data,$method,$setcooke=false,$cookie_file=false){
            $ch = curl_init();   //1.初始化
            curl_setopt($ch, CURLOPT_URL, $url); //2.请求地址
            curl_setopt($ch, CURLOPT_CUSTOMREQUEST, $method);//3.请求方式
            //4.参数如下
            curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
            curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);
            curl_setopt($ch, CURLOPT_USERAGENT, &#39;Mozilla/5.0 (compatible; MSIE 5.01; Windows NT 5.0)&#39;);
            curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
            curl_setopt($ch, CURLOPT_AUTOREFERER, 1);

            if($method==&quot;POST&quot;){//5.post方式的时候添加数据
                curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
            }
            if($setcooke==true){
                curl_setopt($ch, CURLOPT_COOKIEJAR, $cookie_file);
            }else{
                curl_setopt($ch, CURLOPT_COOKIEFILE, $cookie_file);
            }
            curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
            $tmpInfo = curl_exec($ch);//6.执行

            if (curl_errno($ch)) {//7.如果出错
                return curl_error($ch);
            }
            curl_close($ch);//8.关闭
            return $tmpInfo;
        }
        $data=array(&#39;username&#39; =&gt; &#39;***&#39;,&#39;password&#39;=&gt;&#39;***&#39;);
        $url=&quot;http://www.xinxinj.com/login.php&quot;;
        $method=&quot;POST&quot;;
        $file=weixinPost($url,$data,$method,true,$cookie_file);
        echo $file;

        $url=&quot;http://www.xinxinj.com/admin.php&quot;;
        $method=&quot;GET&quot;;
        $file=weixinPost($url,$data,$method,false,$cookie_file);
        echo $file;

    ?&gt;  </pre><br>
    <br>
    </p>

</div>
