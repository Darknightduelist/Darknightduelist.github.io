---
layout: post
title:  "安迪的第一个字典（dictionary UVA10815）"
date:   2018-08-9 12:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-11/42514117.jpg
author: DND
---

书上的例题，，只能说思路清奇(ΩДΩ)

* 
{:toc}

## 算法

### 题目描述
```
输入一个文本，找出所有不同的单词（连续的字母序列），
按字典序从小到大输出。单词不区分大小写。

样例输入：
Adventures in Disneyland

Two blondes were going to Disneyland when they came to a fork in the
road. The sign read: "Disneyland Left."

So they went home.

样例输出：
a
adventures
blondes
came
disneyland
fork
going
home
in
left
read
road
sign
so
the
they
to
two
went
were
when
```

### 代码部分

```c++
#include<iostream>
#include<set>
#include<string>
#include<sstream>
using namespace std;
set<string> dict;
int main()
{
    string s,buf;
    set<string>::iterator it;
    while(cin>>s)
    {
        for(int i=0; i<s.length(); i++)
        {
            if(isalpha(s[i]))//判断是不是字母，如果参数是字母字符，函数返回非零值，否则返回零值。
            {
                s[i]=tolower(s[i]);
            }
            else
            {
                s[i]=' ';
            }
        }
        stringstream ss(s);//定义了一个字符串流，并用一个字符串初始化
        while(ss>>buf)
        {
            dict.insert(buf);
        }
        
    }
    for(it=dict.begin(); it!=dict.end(); it++)
    {
        cout<<*it<<endl;
    }
    return 0;
}

```


### 代码感悟
stringstream是字符串流，找了好多版本的说法，觉得这个最靠谱（[链接](https://zhidao.baidu.com/question/142611736.html)）(<ゝω・)☆,还有知道isalpha函数是干什么用的就可以了

4kLOL壁纸，（￣︶￣）↗

![](http://or4d8nhvk.bkt.clouddn.com/18-8-11/49072338.jpg)

日常《道德经》ヾ(ｏ･ω･)ﾉ

> 企者不立，  
跨者不行。  
自见者不明。  
自是者不彰。  
自伐者无功。  
自矜者不长。  
其在道也，  
曰：“余食赘行。”  
物或恶之，  
故有道者不处。  
