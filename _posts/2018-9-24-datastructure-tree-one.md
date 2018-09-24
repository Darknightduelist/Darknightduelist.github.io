---
layout: post
title:  "数据结构"
date:   2018-09-24 12:59:49 +0800
categories: Datastructure
tags: Datastructure
img: http://or4d8nhvk.bkt.clouddn.com/18-9-24/42188283.jpg
author: DND
---

又将近一个月没更新博客了(｀・ω・´)，今天来聊聊树的同构。(pta上的一道题，重新来做一下)

* 
{:toc}

## 算法

### 题目描述
```
给定两棵树T1和T2。如果T1可以通过若干次左右孩子互换就变成T2，则我们称两棵树是“同构”的。例如图1给出的两棵树就是同构的，因为我们把其中一棵树的结点A、B、G的左右孩子互换后，就得到另外一棵树。而图2就不是同构的。
```
![](http://or4d8nhvk.bkt.clouddn.com/18-9-24/41626591.jpg)   图1

![](http://or4d8nhvk.bkt.clouddn.com/18-9-24/25575104.jpg)   图2

```
现给定两棵树，请你判断它们是否是同构的。
输入格式:
输入给出2棵二叉树树的信息。对于每棵树，首先在一行中给出一个非负整数N (≤10)，即该树的结点数（此时假设结点从0到N−1编号）；随后N行，第i行对应编号第i个结点，给出该结点中存储的1个英文大写字母、其左孩子结点的编号、右孩子结点的编号。如果孩子结点为空，则在相应位置上给出“-”。给出的数据间用一个空格分隔。注意：题目保证每个结点中存储的字母是不同的。

输出格式:
如果两棵树是同构的，输出“Yes”，否则输出“No”。

输入样例1（对应图1）：
8
A 1 2
B 3 4
C 5 -
D - -
E 6 -
G 7 -
F - -
H - -
8
G - 4
B 7 6
F - -
A 5 1
H - -
C 0 -
D - -
E 2 -

输出样例1:
Yes

输入样例2（对应图2）：
8
B 5 7
F - -
A 0 3
C 6 -
H - -
D - -
G 4 -
E 1 -
8
D 6 -
B 5 -
E - -
H - -
C 0 2
G - 3
F - -
A 1 4

输出样例2:
No
```
### 代码部分

```c++
#include <stdio.h>
#define OK 1
#define ERROR 0
#define MaxTree 10
#define Null -1

typedef int Status;/* Status是函数的类型,其值是函数结果状态代码，如OK等 */
typedef char ElementType;/* ElemType类型根据实际情况而定，这里假设为char */

typedef struct TreeNode
{
    ElementType data;
    int left;
    int right;
} Tree;

Tree T1[MaxTree], T2[MaxTree];

int BulidTree(Tree T[])
{
    int N, check[MaxTree], root = Null;    //root = Null 空树则返回Null
    char cl, cr;        //左右孩子序号
    scanf("%d\n",&N);
    if(N) {
        for(int i = 0; i < N; i++)
            check[i] = 0;
        for(int i = 0; i < N; i++) {
            scanf("%c %c %c\n",&T[i].data, &cl, &cr);
            //找root
            if(cl != '-') {
                T[i].left = cl - '0';
                check[T[i].left] = 1;    //不是根节点
            }else {
                T[i].left = Null;
            }
            if(cr != '-') {
                T[i].right = cr - '0';
                check[T[i].right] = 1;    //不是根节点
            }else {
                T[i].right = Null;
            }
        }

        for(int i = 0; i < N; i++)        //check[]=0的为根节点
            if(!check[i]) {
                root = i;
                break;
            }
    }
    return root;
}
Status Isomprphic(int root1, int root2)
{
    if( (root1 == Null) && (root2 == Null))//都是空 ，同构
        return OK;
    if( (root1 == Null)&&(root2 != Null) || (root1 != Null)&&(root2 == Null))//其中一个为空，不同构
        return ERROR;
    if(T1[root1].data != T2[root2].data)     //根数据不同,不同构
        return ERROR;
    ///*******************************************************************************
    if( (T1[root1].left == Null) && (T2[root2].left == Null) ) //若左子树都为空，则判断右子树（包含了两种情况）
        return Isomprphic(T1[root1].right, T2[root2].right);

    if((T1[root1].left != Null) && (T2[root2].left != Null) &&
        ( T1[T1[root1].left].data == T2[T2[root2].left].data) )//两树左子树皆不空，判断值相等不相等
        return (Isomprphic(T1[root1].left, T2[root2].left) &&  //判断其子树
                Isomprphic(T1[root1].right, T2[root2].right) );
    else //两树左子树有一个空  或者  皆不空但值不等
        return (Isomprphic(T1[root1].left, T2[root2].right) &&  //交换左右子树判断
                Isomprphic(T1[root1].right, T2[root2].left) );

}

int main()
{
    int root1, root2;
    root1 = BulidTree(T1);
    root2 = BulidTree(T2);
    if(Isomprphic(root1, root2) )
        printf("Yes\n");
    else
        printf("No\n");
    return 0;
}

```


### 代码感悟
主要函数是Isomprphic，前三个if是终止条件，是递归的出口。注意每一种情况，不要漏。

