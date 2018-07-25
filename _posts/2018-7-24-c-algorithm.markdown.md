﻿---
layout: post
title:  "C/C++ Algorithm"
date:   2018-07-24 10:24:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-7-24/11352791.jpg
author: DND
---

晃晃荡荡大学已过一半，最后只能感叹一句：好快啊。读了不少书可依旧没有啥文采(这可能与天分有关系ヽ(ー_ー)ノ)，假期的第一篇博客只能这样的形式来开头了，这就很难受。再回首大学这两年，有难忘的，又后悔的，有骄傲的，有高兴的，这些经历不管怎么样都是我的人生所必须的，无论自己是否愿意。现在这个年纪仍然有些事情看不开，我也没啥办法，也就这样了。博客好长时间不写了，话说写过的博客也没有几篇，自己学过的东西一样一样地都还给了老师，真是感到惭愧，读过的书也没有做过什么笔记，看过了就看过了，没有任何痕迹(脑子里更不会有痕迹)。自此，重拾博客，复习c/c++，学习算法，写读书笔记，尽力让每一天过得充实有趣。生活可以无趣，但自己一定要有趣。Fighting！

* 
{:toc}

## 算法

### 题目描述
```
输入正整数a,b,c,输出a/b的小数形式，精确到小数点后c位。
a，b≤10^6,c≤100。输入包含多组数据，结束标记记为a=b=c=0.
样例输入：
1 6 4
0 0 0
样例输出：
Case 1:0.1667
```

### 代码部分

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
      int a,b,c,i,flag=0;
      while(scanf("%d%d%d",&a,&b,&c)==3){
        if(a==0&&b==0&&c==0){
            break;
        }
        else{
            printf("Case %d:%d.",++flag,a/b);
            a=a%b;
            for(i=0;i<c-1;i++){
                a=a*10;
                printf("%d",a/b);
                a=a%b;
            }
            if(((a*10)/b)>=5){
                printf("%d\n",(a*10)/b+1);
            }else{
            printf("%d\n",(a*10)/b);
            }
        }
      }
}
```
### 代码感悟
这道题看似很简单，实则做起来一点都是不是想的那么简单（根本原因是自己太菜），主要加深了自己对除法和取余操作的理解。（ps：这篇简单的博客耗了我1个小时.........(｀・ω・´)）