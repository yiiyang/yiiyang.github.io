---
layout:     post
title:      "php get_magic_quotes_gpc()函数用法介绍"
date:       2014-03-20
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
- php get_magic_quotes_gpc()函数用法介绍
---
<div class="main">
    <div class="container">
        <div class="row">

            <div class="col-md-9">

                <div class="panel panel-default">
                    <div class="panel-body">
                        <h1 style="margin-top:0;">php get_magic_quotes_gpc()函数用法介绍</h1>

                        <p>  | 时间：2014-03-20 19:02:38 </p>
                        <blockquote>
                            <p>[导读] magic_quotes_gpc函数在php中的作用是判断解析用户提示的数据，如包括有:post、get、cookie过来的数据增加转义字符&ldquo;  &rdquo;，以确保这些数据不会引起程序，特别是数据库语句因为特殊字符引起的污染而出现致命的错误   </p>
                        </blockquote>
                        <div class="php-content">
                            magic_quotes_gpc函数在php中的作用是判断解析用户提示的数据，如包括有:post、get、cookie过来的数据增加转义字符&ldquo;\&rdquo;，以确保这些数据不会引起程序，特别是数据库语句因为特殊字符引起的污染而出现致命的错误
                            <div class="floatAd" id="c_ads5">&nbsp;
                                <p>在magic_quotes_gpc=On的情况下，如果输入的数据有</p>
                                <p>单引号（&rsquo;）、双引号（&rdquo;）、反斜线（）与 NUL（NULL 字符）等字符都会被加上反斜线。这些转义是必须的，如果这个选项为off，那么我们就必须调用addslashes这个函数来为字符串增加转义。</p>
                                <p>正是因为这个选项必须为On，但是又让用户进行配置的矛盾，在PHP6中删除了这个选项，一切的编程都需要在magic_quotes_gpc=Off下进行了。在这样的环境下如果不对用户的数据进行转义，后果不仅仅是程序错误而已了。同样的会引起数据库被注入攻击的危险。所以从现在开始大家都不要再依赖这个设置为On了，以免有一天你的服务器需要更新到PHP6而导致你的程序不能正常工作。</p>
                                <table align="center" border="0" cellpadding="1" cellspacing="1" style="background:#FB7" width="620">
                                    <tbody>
                                    <tr>
                                        <td bgcolor="#FFE7CE" height="27" width="464">&nbsp;代码如下</td>
                                        <td align="center" bgcolor="#FFE7CE" onclick="doCopy('copy1444')" style="cursor:pointer;" width="109">复制代码</td>
                                    </tr>
                                    <tr>
                                        <td bgcolor="#FFFFFF" class="copyclass" colspan="2" height="auto" id="copy1444" style="padding:10px;" valign="top">
                                            <p>当magic_quotes_gpc=On的时候，函数get_magic_quotes_gpc()就会返回1</p>
                                            <p>当magic_quotes_gpc=Off的时候，函数get_magic_quotes_gpc()就会返回0</p>
                                        </td>
                                    </tr>
                                    </tbody>
                                </table>
                                <p>因此可以看出这个get_magic_quotes_gpc()函数的作用就是得到环境变量magic_quotes_gpc的值。既然在PHP6中删除了magic_quotes_gpc这个选项，那么在PHP6中这个函数我想也已经不复存在了。</p>
                                <p><br />
                                    php 判断是否开启get_magic_quotes_gpc功能了，以方便我们是否决定使用addslashes这个函数了。</p>
                                <table align="center" border="0" cellpadding="1" cellspacing="1" style="background:#FB7" width="620">
                                    <tbody>
                                    <tr>
                                        <td bgcolor="#FFE7CE" height="27" width="464">&nbsp;代码如下</td>
                                        <td align="center" bgcolor="#FFE7CE" onclick="doCopy('copy5907')" style="cursor:pointer;" width="109">复制代码</td>
                                    </tr>
                                    <tr>
                                        <td bgcolor="#FFFFFF" class="copyclass" colspan="2" height="auto" id="copy5907" style="padding:10px;" valign="top">
                                            <p>function SQLString($c, $t){<br />
                                                &nbsp;$c=(!get_magic_quotes_gpc())?addslashes($c):$c;<br />
                                                &nbsp;switch($t){<br />
                                                &nbsp; case &#39;text&#39;:<br />
                                                &nbsp;&nbsp; $c=($c!=&#39;&#39;)?&quot;&#39;&quot;.$c.&quot;&#39;&quot;:&#39;NULL&#39;;<br />
                                                &nbsp;&nbsp; break;<br />
                                                &nbsp; case &#39;search&#39;:<br />
                                                &nbsp;&nbsp; $c=&quot;&#39;%%&quot;.$c.&quot;%%&#39;&quot;;<br />
                                                &nbsp;&nbsp; break;<br />
                                                &nbsp; case &#39;int&#39;:<br />
                                                &nbsp;&nbsp; $c=($c!=&#39;&#39;)?intval($c):&#39;0&#39;;<br />
                                                &nbsp;&nbsp; break;<br />
                                                &nbsp;}<br />
                                                &nbsp;return $c;<br />
                                                }</p>
                                        </td>
                                    </tr>
                                    </tbody>
                                </table>
                                <p>预防数据库攻击的正确做法</p>
                                <table align="center" border="0" cellpadding="1" cellspacing="1" style="background:#FB7" width="620">
                                    <tbody>
                                    <tr>
                                        <td bgcolor="#FFE7CE" height="27" width="464">&nbsp;代码如下</td>
                                        <td align="center" bgcolor="#FFE7CE" onclick="doCopy('copy7915')" style="cursor:pointer;" width="109">复制代码</td>
                                    </tr>
                                    <tr>
                                        <td bgcolor="#FFFFFF" class="copyclass" colspan="2" height="auto" id="copy7915" style="padding:10px;" valign="top">
                                            <p><!--?php</p--></p>
                                            <p>function check_input($value)</p>
                                            <p>{</p>
                                            <p>// 去除斜杠</p>
                                            <p>if (get_magic_quotes_gpc())</p>
                                            <p>{</p>
                                            <p>$value = stripslashes($value);</p>
                                            <p>}</p>
                                            <p>// 如果不是数字则加引号</p>
                                            <p>if (!is_numeric($value))</p>
                                            <p>{</p>
                                            <p>$value = &ldquo;&lsquo;&rdquo; . mysql_real_escape_string($value) . &ldquo;&lsquo;&rdquo;;</p>
                                            <p>}</p>
                                            <p>return $value;</p>
                                            <p>}</p>
                                            <p>$con = mysql_connect(&ldquo;localhost&rdquo;, &ldquo;hello&rdquo;, &ldquo;321&Prime;);</p>
                                            <p>if (!$con)</p>
                                            <p>{</p>
                                            <p>die(&lsquo;Could not connect: &lsquo; . mysql_error());</p>
                                            <p>}</p>
                                            <p>// 进行安全的 SQL</p>
                                            <p>$user = check_input($_POST[&#39;user&#39;]);</p>
                                            <p>$pwd = check_input($_POST[&#39;pwd&#39;]);</p>
                                            <p>$sql = &ldquo;SELECT * FROM users WHERE</p>
                                            <p>user=$user AND password=$pwd&rdquo;;</p>
                                            <p>mysql_query($sql);</p>
                                            <p>mysql_close($con);</p>
                                            <p>?&gt;</p>
                                        </td>
                                    </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                    </div>
                    </div>
                    </div>
                    </div>
                    </div>
                    </div>
