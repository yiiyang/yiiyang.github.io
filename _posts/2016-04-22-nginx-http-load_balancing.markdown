---
layout: post
title: 使用nginx实现负载均衡
category: 服务器
date : 2016-08-22
---

  前面文章我已经记录了<a href="http://www.zhuangyan.cn/2-centos6-nginx1.8/" target="_blank">如何部署Nginx</a>和<a href="http://www.zhuangyan.cn/3-centos6-nginx-uwsgi-django1.6/" target="_blank">如果部署django</a>，如果不做负载均衡，按步骤把nginx和django部署到一台服务上就可以实现WEB服务。但是为了保证服务的性能和稳定性，我们就需要实现负载均衡。
  负载均衡的基本原理就是前端服务器用来接收请求再分发给后端的服务器进行处理。所以我们前端要只部署nginx服务，后端可以只部署uwsgi和django,也可以部署nginx+uwsgi+django。本文主要记录前端服务器的nginx.conf配置。

## 在http节点里添加

{% highlight nginx %}
    upstream backend  {
            server  192.168.1.108:80;
            server  192.168.1.109:80;
        }

{% endhighlight %}

## 修改server节点

{% highlight nginx %}
    location / {
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_buffering off;
        proxy_pass http://backend;
    } 
{% endhighlight %}

## 多应用按域名分发
   就是写多个upstream配置到不同的server中，如：
   {% highlight nginx %}
    upstream django  {
            server  192.168.1.108:80;
            server  192.168.1.109:80;
            server  192.168.1.110:80;
            server  192.168.1.111:80;
    }
    upstream php  {
            server  192.168.1.112:80;
            server  192.168.1.113:80;
    }
{% endhighlight %}

{% highlight nginx %}
    server {
        listen       80;
        server_name  www.zhuangyan.cn;
        #charset koi8-r;
        #access_log  logs/host.access.log  main;
        location / {
            proxy_set_header Host $host;
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_buffering off;
          proxy_pass http://php;
        }
       
    }

    server {
        listen       80;
        server_name  app.zhuangyan.cn;
        location / {
          proxy_set_header Host $host;
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_buffering off;
          proxy_pass http://django;
      }
      location ~/static/ {
            root  /home/django/;
            index  index.html index.htm;
      }      
    }
{% endhighlight %}

## 其他配置
   
   按权重分配什么的配置，请参考<a href="http://nginx.org/en/docs/http/load_balancing.html" target="_blank">官方文档</a>。    

