---
layout: post
title:  "R语言"
date:   2018-08-18 12:59:49 +0800
categories: R-program-language
tags: R-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-17/13546235.jpg
author: DND
---

R语言是S语言的一个分支，用于统计分析、绘图的语言和操作环境。

R语言还有一个神奇的东西，就是它带有机器学习的包，这就很灵性(￣▽￣)／

* 
{:toc}

## R语言的安装、数据类型、函数

### 如何安装RStudio

R的安装包网址：cran.r-project.org
RStudio的网址：www.rstudio.com
安装的时候一定要注意这两个安装在同一个目录下，否则的话RStudio会出现难以名状的错误，这都是血的教训(T＿T)


### 获取帮助

?函数名（R的帮助文档）
--例如：?ml   #线性回归函数的各种东西

问题格式：
--操作系统，版本，哪一步产生的错误，预期是什么，得到的其他有用的信息
--例如：Win7 R 3.2.0 lm（） “seg fault on large data frame”

获取R中的数据集（也就是机器学习所需要的数据）
--date()
--查看数据集中的详细内容，例如：?InsectSprays


### 基本函数
```R
install.packages("carat")  #安装一个机器学习的包

library(caret)  #载入需要的包

methods("caret")#查看函数

getAnywhere("caret")#查看函数

x<-3.14 #赋值

class(x)#查看x的数据类型

```


### 对象属性(attribute)
```R
名称（name）
维度（dimensions：matrix，array）
类型（class）
长度（length）
```
### 对象的5种基本类型
```R
--字符（character）
--数值（numeric：real numbers）
--整数（integer）
--复数（complex）：1+2i
--逻辑（logical：True/False）

```
#### 向量 Vector(3种创建方式)
```R
①  x<-vector("character",length=10)
②  x1<-1:4
③  x2<-c("a","b","c") #需要输入每一种元素

x2<-c(1,"d",TRUE)  #x2最后结果是字符类型，自动转换
as.numeric(x2) #强制转换为数字类型
as.logical(x2) #强制转换为逻辑型变量
as.character(x2) #强制转换为字符类型
class(x2) #查看类型

向量的每一个元素都可以有名称
names(x1)<-c("a","b","c","d") #为每个元素赋予一个名字

```

#### 矩阵 Matrix(2种创建方式，维度只能等于2)
```R
①  x<-matrix(nrow=3,ncol=2)
x<-matrix(1:6,nrow=3,ncol=2) #为矩阵赋值1`6,按列赋值


②  y<-1:6
   dim(y)<-c(2,3)
dim(x) #查看矩阵的属性
attribute(x) #查看矩阵有哪些属性

rbind(y1,y2)#将矩阵进行拼接(按行拼接)
cbind(y1,y2)#将矩阵进行拼接(按列拼接)

```
#### 数组 Array(维度可以大于2)
```R
x<-array(1:24,dim=c(2,3,4)) #三维数组
```

#### 列表 List
```R
l<-list("a",2,10L,3+4i,TRUE) #为列表赋值
l2<-list(a=1,b=2,c=3) #为列表的元素赋予一个名字
l3<-list(c(1,2,3),c(4,5,6,7)) #相当于二维数组

x<-matrix(1:6,nrow=3,ncol=2)
dimnames(x)<-list(c("a","b"),c("c","d","e"))
#为二维数组的每行和每列赋予一个名字
```
#### 因子 Factor(分类数据/有序vs.无序)
```R
x<-factor(c("female","female","female","male","female"))

y<-factor(c("female","female","female","male","female"),levels =c("male","female") ) #注意两者基线水平不同

table(x) #查看x中各个因子的个数
unclass(x) #去掉因子的属性

```

#### 缺失值(missing value)
```R
--NA/NAN:NaN属于NA，NA不属于NaN，NAN一般表示数字类型的缺失值，NA一般表示的类型更广

is.na() #判断缺失值
is.nan() 

x <-c(1,2,3,NA,NA)
```

#### 数据框(data frame)
```R
--存储表格数据（tabular data）
--视为各元素长度相同的列表
  *每个元素代表一列数据
  *每个元素的长度代表行数
  *元素类型可以不同

df<-data.frame(id=c(1,2,3,4),name=c("a","b","c","d"),gender=c(TRUE,TRUE,FALSE,FALSE)) #这个感觉很像数据库中的表

nrow(df) #查看有多少行
ncol(df) #查看有多少列

df<-data.frame(id=c(1,2,3,4),name=c("a","b","c","d")）
data.matrix(df) #将矩阵转化为数据框
```

#### 日期(DATE)
```R
#date 距离1970.1.1的天数
x<-date()

x2<-Sys.Date()

class(x2)

x3<-as.Date("2015-01-01") #赋值

weekdays(x3) #2015.1.1是星期几

months(x3)

quarters(x3) #代表第几个季度

julian(x3)  #距离1970.1.1过去了多少天

x4<-as.Date("2016-01-01")

x4-x3

x<-Sys.time()

p<-as.POSIXlt(x)

names(unclass(p))

p$sec #显示p变量中的秒数

as.POSIXct(p)

as.Date("2015-01-01")

x4<-"Jan 1, 2015 01:01"

x6<-strptime(x4, "%B %d, %Y %H:%M")#字符转化为时间类型

```

## 学习感悟
R语言最基础的东西(｡･ω･｡)

日常分享4k壁纸￣ω￣=  
[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-18/51357056.jpg)

日常《道德经》
> 其政闷闷，其民淳淳；  
其政察察，其民缺缺。  
祸兮，福之所倚；  
福兮，祸之所伏；  
孰知其极？  
其无正也，  
正复为奇，  
善复为妖。  
人之迷，其日固久。  
是以圣人方而不割，  
廉而不刿，  
直而不肆，  
光而不耀。  

