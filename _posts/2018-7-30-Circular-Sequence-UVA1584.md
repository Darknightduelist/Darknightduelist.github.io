---
layout: post
title:  "环状序列(Circular Sequence UVA1584)"
date:   2018-07-30 22:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-7-31/90748701.jpg
author: DND
---

第三章的最后一道例题，做的我好辛苦(Ｔ▽Ｔ)

题目比较简单，但是为啥我就想了个这么笨的方法呢(ŎдŎ；),虽然方法比较笨，但是还是做了出来，
花了一下午加上半晚上。虽然没有敲代码的天赋，尽力做就好，没有任何理由可以成为前进路上退缩的借口。
(￣▽￣)~*

* 
{:toc}

## 算法

### 题目描述
```
长度为n的环状串有n种表示方法，分别为从某个位置开始顺时针得到，
在这些排列中字典顺序最小的称“最小表示”。
如CTCC的最小表示为CCCT，CGAGTCAGCT的最小表示为AGCTCGAGTC。

样例输入：
2
CGAGTCAGCT
CTCC

样例输出：
AGCTCGAGTC
CCCT

```

### 代码部分

```c++
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_SIZE 102
#define LONG_LENGTH 10000
char str_arr[MAX_SIZE];
char big_arr[MAX_SIZE][MAX_SIZE];
char temporary_arr[MAX_SIZE];
char temporary_arr2[MAX_SIZE];
char final_arr[MAX_SIZE];
int main()
{
    int t;
    scanf("%d",&t);
    while(t--)
    {
        memset(big_arr,'\0',sizeof(big_arr));
        memset(str_arr,'\0',sizeof(str_arr));
        memset(temporary_arr,'\0',sizeof(temporary_arr));
        memset(temporary_arr2,'\0',sizeof(temporary_arr2));
        memset(final_arr,'z',sizeof(final_arr));
        scanf("%s",&str_arr);
        int length = strlen(str_arr);
        int i,j,t,k,flag=0,ti=0,tj=0;
        for(j=0; j<length; j++)
        {
            tj=0;
            for(i=j; i<length; i++)
            {
                big_arr[ti][tj]=str_arr[i];
                ++tj;
            }
            if(j>=1)
            {
                for(k=0; k<j; k++)
                {
                    big_arr[ti][tj]=str_arr[k];
                    ++tj;
                }
            }
            ++ti;
        }
        for(i=0; i<length-1; i++)
        {
            for(j=0; j<length; j++)
            {
                temporary_arr[j]=big_arr[i][j];
                temporary_arr2[j]=big_arr[i+1][j];
            }
            if((strcmp(temporary_arr,temporary_arr2))<=0)
            {
                if((strcmp(final_arr,temporary_arr))>=0)
                {
                    strcpy(final_arr,temporary_arr);
                }
            }
            else if((strcmp(temporary_arr,temporary_arr2))>0)
            {
                if((strcmp(final_arr,temporary_arr2))>=0)
                {
                    strcpy(final_arr,temporary_arr2);
                }
            }
        }
        for(i=0; i<length; i++)
        {
            printf("%c",final_arr[i]);
        }
        printf("\n");
    }
}

```
### 代码感悟
这个题主要分为两部分，一部分是将给出的字母序列的环状组合的所有组合形式放在一个字符串形式的二维数组中，第二部分是将二维数组中每一行的字符串两两进行比较，选出字典序最小的一种序列。这其中用到了5个数组(˘•ω•˘)，，，，，，我也不知道为啥用到了这么多，当时可能就是为了找起来方便…(﹂_﹂)…

emmm.....快乐的时光(*/ω＼*)又到来了

last but one ，ヾ(ｏ･ω･)ﾉ给大家分享一张画质4k的外星人桌面背景(oﾟ▽ﾟ)o  

![](http://or4d8nhvk.bkt.clouddn.com/18-7-31/55488939.jpg)


tailender  -- 《道德经》(～￣▽￣)～ 那个“纇（lei）”字是真好（nan）找( • ̀ω•́ )✧


> 上士闻道，勤而行之；  
中士闻道，若存若亡；  
下士闻道，大笑之。  
不笑不足以为道。  
故建言有之：  
明道若昧；  
进道若退；  
夷道若纇；  
上德若谷；  
广德若不足；  
建德若偷；  
质真若渝；  
大白若辱；  
大方无隅；  
大器晚成；  
大音希声；  
大象无形；  
道隐无名。  
夫唯道，善贷[且成。  


