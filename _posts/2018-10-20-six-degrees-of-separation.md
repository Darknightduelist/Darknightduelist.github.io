---
layout: post
title:  "Six degrees of separation"
date:   2018-10-20 12:59:49 +0800
categories: Datastructure
tags: Datastructure
img: http://pgsck8okb.bkt.clouddn.com/1.jpg
author: DND
---

BFS的稍微改动(￣▽￣)／(～￣▽￣)～ ，

* 
{:toc}

## 算法

### 题目描述
```
“六度空间”理论又称作“六度分隔（Six Degrees of Separation）”理论。这个理论可以通俗地阐述为：“你和任何一个陌生人之间所间隔的人不会超过六个，也就是说，最多通过五个人你就能够认识任何一个陌生人。”如图所示。
```

![](http://pgsck8okb.bkt.clouddn.com/1.jpg)
```
“六度空间”理论虽然得到广泛的认同，并且正在得到越来越多的应用。但是数十年来，试图验证这个理论始终是许多社会学家努力追求的目标。然而由于历史的原因，这样的研究具有太大的局限性和困难。随着当代人的联络主要依赖于电话、短信、微信以及因特网上即时通信等工具，能够体现社交网络关系的一手数据已经逐渐使得“六度空间”理论的验证成为可能。

假如给你一个社交网络图，请你对每个节点计算符合“六度空间”理论的结点占结点总数的百分比。

输入格式:
输入第1行给出两个正整数，分别表示社交网络图的结点数N（1<N≤10
​4
​​ ，表示人数）、边数M（≤33×N，表示社交关系数）。随后的M行对应M条边，每行给出一对正整数，分别是该条边直接连通的两个结点的编号（节点从1到N编号）。

输出格式:
对每个结点输出与该结点距离不超过6的结点数占结点总数的百分比，精确到小数点后2位。每个结节点输出一行，格式为“结点编号:（空格）百分比%”。

输入样例:
10 9
1 2
2 3
3 4
4 5
5 6
6 7
7 8
8 9
9 10
输出样例:
1: 70.00%
2: 80.00%
3: 90.00%
4: 100.00%
5: 100.00%
6: 100.00%
7: 100.00%
8: 90.00%
9: 80.00%
10: 70.00%
```
### 代码部分

```c++
#include <iostream>
#include <cstdio>
#include <cstring>
#include <stack>
#include <queue>
#define MAX_SIZE 10000+1
using namespace std;
int n;
queue<int> que;
int Graph[MAX_SIZE][MAX_SIZE]= {0};
int Vis[MAX_SIZE]= {0};
int flag_count;
int level;
int BFS(int x)
{
    memset(Vis,0,sizeof(Vis));
    flag_count=1;
    level=0;
    int last=x;
    int tail;
    while(que.size()) que.pop();
    Vis[x]=1;
    que.push(x);
    while(que.size()>0)
    {
        int y=que.front();
        que.pop();
        for(int i=1; i<=n; i++)
        {
            if(!Vis[i]&&Graph[y][i])
            {
                Vis[i]=1;
                que.push(i);
                tail=i;
                ++flag_count;
            }
        }
        if(y==last)
        {
            ++level;
            last=tail;
        }
        if(level==6)
        {
            break;
        }
    }
    return flag_count;
}

double rate(int fl,int poi)
{
    return (fl*1.0)/poi;
}

int main()
{
    int point;
    int verge;
    int x,y;
    memset(Vis,0,sizeof(Vis));
    cin>>point>>verge;
    n=point;
    for(int i=0; i<verge; i++)
    {
        cin>>x>>y;
        Graph[x][y]=Graph[y][x]=1;
    }
    for(int j=1; j<=point; j++)
    {
        int f=BFS(j);
        double end_number=rate(f,point);
        printf("%d: %.2lf",j,end_number*100);
        printf("%%\n");//输出百分号
    }
    return 0;
}
```


### 代码感悟
建立队列存储节点元素是关键，和图的非递归DFS有相同之处。

