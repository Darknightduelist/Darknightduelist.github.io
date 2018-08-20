---
layout: post
title:  "R语言"
date:   2018-08-20 12:59:49 +0800
categories: R-program-language
tags: R-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-20/81492620.jpg
author: DND
---

还有10天就要返校了(｡･ω･｡)

* 
{:toc}

## R语言的重要函数的使用
### r语言函数-lapply
```r
#R不仅有for/while语句，还有更强大的实现循环的“一句话”函数

#可以循环处理列表中的每一个元素
#lapply（列表，函数/函数名，其他参数）
#总是返回一个列表

str(lapply) #将函数整洁的显示出来,显示出其参数

x<-list(a=c(1:10),b=c(11,21,31,41,51))

y<-lapply(x, mean) #mean是求平均值函数

x1<-1:4
p<-lapply(x1, runif) #runif的作用是生成均匀分布的随机数，默认从0~1抽取
p1<-lapply(x1, runif,min=0,max=100) #生0~100之间的随机数

x2<-list(a=matrix(1:6,nrow = 2,ncol = 3),b=matrix(4:7,nrow = 2,ncol = 2))
x3<-list(a<-matrix(1:6,nrow = 2,ncol = 3),b<-matrix(4:7,nrow = 2,ncol = 2))
x4<-list(a=matrix(1:6,2,3),b=matrix(4:7,2,2))
lapply(x4, function(m) m[1,]) #m是自定义函数，注意中间是逗号还是空格

#sapply对lapply进行化简
#结果列表元素长度均为一，返回向量
#结果列表长度相同且大于一，返回矩阵
f<-list(a=1:10,b=c(11,21,31,41,51))
lapply(x, mean)
sapply(x, mean)
```
### r语言函数-apply
```r
#apply沿着数组的某一维度处理数据
#apply(数组，维度，函数/函数名)

x<-matrix(1:16,4,4)
apply(x,2,mean) #两个维度，1代表行，2代表列
apply(x,2,sum)

rowSums(x)
rowMeans(x)
colSums(x)
colMeans(x)

x1<-matrix(rnorm(100),10,10) #rnorm随机从正态分布的总体中，抽取100个
apply(x1,1,quantile,probs=c(0.25,0.75)) 
#quantile求数据的百分位点(｀・ω・´)，话说什么是百分位点
#百分位点的意思：按大小顺序排列的数列中某一百分位分数所对应百分位所在的位置
#probs是对quantile进行限定，25%和75%所对应的数据

x2<-array(rnorm(2*3*4),c(2:4))
x3<-array(rnorm(2*3*4),dim=c(2,3,4))
apply(x3, c(1,2),mean) #在第一维和第二维组成的平面上按照第三维进行求平均值
#也就可以理解为一个立方体，一维和二维组成的平面按照第三维压下去
```


### r语言函数-mapply
```r
#mapply可以视为lapply的多元版本
#mapply(函数/函数名，数据，函数相关的参数)
list(a=rep(1,4),b=rep(2,3),c=rep(3,2),d=rep(4,1))

mapply(rep, 1:4,4:1) #rep后的两个参数都是rep的参数

s <- function(n,mean,std){
  rnorm(n,mean,std) #从均值为mean、标准差为std的总体中抽取n个数据
}
#n代表从正态分布中抽取的数据的个数
#mean代表正态分布总体的均值
#std代表随机分布的标准差.....

s(4,0,1)

mapply(s,1:5,5:1,2) #相当于下面的一句话,mapply应用起来更加方便
list(s(1,5,2),s(2,4,2),s(3,3,2),s(4,2,2),s(5,1,2))

```


### r语言函数-tapply
```r
#tapply对向量的子集进行操作
#tapply(参数):tapply(向量，因子/因子列表，函数/函数名)
x<-c(rnorm(5),runif(5),rnorm(5,1)) #最后一个参数代表均值为1标准差为0的正态分布

f<-gl(3,5)#建立因子，第一个参数代表有几个水平，第二个参数代表每个水平下有几个元素

tapply(x,f,mean) #对x这个向量按照因子的水平进行分组，对每一组求均值
tapply(x,f,mean ,simplify = FALSE) #simplify默认为TRUE，原来结果是列表，改为FALSE后，变为了一个向量

```



### r语言函数-split
```r
#split根据因子或因子列表将向量或其他对象分组
#通常与lapply一起使用
#split(向量/列表/数据框，因子/因子列表)

x<-c(rnorm(5),runif(5),rnorm(5,1))

f<-gl(3,5)

split(x,f)

lapply(split(x,f), mean) #对于每一个因子求均值

head(airquality) #引用数据集，查看前六行

s<-split(airquality,airquality$Month) #按照month分组，和数据库的group by很像

table(airquality$Month)  #计算每个月有多少条记录

lapply(s, function(x) colMeans(x[,c("Ozone","Wind","Temp")])) #以向量显示结果
sapply(s, function(x) colMeans(x[,c("Ozone","Wind","Temp")],na.rm = TRUE))
#在计算列的平均值是不要包含那些缺失值

sapply(s, function(x) colMeans(x[,c("Ozone","Wind","Temp")])) #以列表显示结果
```

### r语言函数-排序
```r
#sort对向量进行排序，返回排好序的内容
#order返回排好序的内容的下标/多个排序标准
x<-data.frame(v1=1:5,v2=c(10,7,9,6,8),v3=11:15,v4=c(1,1,2,2,1))

sort(x$v2) #对数据框v2的元素进行排序
sort(x$v2,decreasing = TRUE) #降序排序

y<-order(x$v2) #返回了下标

x[order(x$v2),] #一定不要忘记写逗号

x[order(x$v4,x$v2,decreasing = TRUE),] #v4为主要标准,降序排徐
```

### 总结数据信息
```r

```

## 学习感悟
R语言基本函数，用法多变，要好好琢磨(｡･ω･｡)

4k壁纸￣ω￣=  
[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-20/57117624.jpg)

《道德经》
> 善为士者不武；  
善战者不怒；  
善胜敌者不与；  
善用人者为之下。  
是谓不争之德，  
是谓用人之力，  
是谓配天，  
古之极。  
