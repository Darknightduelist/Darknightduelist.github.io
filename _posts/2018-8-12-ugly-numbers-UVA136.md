---
layout: post
title:  "丑数（Ugly Numbers UVA 136）"
date:   2018-08-12 12:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-14/33427643.jpg
author: DND
---

丑数，这真是个题才(^・x・^)。

博客没有想象的那么难改，至少最基本的功能可以运行了，流量统计也可以加上了ミ(・・)ミ

* 
{:toc}

## 算法

### 题目描述
```
丑数是指不能被2,3,5以外的其他素数整除的数。把丑数从小到大排列起来，结果如下：

1,2,3,4,5,6,8,9,10,12,15...

求第1500个丑数

【分析】

从小到大生成各个丑数。最小的丑数是1，而对于任意的丑数x,2x,3x和5x也都是丑数。
这样，就可以用一个优先队列保存所有已生成的丑数，每次取出最小的丑数，
生成3个新的丑数。需要注意的是，同一个丑数有多种生成方式，
所以需要判断一个丑数是否已经生成过。

```

### 代码部分

```c++
#include <iostream>
#include <cstdio>
#include <queue>
#include <set>
#include <vector>
using namespace std;
int coeff[3]={2,3,5};
int main()
{
    priority_queue< long long int,vector<long long int>,greater<long long int> > pq;
    set<long long int> s;
    pq.push(1);
    s.insert(1);
    for(int i=1;;i++){
        long long int x=pq.top();
        pq.pop();
        if(i==1500){
            cout << "The 1500'th ugly number is "<<x<<"."<< endl;
            break;
        }
        for(int j=0;j<3;j++){
            long long int x2=x*coeff[j];
            if(!s.count(x2)){
                s.insert(x2);
                pq.push(x2);
            }
        }
    }
    return 0;
}

```


### 代码感悟
代码比较简单，原来的思路没用到优先队列，因此需要每一次加入元素都要排序，耗时长，代码多，果断改用优先队列︽⊙_⊙︽

日常4k壁纸￣ω￣=  

[(图片链接)](http://or4d8nhvk.bkt.clouddn.com/18-8-14/68215752.jpg)

