---
layout:     post
title:      "PHP MySQLi 增删改查"
date:       2015-03-26
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
-   PHP MySQLi 增删改查
---

<div id="article_content" class="article_content">

    <p>1：登陆页面</p>
    <p><pre name="code" class="php">//前端显示部分

&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;
&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
&lt;head&gt;
&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=utf-8&quot; /&gt;
&lt;title&gt;无标题文档&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
&lt;h2&gt;管理员登陆&lt;/h2&gt;
&lt;form action=&quot;dlyz.php&quot; method=&quot;post&quot;&gt;
&lt;div&gt;用户名：&lt;input type=&quot;text&quot; name=&quot;user&quot; value=&quot;请输入您的工号&quot; /&gt;&lt;/div&gt;
&lt;br /&gt;
&lt;div&gt;密&#160;&#160;码：&lt;input type=&quot;password&quot; name=&quot;psd&quot; /&gt;&lt;/div&gt;
&lt;br /&gt;
&lt;input type=&quot;submit&quot; value=&quot;登录&quot; /&gt;
&lt;input type=&quot;submit&quot; value=&quot;注册新用户&quot; formaction=&quot;zhuc.php&quot;/&gt;
&lt;/form&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>//php对提交登陆信息的处理</p>
    <p><pre name="code" class="php">&lt;?php

$user = $_POST[&quot;user&quot;];
$psd = $_POST[&quot;psd&quot;];


//造对象
$db = new MySQLi(&quot;localhost&quot;,&quot;root&quot;,&quot;&quot;,&quot;newssystem&quot;);

//判断是否出错
!mysqli_connect_error() or die(&quot;连接失败！！&quot;);

//写sql语句

$sql = &quot;select psd from yonghu where user=&#39;{$user}&#39;&quot;;


//执行SQL语句

$result = $db-&gt; query($sql);
$v = $result-&gt;fetch_row();
if($psd==$v[0])
{
header(&quot;location:fabuxinwen.php&quot;);
}
else
{
echo&quot;您输入的用户名或密码不正确，请重新输入！！&quot;;
}</pre></p>
    <p>2：注册页面</p>
    <p><pre name="code" class="php">&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;
&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
&lt;head&gt;
&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=utf-8&quot; /&gt;
&lt;title&gt;无标题文档&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
&lt;h2&gt;欢迎注册&lt;/h2&gt;
&lt;body&gt;

&lt;form action=&quot;zhucyz.php&quot;method=&quot;post&quot;&gt;
&lt;div&gt;用户名：&lt;input type=&quot;text&quot; name=&quot;user&quot; value=&quot;请输入您的工号&quot;/&gt;&lt;/div&gt;&lt;br /&gt;

&lt;div&gt;密&#160;&#160;码：&lt;input type=&quot;password&quot; name=&quot;psd&quot; /&gt;&lt;/div&gt;&lt;br /&gt;

&lt;input type=&quot;submit&quot; value=&quot;提交&quot; /&gt;
&lt;/form&gt;

&lt;/body&gt;
&lt;/html&gt;



&lt;?php
$user = $_POST[&quot;user&quot;];
$psd = $_POST[&quot;psd&quot;];


//造对象
$db = new MySQLi(&quot;localhost&quot;,&quot;root&quot;,&quot;&quot;,&quot;newssystem&quot;);

//判断是否出错
!mysqli_connect_error() or die(&quot;连接失败！！&quot;);

//写sql语句

$sql = &quot;insert into yonghu values(&#39;{$user}&#39;,&#39;{$psd}&#39;)&quot;;

//执行SQL语句

$result = $db-&gt; query($sql);

if($result)
{
header(&quot;location:dl.php&quot;);
}
else
{
echo&quot;很抱歉，注册失败！！&quot;;
}</pre><br>
    3：登陆进去以后，是发布页面，可以发布和查看</p>
    <p><pre name="code" class="php">&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;
&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
&lt;head&gt;
&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=utf-8&quot; /&gt;
&lt;title&gt;无标题文档&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
&lt;div style=&quot;width:100%; text-align:center&quot; &gt;
&lt;h2&gt;发布新闻&lt;/h2&gt;
&lt;form method=&quot;post&quot;&gt;
&lt;input type=&quot;hidden&quot; name=&quot;newsid&quot;/&gt;
&lt;table style=&quot;margin:0 auto; text-align:left&quot; &gt;
&lt;tr&gt;
&lt;td &gt;标题：&lt;/td&gt;&lt;td&gt;&lt;input type=&quot;text&quot; style=&quot;width:400px&quot; name=&quot;title&quot; /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td &gt;作者：
&lt;/td&gt;&lt;td&gt;&lt;input type=&quot;text&quot; style=&quot;width:400px&quot; name=&quot;Author&quot; /&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td &gt;来源：&lt;/td&gt;&lt;td&gt;&lt;input type=&quot;text&quot; style=&quot;width:400px&quot; name=&quot;source&quot;/&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td &gt;内容：&lt;/td&gt;
&lt;td&gt;&lt;textarea cols=&quot;auto&quot; rows=&quot;auto&quot; style=&quot;width:400px; height:400px&quot; name=&quot;content&quot;&gt;&lt;/textarea&gt;&lt;/td&gt;
&lt;/tr&gt;

&lt;/table&gt;&lt;br /&gt;
&lt;?php
$time = date(&#39;y-m-d h:i:s&#39;);

echo &quot;&lt;input type=\&quot;hidden\&quot; name=\&quot;time\&quot; value=\&quot;{$time}\&quot;/&gt;&quot;;
?&gt;

&lt;input type=&quot;submit&quot; value=&quot;提交&quot; formaction=&quot;tijiao.php&quot;/&gt;

&lt;input type=&quot;submit&quot; value=&quot;查看&quot; formaction=&quot;chakan.php&quot;/&gt;
&lt;/form&gt;
&lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;

 </pre><br>
<pre name="code" class="php">&lt;?php
$title = $_POST[&quot;title&quot;];
$Author = $_POST[&quot;Author&quot;];
$source = $_POST[&quot;source&quot;];
$content = $_POST[&quot;content&quot;];

//造对象
$db = new MySQLi(&quot;localhost&quot;,&quot;root&quot;,&quot;&quot;,&quot;newssystem&quot;);

//判断是否出错
!mysqli_connect_error() or die(&quot;添加失败！！&quot;);

//写sql语句

$sql = &quot;insert into news(title,Author,source,content) values(&#39;{$title}&#39;,&#39;{$Author}&#39;,&#39;{$source}&#39;,&#39;{$content}&#39;)&quot;;


//执行SQL语句

$result = $db-&gt; query($sql);

if($result)
{
header(&quot;location:fabuxinwen.php&quot;);
}
else
{
echo&quot;很抱歉，添加失败！！&quot;;
}</pre>4：查看页面</p>
    <p><pre name="code" class="php">&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;
&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
&lt;head&gt;
&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=utf-8&quot; /&gt;
&lt;title&gt;无标题文档&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
&lt;table width=&quot;70%&quot; border=&quot;1px&quot; cellpadding=&quot;0&quot; cellspacing=&quot;0&quot; style=&quot;text-align:center&quot;&gt;
&lt;tr&gt;
&lt;td&gt;编号&lt;/td&gt;
&lt;td&gt;标题&lt;/td&gt;
&lt;td&gt;作者&lt;/td&gt;
&lt;td&gt;来源&lt;/td&gt;
&lt;td&gt;日期&lt;/td&gt;
&lt;td&gt;删除&lt;/td&gt;
&lt;td&gt;修改&lt;/td&gt;

&lt;/tr&gt;

&lt;?php
$db=new mysqli(&quot;localhost&quot;,&quot;root&quot;,&quot;&quot;,&quot;newssystem&quot;);
!mysqli_connect_error() or die(&quot;连接错误&quot;);
$sql=&quot;select * from news&quot;;
$result=$db-&gt;query($sql);
while($attr=$result-&gt;fetch_row())
{
echo &quot;
&lt;tr&gt;
&lt;td&gt;{$attr[0]}&lt;/td&gt;
&lt;td&gt;{$attr[1]}&lt;/td&gt;
&lt;td&gt;{$attr[2]}&lt;/td&gt;
&lt;td&gt;{$attr[3]}&lt;/td&gt;
&lt;td&gt;{$attr[5]}&lt;/td&gt;
&lt;td&gt;&lt;a onclick=\&quot; return confirm(&#39;确定删除&#39;)\&quot; href=&#39;scchuli.php?newsid={$attr[0]}&#39;&gt;删除&lt;/a&gt;&lt;/td&gt;
&lt;td&gt;&lt;a href=&#39;xiugai.php?newsid={$attr[0]}&#39;&gt;修改&lt;/a&gt;&lt;/td&gt;
&lt;/tr&gt;
&quot;;
}

?&gt;
&lt;/table&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>5：在查看页面可以进行修改和删除<pre name="code" class="php">&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;
&lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;
&lt;head&gt;
&lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=utf-8&quot; /&gt;
&lt;title&gt;无标题文档&lt;/title&gt;
&lt;/head&gt;

&lt;body&gt;
&lt;?php
$id = $_GET[&quot;newsid&quot;];

$db=new mysqli(&quot;localhost&quot;,&quot;root&quot;,&quot;&quot;,&quot;newssystem&quot;);
!mysqli_connect_error() or die(&quot;连接错误&quot;);
$sql=&quot;select * from news where newsid=&#39;{$id}&#39;&quot;;
$result=$db-&gt;query($sql);
$attr=$result-&gt;fetch_row();
?&gt;
&lt;div style=&quot;width:100%; text-align:center&quot; &gt;
&lt;h2&gt;修改新闻&lt;/h2&gt;
&lt;form action=&quot;xgchuli.php&quot; method=&quot;post&quot;&gt;
&lt;input type=&quot;hidden&quot; name=&quot;newsid&quot; &lt;?php echo &quot;value=&#39;{$attr[0]}&#39;&quot;;?&gt;/&gt;
&lt;table style=&quot;margin:0 auto; text-align:left&quot; &gt;
&lt;tr&gt;
&lt;td &gt;标题：&lt;/td&gt;&lt;td&gt;&lt;input type=&quot;text&quot; style=&quot;width:400px&quot; name=&quot;title&quot; &lt;?php echo &quot;value=&#39;{$attr[1]}&#39;&quot;;?&gt;/&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td &gt;作者：
&lt;/td&gt;&lt;td&gt;&lt;input type=&quot;text&quot; style=&quot;width:400px&quot; name=&quot;Author&quot; &lt;?php echo &quot;value=&#39;{$attr[2]}&#39;&quot;;?&gt;/&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td &gt;来源：&lt;/td&gt;&lt;td&gt;&lt;input type=&quot;text&quot; style=&quot;width:400px&quot; name=&quot;source&quot; &lt;?php echo &quot;value=&#39;{$attr[3]}&#39;&quot;;?&gt;/&gt;
&lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
&lt;td &gt;内容：&lt;/td&gt;
&lt;td&gt;&lt;textarea cols=&quot;auto&quot; rows=&quot;auto&quot; style=&quot;width:400px; height:400px&quot; name=&quot;content&quot;&gt;&lt;?php echo &quot;{$attr[4]}&quot;;?&gt;
&lt;/textarea&gt;&lt;/td&gt;
&lt;/tr&gt;

&lt;/table&gt;&lt;br /&gt;
&lt;?php
$time = date(&#39;y-m-d h:i:s&#39;);

echo &quot;&lt;input type=\&quot;hidden\&quot; name=\&quot;time\&quot; value=\&quot;{$time}\&quot;/&gt;&quot;;
?&gt;

&lt;div&gt;&lt;a href=&quot;chakan.php&quot;&gt;&lt;input type=&quot;button&quot; title=&quot;查看&quot; value=&quot;查看&quot; /&gt;&lt;/a&gt;&lt;input type=&quot;submit&quot; title=&quot;修改&quot; value=&quot;修改&quot;/&gt;
&lt;/div&gt;

&lt;/form&gt;

&lt;/body&gt;
&lt;/html&gt;



&lt;?php

$id=$_POST[&quot;newsid&quot;];
$title=$_POST[&quot;title&quot;];
$Author=$_POST[&quot;Author&quot;];
$source=$_POST[&quot;source&quot;];
$content=$_POST[&quot;content&quot;];
$time=$_POST[&quot;time&quot;];

$db = new MySQLi(&quot;localhost&quot;,&quot;root&quot;,&quot;&quot;,&quot;newssystem&quot;);

!mysqli_connect_error() or die(&quot;连接失败&quot;);

$sql=&quot;update news set title=&#39;{$title}&#39;,Author=&#39;{$Author}&#39;,source=&#39;{$source}&#39;,content=&#39;{$content}&#39;,time=&#39;{$time}&#39; where newsid=&#39;{$id}&#39; &quot;;

$result=$db-&gt;query($sql);
if ($result)
{
header(&quot;location:chakan.php&quot;);
}
else
{
echo &quot;修改失败&quot;;
}</pre><br>
    //删除数据</p>
    <p><pre name="code" class="php">&lt;?php
$id=$_GET[&quot;newsid&quot;];

$db=new mysqli(&quot;localhost&quot;,&quot;root&quot;,&quot;&quot;,&quot;newssystem&quot;);

!mysqli_connect_error() or die(&quot;连接失败&quot;);

$sql=&quot;delete from news where newsid=&#39;{$id}&#39;&quot;;

$result=$db-&gt;query($sql);

if ($result)
{
header(&quot;location:chakan.php&quot;);
}
else
{
echo &quot;删除失败&quot;;
}</pre><br>
    6：修改页面</p>
    <p><pre name="code" class="php">&lt;?php
$title = $_POST[&quot;title&quot;];
$Author = $_POST[&quot;Author&quot;];
$source = $_POST[&quot;source&quot;];
$content = $_POST[&quot;content&quot;];

//造对象
$db = new MySQLi(&quot;localhost&quot;,&quot;root&quot;,&quot;&quot;,&quot;newssystem&quot;);

//判断是否出错
!mysqli_connect_error() or die(&quot;添加失败！！&quot;);

//写sql语句

$sql = &quot;insert into news(title,Author,source,content) values(&#39;{$title}&#39;,&#39;{$Author}&#39;,&#39;{$source}&#39;,&#39;{$content}&#39;)&quot;;


//执行SQL语句

$result = $db-&gt; query($sql);

if($result)
{
header(&quot;location:fabuxinwen.php&quot;);
}
else
{
echo&quot;很抱歉，添加失败！！&quot;;
}</pre></p>
    <br>

</div>



