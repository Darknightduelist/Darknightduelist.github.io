---
layout: post
title:  "R语言"
date:   2018-08-23 12:59:49 +0800
categories: R-program-language
tags: R-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-23/24965251.jpg
author: DND
---

7天就要返校了(｡･ω･｡)

* 
{:toc}

## R语言的进阶
### r语言基础
```r
x<-rnorm(100)
head(x)
tail(x)
mean(x)
sd(x)
min(x)
max(x)
3^3 #幂的表示形式
log(7)
log10(7)
pi  #π的表现形式
sin(pi/2)
options(digits = 22) #设置内置对象显示的小数位数
options(digits = 6) 
1/0 #得到的是Inf，也就是∞
0/0 #得到NaN
ls() #显示出来所有的变量,与linux中的命令很像
rm(x) #清理对象，回收空间
integrate(dnorm, -1.96, 1.96) #计算积分，第一个参数是要计算积分的曲线，第二三个参数是区间
paste("A",1:6,sep = "") #字符串的链接，sep是字符串之间的分隔符，sep默认为空格
round(1.35)#四舍五入取整

x<-round(runif(20,min = 0,max = 20))
y<-round(runif(20,min = 0,max = 20))
plot(x,y) #画图函数的用法,神奇

c() #连接函数
```
plot函数的作图例子：  
![](http://or4d8nhvk.bkt.clouddn.com/18-8-23/61388468.jpg)


### r语言函数plot
①
```
plot(sin,0,2*pi)
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-23/32465976.jpg)
②
```
x<-seq(0,6,length=100) #seq将0~6划分为100等份
y<-2*x+3+rnorm(100)
plot(x,y)
```
![](http://or4d8nhvk.bkt.clouddn.com/18-8-23/52041308.jpg)


### r语言的三种循环(for while repeat)
```r
for(i in 1:30){
  cat(i,"+",i,"=",i+i,"\n") #输出函数，标准输出
  
}

d<-data.frame(a=1:2,b=2:3)


for(i in 1:30){
  if(i==1) cat(i,"+",i,"=",i+i,"\n") else 
           cat(i,"\n")
}

#还有while循环和repeat循环，break终止循环，next相当于C语言的continue的用法

k<-0
y<-abs(rnorm(1000))
i<-0
while(k<3&i<1000){
  i<-i+1
  temp<-y[i]
  k<-k+(temp>2) #注意逻辑表达式
}
rm(temp)
i


eye.colors<-c("brown","blue","green","yellow","grey")
eyecolor<-data.frame(personId=1:100,color=sample(eye.colors,100,replace=T))
#sample随机抽取，replace=T是有放回抽样
i<-0
list.of.ids<-numeric(0)
repeat{
i<-i+1
if(eyecolor$color[i]=="yellow" | eyecolor$color=="blue") next
list.of.ids<-c(list.of.ids,eyecolor$personId[i])
if(i==100 | length(list.of.ids)==20) break
}
list.of.ids

```


### r语言导入导出数据(write.table)
```r

getwd()#查看当前工作路径

args(read.table) #参数为函数名，返回函数的参数名及其对应的默认值


dat<-read.table("C:/Users/asus/Desktop/test-R/testdat1.dat",
header = TRUE,skip=5,nrow=2) #读取文本中的数据


mydat<-data.frame(
  x1=c(2,2,3,3,1,1),
  x2=c(0.3,1,2.1,2.2,0.1,0.2),
  x3=c(0.01,0.11,0.04,0.02,0.1,0.06)
)

write.table(mydat,file="C:/Users/asus/Desktop/test-R/testdat2.dat",
  row.names = TRUE,col.names = TRUE,sep = ", "
) #导出数据


# write.csv() 逗号分隔，点号作为小数点
# write.csv2() 冒号分隔，逗号作为小数点

#通过这两个函数导入的数据可以直接用excel打开，用法和write.table的一样

```



### r语言将数据写入到文件
```r
#基本的写函数
cat("Test file for cat\n",round(rnorm(5),3),"\n",file = "C:/Users/asus/Desktop/test-R/testdat2.dat")
#writeLines()也是写入函数

sink("C:/Users/asus/Desktop/test-R/testdat2.dat") #输出指向的文件，相当于结果在这个文件里输出
x<-1:5
y<-1:3
outer(x,y) #生成矩阵
sink()

m<-1:3
n<-rpois(10,4) #泊松分布终于出现了 （` . `）
dump(c("m","n"),file = "C:/Users/asus/Desktop/test-R/testdat2.dat") #将对变量的赋值写到文件中

lis<-list(x=1:5,y=3,z=c("a","b","c"))
dput(lis,file = "C:/Users/asus/Desktop/test-R/testdat2.dat") #同dump函数类似

#应用文件链接
f2<-file("C:/Users/asus/Desktop/test-R/testdat2.dat",open = "w")
cat("Header of file\n\n",file = f2)
mat<-matrix(round(rnorm(12),8),ncol = 3)
write.table(mat,file = f2,row.names = FALSE,col.names = FALSE，append=TRUE)
close(f2)
```

### r语言应用文件连接
```r
f2<-file("C:/Users/asus/Desktop/test-R/testdat2.dat",open = "w")
cat("Header of file\n\n",file = f2)
mat<-matrix(round(rnorm(12),8),ncol = 3)
write.table(mat,file = f2,row.names = FALSE,col.names = FALSE，append=TRUE)
close(f2)
```


## 学习感悟
好多函数啊，，有点记不住了￣へ￣，不过画图的函数是真的有意思(｀・ω・´)

4k壁纸(￣▽￣)~*
[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-14/91972922.jpg)

