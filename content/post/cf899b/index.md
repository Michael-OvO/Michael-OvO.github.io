---
title: CF899b
description: 模拟
date: 2021-10-27
slug: cf899b
image: cf899b.jpg
categories:
    - C++题解
---

# CF899B Months and Years

[原题传送门](https://codeforces.com/problemset/problem/899/B)

[洛谷传送门](https://www.luogu.com.cn/problem/CF899B)

这可能是目前最暴力的一篇题解了。。

题目其实很简单，给出几个连续月份的天数，判断是否合法

~~好端端的一道模拟题就这么被打表暴力过了~~

不过确实，与其说写一堆复杂的判断和模拟，打表所需的代码量少之又少。

## 思路
首先自己创建好连续几年（需要包含平年和闰年的数据，因为题目中的月份数最多会达到 $24$）每个月天数的数据。

```cpp
"31 28 31 30 31 30 31 31 30 31 30 31 31 28 31 30 31 30 31 31 30 31 30 31 31 29 31 30 31 30 31 31 30 31 30 31 31 28 31 30 31 30 31 31 30 31 30 31 31 28 31 30 31 30 31 31 30 31 30 31 "
```
随后，我们只需要原封不动的读入字符串，再用 `find()` 函数直接判断是否为我们提前创建好的字符串中的一个子串即可。

其实题目第一行读入的整数并没啥用。

第二行直接全行读入字符串。

完全不需要做任何的处理，直接比对，返回输出。

唯一需要注意的是，使用 `getline()` 的时候需要格外小心数据输入是否有存在回车的情况，需要加上 `cin.ignore()`。

## 前方高能，极其暴力代码
```cpp
#include<bits/stdc++.h>

using namespace std;
string b;
int main()
{
   ios::sync_with_stdio(0);
   cin.tie(0);
   int num;
   cin>>num;
   cin.ignore();
   getline(cin,b);
   string month="31 28 31 30 31 30 31 31 30 31 30 31 31 28 31 30 31 30 31 31 30 31 30 31 31 29 31 30 31 30 31 31 30 31 30 31 31 28 31 30 31 30 31 31 30 31 30 31 31 28 31 30 31 30 31 31 30 31 30 31 ";
    if(month.find(b)!=string::npos){
        cout<<"Yes"<<endl;
    }else{
        cout<<"No"<<endl;
    }
}

```


