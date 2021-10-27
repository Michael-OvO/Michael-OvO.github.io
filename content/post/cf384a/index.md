---
title: CF384A
description: 大模拟
date: 2021-10-27
slug: CF384A
image: cf384a.jpg
categories:
    - C++题解
---

# CF384A

[洛谷传送门](https://www.luogu.com.cn/problem/CF384A)

[原题传送门](https://codeforces.com/problemset/problem/384/A)

本菜鸡的第 $99$ 道橙题，心血来潮写一篇题解。

## 题意

一种棋的规则是：在一个棋盘中，与该棋子相邻的上，下，左，右，$4$ 个格子中不能有棋子出现。

给出一个 $n \times n$ 的棋盘，首先输出在这个棋盘中最多能放多少个棋子，并输出一种最大的可行的摆放方案。

## 解法$1$ 纯暴力模拟

通过画图观察规律。

$$n=2$$

```
C.
.C
```

$$n=3$$

```
C.C
.C.
C.C
```

$$n=4$$
```
C.C.
.C.C
C.C.
.C.C
```
$$n=5$$
```
C.C.C
.C.C.
C.C.C
.C.C.
C.C.C
```
我们发现，当坐标为第偶数行，偶数列时落子，或者在第奇数行，第奇数列落子，得到的一定是最优解。

那么就可以根据这个思路通过创建一个二维字符组模拟棋子摆放的过程。
因为 $n$ 的数据范围很小，所以这样的方法虽然时间复杂度较高，但是也是可行的。

### 第一种解法代码

```cpp
#include<bits/stdc++.h>

using namespace std;

char board[2000][2000];//存储棋盘状态 
int cnt;
int main()
{
   ios::sync_with_stdio(0);
   cin.tie(0);
   int n;
   cin>>n;
   //i代表行,j代表列
   for(int i=1;i<=n;i++){
       for(int j=1;j<=n;j++){
           if((i%2&&j%2)||!(i%2^j%2))board[i][j]='C',cnt++; //判断是否可以落子
           else board[i][j]='.';//否则不下子
       }
   }
   cout<<cnt<<endl;
   for(int i=1;i<=n;i++){
       for(int j=1;j<=n;j++){
           cout<<board[i][j]; //输出棋盘
       }
       cout<<endl;
   }
}

```
## 解法 $2$ 优化暴力

但是刚刚的解法需要先存储，再输出一遍，比较浪费时间，还是有可以优化的空间。

可以直接读入并输出。

首先，给出 $n$ 的时候，就可以直接求出总数了。

分类讨论 $n$ 为奇数和偶数的两种情况：

1. 奇数时，总数为 $(n\times n+1)\div 2$
2. 偶数时，总数为 $n\times n \div 2$

随后就可以根据奇数行和偶数行来进行输出了，大大缩小了时间复杂度。

### 第二种解法代码

```cpp
#include<bits/stdc++.h>

using namespace std;

int main()
{
   ios::sync_with_stdio(0);
   cin.tie(0);
   int n;
   cin>>n;
   if(n%2==0){//如果n为偶数
       cout<<n*n/2<<endl;
       for(int i=1;i<=n;i++){
           if(i%2==1){
               for(int i=1;i<=n/2;i++) cout<<"C.";//奇数行
           }else{
               for(int i=1;i<=n/2;i++) cout<<".C";//偶数行
           }
           cout<<endl;
       }
    }else{//如果n为奇数
       cout<<(n*n+1)/2<<endl;
       for(int i=1;i<=n;i++){
           if(i%2==1){//奇数行
               for(int i=1;i<=n/2;i++) cout<<"C.";
               cout<<"C";
           }else{
               for(int i=1;i<=n/2;i++) cout<<".C";//偶数行
               cout<<".";
           }
           cout<<endl;
       }
   }
}

```


当然，还存在有更优的解，这里因为本人能力有限，就不进行列举了。

~~（数据这么小做别的题它不香吗，干嘛非要优化）~~

码字不易，求点赞




