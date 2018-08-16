---
layout: post
title:  "计算组合数"
date:   2018-08-1 22:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-3/68009754.jpg
author: DND
---

一道看似容易写出来的题目，实则是有个坑▄█▀█●，代码乍看一眼没问题，实际当结果比较大时，就容易越界。


* 
{:toc}

## 算法

### 题目描述
```
编写函数，参数是两个非负整数n和m，返回组合数C（n,m）=(m!)/(n!*(n-m)!),其中m<=n<=25.

样例输入：
25 12

样例输出：
5200300
```

### 代码部分

```c++
#include <stdio.h>
#include <stdlib.h>

long long calxy(int n,int m){
     long long tem=1;
     int i;
     for(i=(m+1);i<=n;i++){
        tem=tem*i;
     }
     for(i=1;i<=n-m;i++){
        tem=tem/i;
     }
     return tem;

}
int main()
{
    int n,m;
    scanf("%d%d",&n,&m);
    printf("%lld",calxy(n,m));
    return 0;
}

```

再贴上自己的错误代码(｡･ω･｡)
```c++
#include <stdio.h>
#include <stdlib.h>
long long int test()
{
    long long int n,m,i,sum1=1,sum2=1,sum3=1;
    scanf("%lld%lld",&n,&m);
    for(i=n; i>=1; i--)
    {
        sum1=sum1*i;
    }
    for(i=m; i>=1; i--)
    {
        sum2=sum2*i;
    }
    for(i=(n-m); i>=1; i--)
    {
        sum3=sum3*i;
    }
    long long tem;
    tem=sum1/sum2;
    return (tem/sum3);

}
int main()
{
    printf("%lld",test());
    return 0;
}


```

### 代码感悟
这道题最重要的是注意在计算结果的过程中，中间计算的数据有可能越界(～￣▽￣)～ 

来一张4k的《疯狂动物城》中小兔纸的桌面壁纸(｀・ω・´)  
[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-3/60829114.jpg)

最后日常《道德经》(σﾟ∀ﾟ)σ..:*☆

> 持而盈之，不如其已。  
揣而锐之，不可长保。  
金玉满堂，莫之能守。  
富贵而骄，自遗其咎。  
功遂身退，天之道也。


