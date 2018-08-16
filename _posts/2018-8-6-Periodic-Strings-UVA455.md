---
layout: post
title:  "周期串（Periodic Strings UVA455)"
date:   2018-08-6 12:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-7/43886495.jpg
author: DND
---

这道题结果是对的，，但是输出格式有误（presentation error），UVA交不上￣へ￣


* 
{:toc}

## 算法

### 题目描述
```
如果一个字符串可以由某个长度为k的字符串重复多次得到，则称该串以k为周期。例如，abcabcabcabc以3为周期（注意，它也以6和12为周期）。
输入一个长度不超过80的字符串，输出其最小周期。

样例输入：
1
HoHoHo

样例输出：
2

```

### 代码部分

```c++
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <cstring>
#include <string>
#define MAX_SIZE 80+10
using namespace std;
char string_arr[MAX_SIZE];
char tem_arr[MAX_SIZE];
int main()
{
    int t,y=0;
    scanf("%d",&t);
    while(t--)
    {
        memset(string_arr,'\0',sizeof(string_arr));
        scanf("%s",string_arr);
        int arr_length=strlen(string_arr);
        int asfor=0;
        for(int k=2; k<arr_length; k++)
        {
            if(arr_length%k==0)
            {
                asfor++;
                break;
            }
        }
        if(asfor>0)
        {
            int i;
            for(i=0; i<arr_length; i++)
            {
                int m=i+1;
                memset(tem_arr,'\0',sizeof(tem_arr));
                strncpy(tem_arr,string_arr,m);
                int tem_length=strlen(tem_arr);
                double t=(arr_length*1.0)/tem_length;
                int flag=arr_length/tem_length;
                if(t>flag*1.0)
                {
                    continue;
                }
                else
                {
                    y=0;
                    int x;
                    char tem_arr_two[MAX_SIZE];
                    memset(tem_arr_two,'\0',sizeof(tem_arr_two));
                    for(x=1; x<=flag; x++)
                    {
                        string s=string_arr;
                        strcpy(tem_arr_two,
                               (s.substr(tem_length*(x-1),tem_length).c_str()));
                        if(strcmp(tem_arr,tem_arr_two)!=0)
                        {
                            y++;
                            break;
                        }
                    }
                    if(y==0)
                    {
                        if(t==0)
                        {
                            printf("%d",tem_length);
                        }
                        else
                        {
                            printf("%d\n\n",tem_length);
                        }

                        break;
                    }
                }
            }
            if(i==arr_length&&y==0)
            {
                if(t==0)
                {
                    printf("%d",arr_length);
                }
                else
                {
                    printf("%d\n\n",arr_length);
                }
            }
        }
        else
        {
            if(arr_length==1)
            {
                if(t==0)
                {
                    printf("1");
                }
                else
                {
                    printf("1\n\n");
                }
            }
            else
            {
                int pk=0;
                for(int h=0; h<arr_length-1; h++)
                {
                    if(string_arr[0]!=string_arr[h+1])
                    {
                        pk++;
                    }
                }
                if(pk>0)
                {
                    if(t==0)
                    {
                        printf("%d",strlen(string_arr));
                    }
                    else
                    {
                        printf("%d\n\n",strlen(string_arr));
                    }
                }
                else
                {
                    if(t==0)
                    {
                        printf("1");
                    }
                    else
                    {
                        printf("1\n\n");
                    }
                }
            }
        }
    }
}

```


### 代码感悟
做的我心累(ŎдŎ；)，代码写的比较长，从开始就想要缩短判断的时间（实际上是增加了(˘•ω•˘)），导致代码有点乱、长，变量比较多。
思路是分别从头截取原字符串长度为1,2,3...n最大为原字符串长度的字符串，再用截取的字符串与原字符串按照截取字符串的长度进行等长分隔后的字符串一一进行比较，如果不相同，就对下一个字符串按照刚才所属步骤进行判断，一旦找到第一个，就停止判断，此时该字符串的长度就是最小长度。

4k洛克希德侦察机壁纸(￣▽￣)~*

[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-7/36246399.jpg)

日常《道德经》ヽ(°▽、°)ﾉヾ(๑╹◡╹)ﾉ"

> 反者道之动，  
弱者道之用，  
天下万物生于有，  
有生于无。


