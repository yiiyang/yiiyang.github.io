---
layout:     post
title:      " linux操作mysql命令"
date:       2014-12-16
author:     "yangyang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
-    linux操作mysql命令
---

<div id="article_content" class="article_content">

    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
<span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">1.终端启动&nbsp;<a target="_blank" href="http://lib.csdn.net/base/mysql" class="replace_word" title="MySQL知识库" target="_blank" style="color:rgb(223,52,52); text-decoration:none; font-weight:bold">MySQL</a>：/etc/init.d/mysql
 start</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">&nbsp;2.登录 MySQL：mysql -uroot -p (用 root 账户登录),然后输入密码&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
<span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">3.查看所有的<a target="_blank" href="http://lib.csdn.net/base/mysql" class="replace_word" title="MySQL知识库" target="_blank" style="color:rgb(223,52,52); text-decoration:none; font-weight:bold">数据库</a>名字：show
 databases;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">4.选择一个数据库操作： use database_name;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">5.查看当前数据库下所有的表名：show tables;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">6.创建一个数据库：create database database_name;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">7.删除一个数据库：drop database database_name;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">8.创建一个表: create table mytest( uid bigint(20) not null primary key, uname varchar(20) not null);&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">9.删除一个表: drop table mytest;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">10.SQL 插入语句：insert into table_name(col1,col2) values(value1,value2);&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">11.SQL 更新语句：update table_name set col1='value1',col2='value2' where where_definition;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">12.SQL 查询语句：select * from table_name where.......</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">13.SQL 删除语句：delete from table_name where...&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">14.增加表结构的字段：alert table table_name add column field1 date ,add column field2 time...&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">15.删除表结构的字段：alert table table_name drop field1;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">16.查看表的结构：show columns from table_name;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">17.limit 的使用：select * from table_name limit 3; &nbsp; //每页只显示 3 行&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px"><span style="white-space:pre"></span>select * from table_name limit 3,4; &nbsp; //从查询结果的第三个开始，显示四项结果。 此处可很好的用来作分页处理。&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">18.对查询结果进行排序: select * from table_name order by field1,orderby field2;多重排序&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">19.退出 MySQL:exit;&nbsp;</span></span></p>
    <p style="color:rgb(51,51,51); font-family:Arial; font-size:14px; line-height:26px">
        <span style="font-family:arial,helvetica,clean; line-height:24px"><span style="font-size:18px">20.删除表中所有数据： truncate table 数据表名称 （不可恢复）</span></span></p>

</div>


