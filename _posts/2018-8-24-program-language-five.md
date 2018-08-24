---
layout: post
title:  "R语言"
date:   2018-08-24 12:59:49 +0800
categories: R-program-language
tags: R-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-24/31315217.jpg
author: DND
---

6天就要返校了(｡･ω･｡)

* 
{:toc}

## R语言的数据库的连接
### r语言连接数据库的基本函数
```r
odbcDriverConnect() #打开一个ODBC数据库的链接
sqlQuery() #提交一个SQL语句到ODBC数据库，然后返回结果
sqlTables() #列出ODBC链接里的所有表
sqlFetch() #从ODBC数据库里读取一个表到数据帧
sqlColumns() #在ODBC中查询列结构
close(connection) #关闭链接
```


### r语言连接数据库及基本操作

```r
#连接mysql数据库
install.packages("RMySQL") #如果没有这个包就先下载
library("RMySQL") #加载这个包
con<-dbConnect(MySQL(),host="127.0.0.1",dbname="mysql",user="root",password="newpass")
con2<-dbConnect(MySQL(),host="127.0.0.1",dbname="ourwork",user="root",password="newpass")
dbListTables(con2)
query<-dbSendQuery(con2, "SELECT * from vip") #执行sql语句，和jdbc类似
data<-fetch(query,n=-1) #n=2是取出前两条数据，n=-1是取出所有数据
close(con2)

con3<-dbConnect(MySQL(),host="127.0.0.1",dbname="ourwork",user="root",password="newpass")
query1<-dbSendQuery(con3,"select count(*) from vip")
data1<-fetch(query1,n=-1)
```




## 学习感悟
连接数据库，固定的套路，(￣▽￣)~*

4k壁纸(￣▽￣)~*
[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-24/77405646.jpg)

