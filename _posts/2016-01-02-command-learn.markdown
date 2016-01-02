---
layout: post
title:  "linux命令学习"
date:   2016-01-02 17:13:53
categories: linux
---

记录学到的linux命令
====

base64
----------------------

###加密：

base64，输入要加密内容，ctrl+D
: mac下需要两次ctrl+D    

echo "str" | base64
: str+换行，加密

echo -n "str" | base64
: str，加密，没有换行
         



###解密：

echo "c3RyCg==" | base64 -D
: 
 

        
____________________
 
md5
----------------

###加密

####字符串：md5 -s "str"

####文件：md5 -f [files ...]    

    例子：    
	md5 ./*    
	加密当前目录下得所有文件

