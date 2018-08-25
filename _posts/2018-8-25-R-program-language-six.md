---
layout: post
title:  "R语言"
date:   2018-08-25 12:59:49 +0800
categories: R-program-language
tags: R-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-25/96766257.jpg
author: DND
---

还剩5天(｡･ω･｡)

* 
{:toc}

## R语言的三大绘图系统
### r语言的绘图系统之一--基本绘图系统
```r
#基本绘图
library(graphics)
#plot(绘图)/hist(柱状图)/boxplot(箱图)/points(点)/lines(线)/text(添加文字)/title(命名)/axis(添加坐标轴)
?airquality
```
```
hist(airquality$Wind,xlab = "Wind") #可以呈现出风速的柱状图
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/15750170.jpg)
```
boxplot(airquality$Wind,xlab="Wind",ylab="Speed(mph)") #可以呈现出风速的箱图
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/61869175.jpg)
```
boxplot(Wind~Month,airquality,xlab="Month",ylab="Speed(mph)") #风速随月份变化的箱图
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/59093083.jpg)
```
plot(airquality$Wind,airquality$Temp) #风速与温度的关系

with(airquality,plot(Wind,Temp)) #上面一种写法的简化
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/56209339.jpg)
```
par(mfrow=c(1,2)) #将一个平面左右分为两半

title(main = "Wind and Temp in NYC") #添加标题

with(airquality,plot(Wind,Temp,main = "Wind and Temp in NYC")) #添加标题的第二种写法

with(airquality,plot(Wind,Temp,main = "Wind and Temp in NYC",type="n"))
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/12796701.jpg)
```
with(subset(airquality,Month==9),points(Wind,Temp,col="red"))

with(subset(airquality,Month==5),points(Wind,Temp,col="green"))

with(subset(airquality,Month %in% c(6,7,8)),points(Wind,Temp,col="blue"))

fit<-lm(Temp ~ Wind,airquality) #"~"左边是因变量，右边是自变量,lm回归线

abline(fit) #做出线性回归直线

abline(fit,lwd=2)

#加上各种颜色的含义
legend("topright",pch=1,col = c("red","green","blue"),legend = c("Sep","May","Other"))
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/96766257.jpg)
```


#基本绘图系统之全局参数
par("bg")
par("col")
par("mar") #与html5中的margin很像
par("mfrow") #只有一行一列
par("mfcol") #按列来写
?par #查看图形都有哪些属性
```
```
par(mfrow=c(1,2))
hist(airquality$Temp)
hist(airquality$Wind)
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/74946710.jpg)
```
par(mfrow=c(1,3))
boxplot(airquality$Temp)
boxplot(airquality$Wind)
boxplot(airquality$Solar.R)
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/65115336.jpg)
```
par(mfcol=c(2,1))
hist(airquality$Temp)
hist(airquality$Wind)
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-25/45095174.jpg)
## 学习感悟
绘图系统，r语言区别于其它语言的重要指标之一。


4k壁纸
[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-25/68324654.jpg)

