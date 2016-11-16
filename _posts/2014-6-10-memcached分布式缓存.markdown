---
layout:     post
title:      "memcached内存缓存"
date:       2014-06-10
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
-   memcached内存缓存
---
<p><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; font-size:14px; line-height:20px">PHP内存缓存Memcached类有需要的朋友可参考一下。</span></p>
<p><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; font-size:14px; line-height:20px"></span><pre code_snippet_id="1987511" snippet_file_name="blog_20161116_1_7721954"  name="code" class="php">&lt;?PHP

class MemcacheModel {
private $mc = null;
/**
* 构造方法,用于添加服务器并创建memcahced对象
*/
function __construct(){
$params = func_get_args();
$mc = new Memcache;
//如果有多个memcache服务器
if( count($params) &gt; 1){
foreach ($params as $v){
call_user_func_array(array($mc, 'addServer'), $v);
}
//如果只有一个memcache服务器
} else {
call_user_func_array(array($mc, 'addServer'), $params[0]);
}
$this-&gt;mc=$mc;
}
/**
* 获取memcached对象
* @return object memcached对象
*/
function getMem(){
return $this-&gt;mc;
}
/**
* 检查mem是否连接成功
* @return bool 连接成功返回true,否则返回false
*/
function mem_connect_error(){
$stats=$this-&gt;mc-&gt;getStats();
if(empty($stats)){
return false;
}else{
return true;
}
}

private function addKey($tabName, $key){
$keys=$this-&gt;mc-&gt;get($tabName);
if(empty($keys)){
$keys=array();
}
//如果key不存在,就添加一个
if(!in_array($key, $keys)) {
$keys[]=$key;  //将新的key添加到本表的keys中
$this-&gt;mc-&gt;set($tabName, $keys, MEMCACHE_COMPRESSED, 0);
return true;   //不存在返回true
}else{
return false;  //存在返回false
}
}
/**
* 向memcache中添加数据
* @param string $tabName 需要缓存数据表的表名
* @param string $sql 使用sql作为memcache的key
* @param mixed $data 需要缓存的数据
*/
function addCache($tabName, $sql, $data){
$key=md5($sql);
//如果不存在
if($this-&gt;addKey($tabName, $key)){
$this-&gt;mc-&gt;set($key, $data, MEMCACHE_COMPRESSED, 0);
}
}
/**
* 获取memcahce中保存的数据
* @param string $sql 使用SQL的key
* @return mixed 返回缓存中的数据
*/
function getCache($sql){
$key=md5($sql);
return $this-&gt;mc-&gt;get($key);
}


/**
* 删除和同一个表相关的所有缓存
* @param string $tabName 数据表的表名
*/
function delCache($tabName){
$keys=$this-&gt;mc-&gt;get($tabName);
//删除同一个表的所有缓存
if(!empty($keys)){
foreach($keys as $key){
$this-&gt;mc-&gt;delete($key, 0); //0 表示立刻删除
}
}
//删除表的所有sql的key
$this-&gt;mc-&gt;delete($tabName, 0);
}
/**
* 删除单独一个语句的缓存
* @param string $sql 执行的SQL语句
*/
function delone($sql){
$key=md5($sql);
$this-&gt;mc-&gt;delete($key, 0); //0 表示立刻删除
}
}</pre><br>
<br>
</p>




