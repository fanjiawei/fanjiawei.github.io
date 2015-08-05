---
layout: post
title:  "单页应用的nginx配置!"
date:   2015-08-01 18:07:37
categories: nginx
---

weather.zoumeizou.com返回前端页面，    
weather.zoumeizou.com/api是接口地址。

nginx配置如下

{% highlight javascript %}
server {
    listen       80;
    server_name  weather.zoumeizou.com;
    
    location /api {
        proxy_pass http://localhost:8080/weather/api;
        proxy_set_header Host $http_host;
    }
    
    location / {
        rewrite ^ /index.html break;
        root   /usr/share/nginx/weather;
        index  index.html index.htm;
    }
}
{% endhighlight %}

rewrite使用   
作用：重写url实现页面跳转，可以做到前端url地址不变跳转和返回302，301状态码跳转。    
用法：rewrite (访问路径规则) (修改后的url) flag;    

flag的值   
1. last 相当于Apache里的[L]标记，表示完成rewrite   
2. break 终止匹配, 不再匹配后面的规则   
3. redirect 返回302临时重定向 地址栏会显示跳转后的地址   
4. permanent 返回301永久重定向 地址栏会显示跳转后的地址    