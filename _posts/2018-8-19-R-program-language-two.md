---
layout: post
title:  "R语言"
date:   2018-08-19 12:59:49 +0800
categories: R-program-language
tags: R-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-19/6736176.jpg
author: DND
---

RRRRRRRRRRRRRRRRRRRRRRRR

* 
{:toc}

## R语言的操纵数据、构建子集
###基本方法
```
x<-1:10
x[1]
x[1:5]
x[x>5] #取出大于5的数据
x>5  #对每一个元素进行判断
x[x>5&x<7] #注意与C语言的区别
x[x<3|x>7]
y<-1:4
names(y)<-c("a","b","c","d")
y[2]
y["b"]
```
###矩阵的子集
```
x<-matrix(1:6,nrow=2,ncol = 3)
x[1,2]  #注意与C语言的区别
x[1,]  #返回第一行的内容
x[2,c(1,3)] #取出第二行第一列和第三列的内容
class(x[1,2]) #传出的是一个向量
x[1,2, drop=FALSE] #传出的是一个矩阵,行和列都显示出来
```


###数据框的子集
```
X<-data.frame(v1=1:5,v2=6:10,v3=11:15)

X$v3[c(2,4)]<-NA #对X数据框中的第三列第二个和第四个元素设置成缺失值

y<-data.frame(v1=c(1:5),v2=c(6:10),v3=c(11:15))

y[,2]

y[,"v2"]

y[(y$v1<4 & y$v2>=8),] #选出v1列中小于4，v2列中大于等于8的行

y[y$v1>2,]

y[which(y$v1>2),] #结果与上面的一句话相同

?which #查看函数

which(y$v1>2) #返回下标

y$v1>2  #返回逻辑值,注意与which的区别

p<-subset(y,y$v1>2) #第一个参数是要操作的数据框，第二个参数是条件

```


###列表的子集
```
x<-list(id=c(1:4),height=170,gender="male")

x[1]

x["id"]  #这样既拿到名字又拿到内容

x[[1]]   #这样既拿到名字又拿到内容

x[["id"]]  #这样是只拿到内容

x$id  #这样是只拿到内容

x[c(1,3)] #取出第一个和第三个元素的内容

y<-"id"
x[[y]]

x$id  #此法只能直接引用名字，而不能引用变量

a<-list(m=list(1,2,3,4),b=c("MOnday","Tuelist"))

a[[1]]

a[1]

a[[1]][[2]] #取出第一个元素中的第二个内容
a[[1]][2]  #区别于上一条

a[[c(1,3)]] #取出第一个元素中的第3个内容
a[[c(2,1)]]

# particle matching

l<-list(asdfghj =c(1:10))

l$asdfghj

l$a  #这就是不完全匹配，十分人性化，与上一条语句一样

l[["a",exact=FALSE]] #关闭掉精确匹配

x<-list(asdfghj=c(1:10),b=c(1,2),aaa="3:5")

x$a  #如果重复则是空值

x$as #不完全匹配
```



###处理缺失值
```
x<-c(1,NA,2,NA,3)

b<-is.na(x)

x[b]

x[!b]

x<-c(1,NA,2,NA,3)
y<-c("a","b",NA,"c",NA)
z<-complete.cases(x,y) #比较两者相同位置是不是缺失值，如果不是则返回true
z<-complete.cases(x) #等价于is.na()


x[z] #返回不是缺失值的元素

y[z]  #返回不是缺失值的元素

library(datasets) #加载一个包

head(airquality)  #查看airquelity有哪些变量

g<-complete.cases(airquality)

airquality[g,][1:10,]  #返回前十条中不是缺失值的记录
```



###向量化操作
```
x<-1:5
y<-6:10
z<-x+y #对应的每一个元素做加法运算,这就比一些该机语言方便很多
z1<-x/y
z2<-x*y


x<-matrix(1:4,nrow=2,ncol=2)
y<-matrix(rep(2,4),nrow = 2,ncol = 2) #rep函数是将第一个参数重复第二个参数的次数
k<-x*y
k1<-x/y
k2<-x%*%y  #这样才是矩阵的乘法，也就是线性代数中所讲的矩阵的乘法
```


## 学习感悟
R语言中对五种基本类型对象的基本操作( • ̀ω•́ )✧

4k壁纸￣ω￣=  
[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-20/4213785.jpg)

《道德经》
> 治大国，若烹小鲜。  
以道莅天下，其鬼不神；  
非其鬼不神，其神不伤人；  
非其神不伤人，圣人亦不伤人。  
夫两不相伤，故德交归焉。  

