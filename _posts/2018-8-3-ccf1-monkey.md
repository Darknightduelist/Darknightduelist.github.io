---
layout: post
title:  "约瑟环问题（CCF)"
date:   2018-08-03 12:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-5/78392145.jpg
author: DND
---

猴子猴子选选选选选选选选选选大王！！！


* 
{:toc}

## 算法

### 题目描述
```
有n个小朋友围成一圈玩游戏，小朋友从1至n编号，2号小朋友坐在1号小朋友的顺时针方向，
3号小朋友坐在2号小朋友的顺时针方向，……，1号小朋友坐在n号小朋友的顺时针方向。
游戏开始，从1号小朋友开始顺时针报数，接下来每个小朋友的报数是上一个小朋友报的数加1。
若一个小朋友报的数为k的倍数或其末位数（即数的个位）为k，则该小朋友被淘汰出局，
不再参加以后的报数。当游戏中只剩下一个小朋友时，该小朋友获胜。
　　例如，当n=5, k=2时：
　　1号小朋友报数1；
　　2号小朋友报数2淘汰；
　　3号小朋友报数3；
　　4号小朋友报数4淘汰；
　　5号小朋友报数5；
　　1号小朋友报数6淘汰；
　　3号小朋友报数7；
　　5号小朋友报数8淘汰；
　　3号小朋友获胜。

样例输入：
5 2
样例输出：
3
样例输入：
7 3
样例输出：
4

数据规模和约定：
对于所有评测用例，1 ≤ n ≤ 1000，1 ≤ k ≤ 9。
```

### 代码部分

```c++
#include <iostream>
#include <algorithm>
#include <queue>
using namespace std;

int main()
{
    int n,k;
    cin>>n>>k;
    queue<int> t;
    for(int i=1;i<=n;i++){
        t.push(i);
    }
    int index=0;
    while(t.size()>1){
        index++;
        int f=t.front();
        t.pop();
        if(index%k==0||index%10==k){
            continue;
        }else{
            t.push(f);
        }
    }
    cout<<t.front()<<endl;
}


```


### 代码感悟
这个ccf题就是约瑟夫问题，就是环状数组问题，只要用队列模拟出环状数组即可，貌似oj上做过(=ﾟωﾟ)ﾉ

4k高清水墨画壁纸(灬°ω°灬) 

![](http://or4d8nhvk.bkt.clouddn.com/18-8-5/74358810.jpg)

《道德经》经典语录ヾ(ｏ･ω･)ﾉ

> 大道废，有仁义。  
智慧出，有大伪。  
六亲不和，有孝慈。  
国家昏乱，有忠臣。  


