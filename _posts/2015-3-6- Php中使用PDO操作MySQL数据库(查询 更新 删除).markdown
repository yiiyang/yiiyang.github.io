---
layout:     post
title:      " Php中使用PDO操作MySQL数据库(查询 更新 删除)"
date:       2015-03-06
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
-    Php中使用PDO操作MySQL数据库(查询 更新 删除)
---

<div id="article_content" class="article_content">

    <p><span style="color:rgb(68,68,68); font-family:Simsun; font-size:15px; line-height:26px">PDO是mysql数据库操作的一个公用类了，我们不需要进行自定类就可以直接使用pdo来操作数据库了，但是在php默认配置中pdo是未开启所以我们必须先在php.ini中开启它才可以使用，下文我会讲到。</span></p>
    <p><span style="color:rgb(68,68,68); font-family:Simsun; font-size:15px; line-height:26px"></span></p>
    <p style="list-style:none; margin-top:0px; margin-bottom:0px; padding-top:8px; padding-bottom:8px; font-size:14px; line-height:26px; word-wrap:break-word; color:rgb(68,68,68); font-family:Simsun">
        PDO扩展为PHP访问<a target="_blank" href="http://www.111cn.net/list-55/" target="_blank" style="font-size:15px; color:rgb(45,100,179)">数据库</a>定义了一个轻量级的、一致性的接口，它提供了一个数据访问抽象层，<br>
        这样，无论使用什么<a target="_blank" href="http://www.111cn.net/database/database.html" target="_blank" style="font-size:15px; color:rgb(45,100,179)">数据库</a>，都可以通过一致的函数执行查询和获取数据。</p>
    <p style="list-style:none; margin-top:0px; margin-bottom:0px; padding-top:8px; padding-bottom:8px; font-size:14px; line-height:26px; word-wrap:break-word; color:rgb(68,68,68); font-family:Simsun">
        PDO支持的PHP版本为PHP5.1以及更高的版本,而且在PHP5.2下PDO默认为开启状态,<br>
        下面是在php.ini中PDO的配置:</p>
    <p style="list-style:none; margin-top:0px; margin-bottom:0px; padding-top:8px; padding-bottom:8px; font-size:14px; line-height:26px; word-wrap:break-word; color:rgb(68,68,68); font-family:Simsun">
        <span style="color:#ff0000">extension=php_pdo.dll</span></p>
    <p style="list-style:none; margin-top:0px; margin-bottom:0px; padding-top:8px; padding-bottom:8px; font-size:14px; line-height:26px; word-wrap:break-word; color:rgb(68,68,68); font-family:Simsun">
        为了启用对某个数据库的支持,需要在<a target="_blank" href="http://www.111cn.net/tags.php/php%C5%E4%D6%C3/" target="_blank" style="font-size:15px; color:rgb(45,100,179)">php配置</a>文件中将相应的扩展打开,例如要支持MySQL,需要开启下面的扩展</p>
    <p style="list-style:none; margin-top:0px; margin-bottom:0px; padding-top:8px; padding-bottom:8px; font-size:14px; line-height:26px; word-wrap:break-word; color:rgb(68,68,68); font-family:Simsun">
        <span style="color:#ff0000">extension=php_pdo_mysql.dll</span></p>
    <p style="list-style:none; margin-top:0px; margin-bottom:0px; padding-top:8px; padding-bottom:8px; font-size:14px; line-height:26px; word-wrap:break-word; color:rgb(68,68,68); font-family:Simsun">
        这里是使用PDO对mysql进行基本的增删改查操作</p>
<pre name="code" class="php">header(&quot;content-type:text/html;charset=utf-8&quot;);
$dsn=&quot;mysql:dbname=test;host=localhost&quot;;
$db_user=&#39;root&#39;;
$db_pass=&#39;admin&#39;;
try{
 $pdo=new PDO($dsn,$db_user,$db_pass);
}catch(PDOException $e){
 echo &#39;数据库连接失败&#39;.$e-&gt;getMessage();
}
//新增
$sql=&quot;insert into buyer (username,password,email) values (&#39;ff&#39;,&#39;123456&#39;,&#39;admin@admin.com&#39;)&quot;;
$res=$pdo-&gt;exec($sql);
echo &#39;影响行数：&#39;.$res;

//修改
$sql=&quot;update buyer set username=&#39;ff123&#39; where id&gt;3&quot;;
$res=$pdo-&gt;exec($sql);
echo &#39;影响行数：&#39;.$res;
//查询
$sql=&quot;select * from buyer&quot;;
$res=$pdo-&gt;query($sql);
foreach($res as $row){
 echo $row[&#39;username&#39;].&#39;&lt;br/&gt;&#39;;
}
//删除
$sql=&quot;delete from buyer where id&gt;5&quot;;
$res=$pdo-&gt;exec($sql);
echo &#39;影响行数：&#39;.$res;</pre><br>
    <br>

</div>
