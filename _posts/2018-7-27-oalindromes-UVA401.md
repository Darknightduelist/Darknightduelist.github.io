---
layout: post
title:  "回文词（Oalindromes UVA401）"
date:   2018-07-27 20:57:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-7-27/91340908.jpg
author: DND
---

今天的第二篇博客，奥西里斯的天空龙镇楼(ノ￣▽￣)

这个题是个关于回文串的问题，感觉还好，以前做过的回文串还有点印象(￣▽￣)~*，自己半年多没接触任何算法，假期里要加油了ヾ(◍°∇°◍)ﾉﾞ

* 
{:toc}

## 算法

### 题目描述
![](http://or4d8nhvk.bkt.clouddn.com/18-7-27/83966553.jpg)
```
输入一个字符串，判断它是否为回文以及镜像串。输入字符串保证不含数字0.所谓回文串，就是反转之后原串相同，
如abba和madam。所谓镜像串，就是左右镜像之后和原串相同，如2S和3AIAE。
注意，并不是每个字符在镜像之后都能得到一个合法字符，
本题中，每个字符的镜像如上所示，（空白项表示该字符镜像后不能得到一个合法的字符）。
样例输入：

NOTAPALINDROME 
ISAPALINILAPASI 
2A3MEAS 
ATOYOTA

样例输出：
NOTAPALINDROME -- is not a palindrome.
 
ISAPALINILAPASI -- is a regular palindrome.
 
2A3MEAS -- is a mirrored string.
 
ATOYOTA -- is a mirrored palindrome.
```

### 代码部分

```c++
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main()
{
    int flag1=1,flag2=1;
    char anystring[60];
    const char stringarr[21] = "AEHIJLMOSTUWXYZ12358";
    while(scanf("%s",anystring)==1)
    {

        flag1=1;
        flag2=1;
        int length =strlen(anystring);
        int i,j,k,tag=0;
        for(i=0; i<length/2; i++)
        {
            if(anystring[i]!=anystring[length-i-1])
            {
                flag1=0;
            }
        }
        int length2=strlen(stringarr);
        for(j=0; j<length; j++)
        {
            for(k=0; k<length2; k++)
            {
                if(anystring[j]==stringarr[k])
                {
                    ++tag;
                }
            }
        }
        if(tag!=length)
        {
            flag2=0;
        }
        if(flag1==1&&flag2==1)printf("%s -- is a mirrored palindrome.\n\n",anystring);
        if(flag1==1&&flag2==0)printf("%s -- is a regular palindrome.\n\n",anystring);
        if(flag1==0&&flag2==1)printf("%s -- is a mirrored string.\n\n",anystring);
        if(flag1==0&&flag2==0)printf("%s -- is not a palindrome.\n\n",anystring);
    }
}


```
### 代码感悟
这个题也没有什么可以总结的，记住回文串怎么判断就可以了，接下来又到了有趣的时刻了(★ᴗ★)
附上我很喜欢的《游戏王》的三张图(・∀・)
![](http://or4d8nhvk.bkt.clouddn.com/18-7-27/32533145.jpg)
![](http://or4d8nhvk.bkt.clouddn.com/18-7-27/64024113.jpg)
![](http://or4d8nhvk.bkt.clouddn.com/18-7-27/80024871.jpg)  
最后再来我很喜欢的《道德经》的一个小章节(o゜▽゜)o☆，（大家看起我来可能有点像个迂腐书生，但是我觉得这本书说的很有道理，是我看过的最能让人静下心来的书(ﾟ▽ﾟ*) ）
> 曲则全，枉则直，洼则盈，敝则新，少则得，多则惑。  
是以圣人抱一为天下式。  
不自见，故明；  
不自是，故彰；  
不自伐，故有功；  
不自矜，故长；  
夫唯不争，故天下莫能与之争。  
古之所谓“曲则全”者，岂虚言哉！  