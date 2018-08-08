---
layout: post
title:  "刽子手游戏（Hangman Judge UVA489)"
date:   2018-08-7 12:59:49 +0800
categories: C-program-language
tags: C-program-language
img: http://or4d8nhvk.bkt.clouddn.com/18-8-8/32972167.jpg
author: DND
---

本题我用到了multiple容器，以及对它的erase（删除）操作，整体不难(｀・ω・´)

找不到配图了，，，¯\_(ツ)_/¯本来想画一个，，但是，，，你懂得(￣∠￣)ﾉ

* 
{:toc}

## 算法

### 题目描述
```
游戏规则，计算机想一个单词让你猜，你每次可以猜一个字母，如果单词里有那个字母，
所有该字母都会显示出来，如果没有那个字母
则计算机会在一副“刽子手”画上填一笔，这幅画一共需要7笔就能完成，
因此你最多只能错6次。注意猜一个已经猜过的字母也算错。
在本题中，你的任务是编写一个“裁判”程序，输入单词和玩家的猜测，
判断玩家赢了，（You win.）、输了（You lose.）、还是放弃了（You chickened out.)
每组包含3行，第一行是游戏编号（-1为输入结束标记），第2行是计算机想的单词，
第3行是玩家的猜测。后两行保证只含小写字母。

样例输入：
1
cheese
chese
2
cheese
abcdefg
3
cheese
abcdefgij
-1

样例输出：
Round 1
You win.
Round 2
You chickened out.
Round 3 
You lose. 

```

### 代码部分

```c++
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <cstring>
#include <string.h>
#include <algorithm>
#include <set>
#define MAX_SIZE 1000
using namespace std;
char arr[MAX_SIZE];
char tem_arr[MAX_SIZE];
int main()
{
    multiset<char> setstring;
    int t,n=0;
    while(scanf("%d",&t)!=EOF&&t!=-1){
        memset(arr,'\0',sizeof(arr));
        memset(tem_arr,'\0',sizeof(tem_arr));
        setstring.clear();
        n++;
        scanf("%s",arr);
        for(int i=0;i<strlen(arr);i++){
            setstring.insert(arr[i]);
        }
        int flag=0;
        scanf("%s",tem_arr);
        int tem_length=strlen(tem_arr);
        for(int i=0;i<tem_length;i++){
            bool boolflag=setstring.erase(tem_arr[i]);
            if(!boolflag){
                flag++;
            }
        }
        if(flag<=6&&setstring.size()>0){
            cout<<"Round "<<n<<endl;
            cout<<"You chickened out."<<endl;
        }
        if(setstring.size()==0&&flag<=6){
            cout<<"Round "<<n<<endl;
            cout<<"You win."<<endl;
        }
        if(setstring.size()>0&&flag>6){
            cout<<"Round "<<n<<endl;
            cout<<"You lose."<<endl;
        }
    }
}

```


### 代码感悟
大致复习了一遍stl，还好٩(๑❛ᴗ❛๑)۶

4k冰河时代5壁纸(￣▽￣)~*ヽ(。_°)ノ

![](http://or4d8nhvk.bkt.clouddn.com/18-8-8/24797342.jpg)

《道德经》一小节(˘•ω•˘)

> 天下莫柔弱于水，  
而攻坚强者莫之能胜，  
以其无以易之。  
弱之胜强，  
柔之胜刚，  
天下莫不知，  
莫能行。  
是以圣人云：  
“受国之垢，  
是谓社稷主；  
受国不祥，  
是为天下王。”  
正言若反。  


