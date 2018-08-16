---
layout: post
title:  "C/C++ Algorithm"
date:   2018-07-24 10:24:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-7-24/11352791.jpg
author: DND
---

转转悠悠大学已过一半，最后只能冷不丁地冒一句：好快啊。

学过的该忘的不该忘的都忘了，惭愧的很，看着博客仅有的两篇文章，更是觉得自己虚度了不少光阴。
都说似水年华，看来一点不假。
开学就真的成了大三狗了，有好多话想说，不过没有什么文采说不出口，
比不了大咖们的出口成章，我也就能胡诌几句话了。
假期里无聊，写几篇博客充实一下生活。

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
