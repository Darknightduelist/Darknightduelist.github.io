﻿---
layout: post
title:  "生成元(Digit Generator UVA1583)"
date:   2018-07-29 11:23:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-7-31/53424252.jpg
author: DND
---

没撒好说的，直接步入正题了(〃'▽'〃)

* 
{:toc}

## 算法

### 题目描述
```
如果x加上x的各位数之和等于y，就说x是y的生成元.
给出n(1<=n<=100000),求n的最小生成元,  无解输出0.
例如 n=216,121,2005 应输出 198 0 1979
输入的第一行是几个样例，剩下的是输入的样例
样例输入：
3 
216 
121 
2005

样例输出：
198 
0 
1979

```

### 代码部分

```c++
#include <stdio.h>
#include <stdlib.h>
#define MAX_SIZE 100010
int arr[MAX_SIZE];
int main()
{
    memset(arr,0,sizeof(arr));
    int T,n,i;
    for(i=1; i<MAX_SIZE; i++)
    {
        int x=i,y=i;
        while(x>0)
        {
            y=y+x%10;
            x=x/10;
        }
        if(arr[y]==0||i<arr[y])arr[y]=i;

    }
    scanf("%d",&T);
    while(T--){
        scanf("%d",&n);
        printf("%d\n",arr[n]);
    }

    return 0;
}



```
### 代码感悟
这个题开始的思路是每个数去判断一次，结果发现很麻烦，而且很耗时(｀・ω・´)，于是改成了书上的另一种解法：只需一次性枚举100000以内的所有正整数m，标记“m加上m的各个数字之和得到的数有一个生成元是m”，最后查表即可。

倒数第二项，ヾ(ｏ･ω･)ﾉ给大家分享一张4k森林鹿桌面背景(oﾟ▽ﾟ)o  
[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-7-31/42591922.jpg)



