---
layout: post
title:  "Intransitive DFS"
date:   2018-10-17 12:59:49 +0800
categories: Datastructure
tags: Datastructure
img: http://pgscy2alk.bkt.clouddn.com/two.jpg
author: DND
---

DFS的非递归实现，有助于更好地了解DFS的递归，以及递归过程。(￣▽￣)~*

* 
{:toc}

## 算法

### 题目描述
```
实现图的非递归DFS
```
### 代码部分

```c++
#include <iostream>
#include <cstdio>
#include <cstring>
#include <stack>
#include <queue>
#define MAX_SIZE 12
using namespace std;

stack<int> sk;
queue<int> que;
int n=MAX_SIZE;
int Graph[MAX_SIZE][MAX_SIZE]={
    {-1,1,1,0,0,0,0,0,0,0,0,0},
	{1,-1,1,0,1,1,0,0,0,0,0,0},
	{1,1,-1,1,0,0,0,0,0,0,0,0},
	{0,0,1,-1,1,0,0,0,0,0,1,1},
	{0,1,0,1,-1,0,0,0,0,0,0,0},
	{0,1,0,0,0,-1,0,0,0,0,1,0},
	{0,0,0,0,0,0,-1,1,1,1,0,0},
	{0,0,0,0,0,0,1,-1,0,0,0,0},
	{0,0,0,0,0,0,1,0,-1,1,1,0},
	{0,0,0,0,0,0,1,0,1,-1,0,1},
	{0,0,0,1,0,1,0,0,1,0,-1,0},
	{0,0,0,1,0,0,0,0,0,1,0,-1},
};
int Vis[MAX_SIZE];

void DFS(int x){
    if(Vis[x]){
        return;
    }
    Vis[x]=1;
    cout<<x<<" ";
    for(int i=0;i<n;i++){
        if(!Vis[i]&&Graph[x][i]==1){
            DFS(i);
        }
    }
}

void BFS(int x){
    if(Vis[x]){
        return;
    }
    Vis[x]=1;
    cout<<x<<" ";
    que.push(x);
    while(que.size()>0){
        int y=que.front();
        que.pop();
        for(int i=0;i<n;i++){
          if(!Vis[i]&&Graph[y][i]){
            Vis[i]=1;
            que.push(i);
            cout<<i<<" ";
          }
        }
    }
}

void Intransitive_DFS(int x){
    int i;
    if(Vis[x]){
        return;
    }
    Vis[x]=1;
    sk.push(x);
    cout<<sk.top()<<" ";
    while(sk.size()>0){
        x=sk.top();
        for(i=0;i<n;i++){
            if(!Vis[i]&&Graph[x][i]){
                sk.push(i);
                Vis[i]=1;
                cout<<sk.top()<<" ";
                break;
            }
        }
        if(i==n){
            sk.pop();
        }
    }
}

int main()
{
    memset(Vis,0,sizeof(Vis));
    cout<<"DFS: ";
    DFS(1);
    cout<<endl;
    memset(Vis,0,sizeof(Vis));
    cout<<"Intransitive_DFS: ";
    Intransitive_DFS(1);
    cout<<endl;
    memset(Vis,0,sizeof(Vis));
    cout<<"BFS: ";
    BFS(1);
    return 0;
}

```


### 代码感悟
建立递归栈是本题的关键，递归栈可以用数组模拟，我采用的是stl模板。

