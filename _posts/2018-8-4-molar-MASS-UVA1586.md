---
layout: post
title:  "分子量（Molar Mass UVA1586)"
date:   2018-08-4 12:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-5/69538067.jpg
author: DND
---

对字符串的处理，还好(ﾟωﾟ)ﾉ☆ 


* 
{:toc}

## 算法

### 题目描述
```
给出一种物质的分子式(不带括号)，求分子量。本题中的分子式只包含4种原子，
分别为C, H, O, N,原子量分别为12.01, 1.008, 16.00, 14.01(单位:g/mol)。
例如，C6H5OH的分子量为94.108g/mol。

样例输入：
4
C
C6H5OH
NH2CH2COOH
C12H22O11

样例输出：
12.010
94.108
75.070
342.296

```

### 代码部分

```c++
#include <iostream>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#define MAX_SIZE 1000
using namespace std;
char arr[MAX_SIZE];
char tem_arr[MAX_SIZE];
int main()
{
    int t;
    scanf("%d",&t);
    while(t--)
    {
        memset(arr,'\0',sizeof(arr));
        scanf("%s",&arr);
        double sum=0.0;
        for(int i=0; arr[i]!='\0'; i++)
        {
            if(arr[i]=='C')
            {
                memset(tem_arr,'\0',sizeof(tem_arr));
                if(arr[i+1]>='0'&&arr[i+1]<='9')
                {
                    int j;
                    int t=0;
                    for(j=i+1; arr[j]>='0'&&arr[j]<='9'; j++)
                    {

                        tem_arr[t]=arr[j];
                        ++t;
                    }
                    int k=atoi(tem_arr);
                    sum +=12.01*k;
                }
                else
                {
                    sum +=12.01;
                }
            }
            if(arr[i]=='H')
            {
                memset(tem_arr,'\0',sizeof(tem_arr));
                if(arr[i+1]>='0'&&arr[i+1]<='9')
                {
                    int j;
                    int t=0;
                    for(j=i+1; arr[j]>='0'&&arr[j]<='9'; j++)
                    {

                        tem_arr[t]=arr[j];
                        ++t;
                    }
                    int k=atoi(tem_arr);
                    sum +=1.008*k;
                }
                else
                {
                    sum +=1.008;
                }
            }
            if(arr[i]=='O')
            {
                memset(tem_arr,'\0',sizeof(tem_arr));
                if(arr[i+1]>='0'&&arr[i+1]<='9')
                {
                    int j;
                     int t=0;
                    for(j=i+1; arr[j]>='0'&&arr[j]<='9'; j++)
                    {

                        tem_arr[t]=arr[j];
                        ++t;
                    }
                    int k=atoi(tem_arr);
                    sum +=16.00*k;
                }
                else
                {
                    sum +=16.00;
                }
            }
            if(arr[i]=='N')
            {
                memset(tem_arr,'\0',sizeof(tem_arr));
                if(arr[i+1]>='0'&&arr[i+1]<='9')
                {
                    int j;
                     int t=0;
                    for(j=i+1; arr[j]>='0'&&arr[j]<='9'; j++)
                    {

                        tem_arr[t]=arr[j];
                        ++t;
                    }
                    int k=atoi(tem_arr);
                    sum +=14.01*k;
                }
                else
                {
                    sum +=14.01;
                }
            }
        }
        printf("%.3lf\n",sum);
    }
    return 0;
}



```


### 代码感悟
虽然代码很长，但是不难，用到了一个关键函数atoi，将纯字符串char型数组转化为整形数字，其他的没什么好说的了(*❦ω❦)

日常分享4k壁纸(✪ω✪)  

[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-5/55943846.jpg)

《道德经》经典语录ヾ(ｏ･ω･)ﾉ

> 大道废，有仁义。  
智慧出，有大伪。  
六亲不和，有孝慈。  
国家昏乱，有忠臣。  


