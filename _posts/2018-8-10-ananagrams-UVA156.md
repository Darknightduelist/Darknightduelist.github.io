---
layout: post
title:  "反片语（Ananagrams UVA 156）"
date:   2018-08-10 12:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-12/76518787.jpg
author: DND
---

一道例题，，容器的练习(= =) 

* 
{:toc}

## 算法

### 题目描述
```
输入一些单词，找出所有满足如下条件的单词：该单词不能通过字母重排，得到输入文本中的另外一个单词。在判断是否满足条件时，字母不区分大小写，但在输出时应保留输入的大小写，按字典序进行排列（所有大写字母在小写字母的前面）。

样例输入：
ladder came tape soon leader acme RIDE lone Dreis peat

ScAlE orb eye Rides dealer NotE derail LaCeS drIed

noel dire Disk mace Rob dries

样例输出：
Disk

NotE

derail

drIed

eye

ladder

soon
```

### 代码部分

```c++
#include <iostream>
#include <algorithm>
#include <string>
#include <vector>
#include <cctype>
#include <map>
#include <stdio.h>
#include <stdlib.h>
using namespace std;

map<string,int> cnt;
vector<string> words;

string repr(const string &s){
   string ans=s;
   for(int i=0;i<ans.length();i++){
     ans[i]=tolower(ans[i]);
   }
   sort(ans.begin(),ans.end());
   return ans;
}


int main()
{
    int n=0;
    string s;
    while(cin>>s){
        if(s=="#"){
            break;
        }
        words.push_back(s);
        string r=repr(s);
        /*algorithm头文件定义了一个count的函数，
        其功能类似于find。
        这个函数使用一对迭代器和一个值做参数，
        返回这个值出现次数的统计结果。 */
        if(!cnt.count(r)){
            cnt[r]=0;
        }
        cnt[r]++;
    }
    vector<string> ans;
    for(int i=0;i<words.size();i++){
        if(cnt[repr(words[i])]==1){
            ans.push_back(words[i]);
        }
    }
    sort(ans.begin(),ans.end());
    for(int i=0;i<ans.size();i++){
        cout<<ans[i]<<"\n";
    }


    return 0;
}


```


### 代码感悟
count函数是algorithm头文件定的，其功能类似于find。这个函数使用一对迭代器和一个值做参数，
返回这个值出现次数的统计结果。（ps：接下来我要试验一下视频可不可被Jekyll博客模板解析o(￣▽￣)ｄ ，以下视频和博客毫无关系，emmmmmm..........）

<iframe width="560" height="315" src="http://www.aipai.com/c16/PzkoKSUhLS1qJWQsLw.html" frameborder="0" allowfullscreen></iframe>

[flash=880,495]http://www.aipai.com/c16/PzkoKSUhLS1qJWQsLw/playerOut.swf[/flash]

<embed width="880" height="495" src="http://www.aipai.com/c16/PzkoKSUhLS1qJWQsLw/playerOut.swf" quality="high" align="middle" allowScriptAccess="always" type="application/x-shockwave-flash"/>

5k壁纸（：·）

![](http://or4d8nhvk.bkt.clouddn.com/18-8-12/59122841.jpg)

日常《道德经》(∩_∩)

> 知人者智，  
自知者明，  
胜人者有力，  
自胜者强。  
知足者富，  
强行者有志。  
不失其所者久。  
死而不亡者寿。  