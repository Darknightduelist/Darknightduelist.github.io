---
layout: post
title:  "数数字（Digit Counting UVA1225)"
date:   2018-08-5 12:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-5/44939082.jpg
author: DND
---

这道题如果不给出输入输出数据的话，，，，感觉有点歧义─━ _ ─━✧


* 
{:toc}

## 算法

### 题目描述
```
把前n个整数顺序写在一起：1234574854552452...数一数0~9各出现多少次（输出10个整数，分别是0,1，....，9出现的次数）

样例输入：
2
3
13

样例输出：
0 1 1 1 0 0 0 0 0 0
1 6 2 2 1 1 1 1 1 1

```

### 代码部分

```c++
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_SIZE 10000+10
using namespace std;
int arr[MAX_SIZE];
int main()
{
    int t,n;
    scanf("%d",&t);
    while(t--)
    {
        memset(arr,0,sizeof(arr));
        scanf("%d",&n);
        for(int i=1;i<=n;i++){
            int flag=i;
            while(flag){
                int t=flag%10;
                arr[t]++;
                flag=flag/10;
            }
        }
        for(int j=0; j<10; j++)
        {
            if(j==0){
                cout<<arr[j];
            }else{
                cout<<" "<<arr[j];
            }
        }
        cout<<endl;
    }
    return 0;
}


```


### 代码感悟
读懂题就很简单，主要考察对取余和除的理解(～￣▽￣)～ 

海贼王4k壁纸（里面没有(･□´･ｷ)＝＝＝⊃))←路飞）(￣▽￣)~*

![](http://or4d8nhvk.bkt.clouddn.com/18-8-5/71248784.jpg)

《道德经》ヽ(°▽、°)ﾉヾ(๑╹◡╹)ﾉ"

> 绝圣弃智，民利百倍。  
绝仁弃义，民复孝慈。  
绝巧弃利，盗贼无有。  
此三者以为文不足，  
故令有所属。  
见素抱朴，  
少私寡欲。  
绝学无忧。  


