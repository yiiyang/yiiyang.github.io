---
layout:     post
title:      "memcached实现内存消息队列实例"
date:       2014-06-10
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
-   memcached实现内存消息队列实例
---

<div id="article_content" class="article_content">

    <h1 style=""><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; font-size:14px; line-height:20px">现在memcache在服务器缓存应用比较广泛，下面我来介绍memcache实现消息队列等待的一个例子，有需要了解的朋友可参考。</span>
        <p style="">memche消息队列的原理就是在key上做文章，用以做一个连续的数字加上前缀记录序列化以后消息或者日志。然后通过定时程序将内容落地到文件或者<a target="_blank" href="http://www.php100.com/database/database.html" target="_blank" style="">数据库</a>。</p>
        <p style=""><br style="">
            php实现消息队列的用处比如在做发送<a target="_blank" href="http://www.php100.com/list-54/" target="_blank" style="">邮件</a>时发送大量邮件很费时间的问题，那么可以采取队列。<br style="">
            方便实现队列的轻量级队列服务器是：<br style="">
            star<a target="_blank" href="http://www.php100.com/list-198/" target="_blank" style="">ling</a>支持memcache协议的轻量级持久化服务器<br style="">
            htt<a target="_blank" href="http://www.php100.com/fw/photo.html" target="_blank" style="">ps</a>://github.com/starling/starling<br style="">
            Beanstalkd轻量、高效，支持持久化，每秒可处理3000左右的队列<br style="">
            http://kr.github.com/beanstalkd/<br style="">
            php中也可以使用memcache/memcached来实现消息队列。</p>
<pre name="code" class="php">&lt;?php
/**
* Memcache 消息队列类
*/

class QMC {
const PREFIX = 'ASDFASDFFWQKE';

/**
* 初始化mc
* @staticvar string $mc
* @return Memcache
*/
static private function mc_init() {
static $mc = null;
if (is_null($mc)) {
$mc = new Memcache;
$mc-&gt;connect('127.0.0.1', 11211);
}
return $mc;
}
/**
* mc 计数器,增加计数并返回新的计数
* @param string $key   计数器
* @param int $offset   计数增量,可为负数.0为不改变计数
* @param int $time     时间
* @return int/false    失败是返回false,成功时返回更新计数器后的计数
*/
static public function set_counter( $key, $offset, $time=0 ){
$mc = self::mc_init();
$val = $mc-&gt;get($key);
if( !is_numeric($val) || $val &lt; 0 ){
$ret = $mc-&gt;set( $key, 0, $time );
if( !$ret ) return false;
$val = 0;
}
$offset = intval( $offset );
if( $offset &gt; 0 ){
return $mc-&gt;increment( $key, $offset );
}elseif( $offset &lt; 0 ){
return $mc-&gt;decrement( $key, -$offset );
}
return $val;
}

/**
* 写入队列
* @param string $key
* @param mixed $value
* @return bool
*/
static public function input( $key, $value ){
$mc = self::mc_init();
$w_key = self::PREFIX.$key.'W';
$v_key = self::PREFIX.$key.self::set_counter($w_key, 1);
return $mc-&gt;set( $v_key, $value );
}
/**
* 读取队列里的数据
* @param string $key
* @param int $max  最多读取条数
* @return array
*/
static public function output( $key, $max=100 ){
$out = array();
$mc = self::mc_init();
$r_key = self::PREFIX.$key.'R';
$w_key = self::PREFIX.$key.'W';
$r_p   = self::set_counter( $r_key, 0 );//读指针
$w_p   = self::set_counter( $w_key, 0 );//写指针
if( $r_p == 0 ) $r_p = 1;
while( $w_p &gt;= $r_p ){
if( --$max &lt; 0 ) break;
$v_key = self::PREFIX.$key.$r_p;
$r_p = self::set_counter( $r_key, 1 );
$out[] = $mc-&gt;get( $v_key );
$mc-&gt;delete($v_key);
}
return $out;
}
}
/**
使用方法:
QMC::input($key, $value );//写入队列
$list = QMC::output($key);//读取队列
*/
?&gt;</pre><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; font-size:14px; line-height:20px">基于PHP共享内存实现的消息队列:</span></h1>
    <h1 style=""><pre name="code" class="php">&lt;?php
/**
* 使用共享内存的PHP循环内存队列实现
* 支持多进程, 支持各种数据类型的存储
* 注: 完成入队或出队操作,尽快使用unset(), 以释放临界区
*
* @author wangbinandi@gmail.com
* @created 2009-12-23
*/
class ShmQueue
{
private $maxQSize = 0; // 队列最大长度

private $front = 0; // 队头指针
private $rear = 0;  // 队尾指针

private $blockSize = 256;  // 块的大小(byte)
private $memSize = 25600;  // 最大共享内存(byte)
private $shmId = 0;

private $filePtr = './shmq.ptr';

private $semId = 0;
public function __construct()
{
$shmkey = ftok(__FILE__, 't');

$this-&gt;shmId = shmop_open($shmkey, &quot;c&quot;, 0644, $this-&gt;memSize );
$this-&gt;maxQSize = $this-&gt;memSize / $this-&gt;blockSize;

// 申?一个信号量
$this-&gt;semId = sem_get($shmkey, 1);
sem_acquire($this-&gt;semId); // 申请进入临界区

$this-&gt;init();
}

private function init()
{
if ( file_exists($this-&gt;filePtr) ){
$contents = file_get_contents($this-&gt;filePtr);
$data = explode( '|', $contents );
if ( isset($data[0]) &amp;&amp; isset($data[1])){
$this-&gt;front = (int)$data[0];
$this-&gt;rear  = (int)$data[1];
}
}
}

public function getLength()
{
return (($this-&gt;rear - $this-&gt;front + $this-&gt;memSize) % ($this-&gt;memSize) )/$this-&gt;blockSize;
}

public function enQueue( $value )
{
if ( $this-&gt;ptrInc($this-&gt;rear) == $this-&gt;front ){ // 队满
return false;
}

$data = $this-&gt;encode($value);
shmop_write($this-&gt;shmId, $data, $this-&gt;rear );
$this-&gt;rear = $this-&gt;ptrInc($this-&gt;rear);
return true;
}

public function deQueue()
{
if ( $this-&gt;front == $this-&gt;rear ){ // 队空
return false;
}
$value = shmop_read($this-&gt;shmId, $this-&gt;front, $this-&gt;blockSize-1);
$this-&gt;front = $this-&gt;ptrInc($this-&gt;front);
return $this-&gt;decode($value);
}

private function ptrInc( $ptr )
{
return ($ptr + $this-&gt;blockSize) % ($this-&gt;memSize);
}

private function encode( $value )
{
$data = serialize($value) . &quot;__eof&quot;;
echo '';

echo strlen($data);
echo '';

echo $this-&gt;blockSize -1;
echo '';

if ( strlen($data) &gt; $this-&gt;blockSize -1 ){
throw new Exception(strlen($data).&quot; is overload block size!&quot;);
}
return $data;
}

private function decode( $value )
{
$data = explode(&quot;__eof&quot;, $value);
return unserialize($data[0]);
}

public function __destruct()
{
$data = $this-&gt;front . '|' . $this-&gt;rear;
file_put_contents($this-&gt;filePtr, $data);

sem_release($this-&gt;semId); // 出临界区, 释放信号量
}
}

/*
// 进队操作
$shmq = new ShmQueue();
$data = 'test data';
$shmq-&gt;enQueue($data);
unset($shmq);
// 出队操作
$shmq = new ShmQueue();
$data = $shmq-&gt;deQueue();
unset($shmq);
*/
?&gt;</pre><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; font-size:14px; line-height:20px">对于一个很大的消息队列，频繁进行进行大</span><a target="_blank" href="http://www.php100.com/list-55/" target="_blank" style="">数据库</a><span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; font-size:14px; line-height:20px">的序列化
 和 反序列化，有太耗费。下面是我用PHP 实现的一个消息队列，只需要在尾部插入一个数据，就操作尾部，不用操作整个消息队列进行读取，与操作。但是，这个消息队列不是线程安全的，我只是尽量的避免了冲突的可能性。如果消息不是非常的密集，比如几秒钟才一个，还是可以考虑这样使用的。&nbsp;</span><br style="">
        <span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; font-size:14px; line-height:20px">如果你要实现线程安全的，一个建议是通过文件进行锁定，然后进行操作。下面是代码：&nbsp;</span><br style="">
        <span style="color:rgb(51,51,51); font-family:&quot;Microsoft Yahei&quot;,&quot;Helvetica Neue&quot;,Helvetica,Arial,sans-serif; font-size:14px; line-height:20px">代码如下:</span></h1>
    <h1 style=""><pre name="code" class="php">class Memcache_Queue
{
private $memcache;
private $name;
private $prefix;
function __construct($maxSize, $name, $memcache, $prefix = &quot;__memcache_queue__&quot;)
{
if ($memcache == null) {
throw new Exception(&quot;memcache object is null, new the object first.&quot;);
}
$this-&gt;memcache = $memcache;
$this-&gt;name = $name;
$this-&gt;prefix = $prefix;
$this-&gt;maxSize = $maxSize;
$this-&gt;front = 0;
$this-&gt;real = 0;
$this-&gt;size = 0;
}
function __get($name)
{
return $this-&gt;get($name);
}
function __set($name, $value)
{
$this-&gt;add($name, $value);
return $this;
}
function isEmpty()
{
return $this-&gt;size == 0;
}
function isFull()
{
return $this-&gt;size == $this-&gt;maxSize;
}
function enQueue($data)
{
if ($this-&gt;isFull()) {
throw new Exception(&quot;Queue is Full&quot;);
}
$this-&gt;increment(&quot;size&quot;);
$this-&gt;set($this-&gt;real, $data);
$this-&gt;set(&quot;real&quot;, ($this-&gt;real + 1) % $this-&gt;maxSize);
return $this;
}
function deQueue()
{
if ($this-&gt;isEmpty()) {
throw new Exception(&quot;Queue is Empty&quot;);
}
$this-&gt;decrement(&quot;size&quot;);
$this-&gt;delete($this-&gt;front);
$this-&gt;set(&quot;front&quot;, ($this-&gt;front + 1) % $this-&gt;maxSize);
return $this;
}
function getTop()
{
return $this-&gt;get($this-&gt;front);
}
function getAll()
{
return $this-&gt;getPage();
}
function getPage($offset = 0, $limit = 0)
{
if ($this-&gt;isEmpty() || $this-&gt;size &lt; $offset) {
return null;
}
$keys[] = $this-&gt;getKeyByPos(($this-&gt;front + $offset) % $this-&gt;maxSize);
$num = 1;
for ($pos = ($this-&gt;front + $offset + 1) % $this-&gt;maxSize; $pos != $this-&gt;real; $pos = ($pos + 1) % $this-&gt;maxSize)
{
$keys[] = $this-&gt;getKeyByPos($pos);
$num++;
if ($limit &gt; 0 &amp;&amp; $limit == $num) {
break;
}
}
return array_values($this-&gt;memcache-&gt;get($keys));
}
function makeEmpty()
{
$keys = $this-&gt;getAllKeys();
foreach ($keys as $value) {
$this-&gt;delete($value);
}
$this-&gt;delete(&quot;real&quot;);
$this-&gt;delete(&quot;front&quot;);
$this-&gt;delete(&quot;size&quot;);
$this-&gt;delete(&quot;maxSize&quot;);
}
private function getAllKeys()
{
if ($this-&gt;isEmpty())
{
return array();
}
$keys[] = $this-&gt;getKeyByPos($this-&gt;front);
for ($pos = ($this-&gt;front + 1) % $this-&gt;maxSize; $pos != $this-&gt;real; $pos = ($pos + 1) % $this-&gt;maxSize)
{
$keys[] = $this-&gt;getKeyByPos($pos);
}
return $keys;
}
private function add($pos, $data)
{
$this-&gt;memcache-&gt;add($this-&gt;getKeyByPos($pos), $data);
return $this;
}
private function increment($pos)
{
return $this-&gt;memcache-&gt;increment($this-&gt;getKeyByPos($pos));
}
private function decrement($pos)
{
$this-&gt;memcache-&gt;decrement($this-&gt;getKeyByPos($pos));
}
private function set($pos, $data)
{
$this-&gt;memcache-&gt;set($this-&gt;getKeyByPos($pos), $data);
return $this;
}
private function get($pos)
{
return $this-&gt;memcache-&gt;get($this-&gt;getKeyByPos($pos));
}
private function delete($pos)
{
return $this-&gt;memcache-&gt;delete($this-&gt;getKeyByPos($pos));
}
private function getKeyByPos($pos)
{
return $this-&gt;prefix . $this-&gt;name . $pos;
}
} </pre><br>
        <br>
    </h1>

</div>
