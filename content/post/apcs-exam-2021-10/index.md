---
title: AP CS Exam Notes 2021-10-28
description: 考试笔记
date: 2021-10-27
slug: APCS Notes
image: head.jpg
categories:
    - APCS
tags:
    - 笔记
    - APCS
---

## 第一题修改代码

很简单的 10进制转2进制，用的也是常规方法

附上考试时调出来的代码：

```java
import java.util.*;

public class base
{
    public static void main(String[] args)
    {
    	int n,a,count0=0, count1=0;
    	String s="";
    	Scanner sc=new Scanner(System.in);
    	System.out.println("number");
    	n=sc.nextInt();
    	while(n>0){
    		a=n%2;
    		if(a==1){
    				count1++;
    		}else{
    			count0++;
    		}
    		n=n/2;
    		s=a+" "+s;
    	}
    	System.out.println("Bin number is "+s);
    	System.out.println("0count "+count0);
    	System.out.println("1count "+count1);
    }
}
```

有些人的卷子上写的是 

```
count1--;
```

需要改成

```
count1++;
```

另外在进制转时需要倒序排列数字，所以需要改成：

```java
s=a+" "+s;
```

同时将语句将else里移出来，这题就调好了。

## 第二部分 选择题

### Question 1

What are the values of a and b after the for loop finishes?

```java
int a = 10;
 int b = 3;
 int t = 0;
 for (int i = 1; i < 4; i++)
 {
 t = a;
 a = i + b;
 b = t - i;
 }
```

(A) a = 5 and b = -2
(B) a = 6 and b = 7
(C) a = 6 and b = 3
(D) a = 12 and b = 1
(E) a = 5 and b = 8

简单推算即可，正确答案是E

### Question 2

Consider the following code segment:

```java
for(int i = 0; i <= 3; i++)
{
 for(int j = 1; j <= 5; j+=2)
 {
 System.out.println("*");
 }
}

```

How many times will a ‘*’ be printed?
(A) 3
(B) 6
(C) 9
(D) 12
(E) 15

此题正解为 $3 \times 4=12$。

但是有些人的卷子(本题第一行代码)上应该看到的是:

```java
for(int i = 0; i <= 3; j++)
```

所以应该是存在语法错误，所以无法输出任何结果，故应填 No Answer!

### Question 3

Consider the following code segment.

```java
for (int k = 0; k < 20; k = k + 1)
{
 if (k % 2 == 1)
 System.out.print((k + 1) + " ");
}
```

What is printed as a result of executing the code segment?
(A) 1 3 5 7 9 11 13 15 17 19
(B) 0 2 4 6 8 10 12 14 16 18
(C) 2 4 6 8 10 12 14 16 18 20
(D) 3 6 9 12 15 18
(E) 0 2 4 6 8 10 13 14 16 18 20

此题通过if判断的k值应该为0-19之间的所有奇数，但是应为输出时输出的是

```java
System.out.print((k+1)+" ");
```

所以应为 2-20的所有奇数

故选B

### Question 4

Which of the following would be the correct result from the following expression?

```
123(Decimal) - 12(Octal) + 101(Binary) + D(Hex)
```

(A) 130 (Decimal)
(B) 133 (Decimal)
(C) 151 (Decimal)
(D) 132 (Decimal)
(E) 136 (Decimal)

此题依次转换为10进制即可

$123_{(10)}$ 无需转化，$12_{(8)}=1\times8^1+2=10_{(10)}$，$101_{(2)}=5_{(10)}$，$D_{(16)}=13_{(10)}$

最终转化成

$$123-10+5+13 = 131 $$

故无答案。

### Question 5

Consider the following code segment:

```java
 int p = 5;
 int q = 2;
 int sum = 0;
 while (p <= 8)
 {
 sum += p % q;
 p++;
 q++;
 }
```

What is the value of sum after the code is executed?
(A) 1
(B) 0
(C) 13
(D) 7
(E) 4

这个也是比较简单的题，直接trace即可

最终答案`sum = 7`,故选D

### Question 6

Consider the following code segment:

```java
 // int i = a random number such that 1 <= i <= n;
 for (int a = 2; a <= i; a++)
 for (int b = 1; b < i; b++)
 System.out.println("*");

```

What is the minimum number of times that * will be printed?
(A) 0
(B) 1
(C) 2
(D) n - 1
(E) n - 2

此题定义`i`的取值范围 `1<=i<=n` 所以取`i=1`的时候，循环不执行，故输出0，应选A。

### Question 7 

```
Which of the following code will produce the following output?

 1
 22
 333
 4444
```

选项1：

```java
for (int i = 1; i < 5; i++) {
 for (int j = i; j > 0; j--) {
 System.out.print(i+1);
 }
 System.out.println();
 }
```

运行结果:

```
2
33
444
5555
```

选项2:

```java
for (int i = 0; i < 5; i++) {
 for (int j = 0; j < i; j++) {
 System.out.print(i);
 }
 System.out.println();
 }

```

运行结果: 

```

1
22
333
4444
```

答案正确。

其他代码的运行结果就不进行列举了，鉴于选项顺序可能会有出入，这里列出所有错误的代码:

```java
for (int i = 1; i < 5; i++) {
 for (int j = i; j > 0; j--) {
 System.out.print(i+1);
 }
 System.out.println();
 }

for (int i = 1; i <= 5; i++) {
 for (int j = i; j > 0; j--) {
 System.out.print(i);
 }
 System.out.println();
 }
 
 for (int i = 1; i < 6; i++) {
 for (int j = 0; j < i; j++) {
 System.out.println(i);
 }
 }
 
 for (int i = 0; i < 5; i++) {
 for (int j = 0; j < i; j++) {
 System.out.print(i+1);
 }
 System.out.println();
 }
```

### Question 8

When is the following Boolean expression true (a and b are integers)?

```java
(a < b) && !(b > a)
```

(A) Always true
(B) Never true
(C) a = b
(D) a < b
(E) a > b

考虑两个情况, a<b 为 true和 a<b为false

根据 `&&`运算规则，有一个false就结果为false，所以never true

### Question 9

Which of the following code segments is equivalent to the code below?

```java
if (x >= 1) x = x * 3;
 if (x > 3) x = 0;
```

(A) x = 0;
(B) if (x > 1) x = 0;
(C) if (x > 3) x = 0;
(D) if (x >=1) x = 0;
(E) none of the above

简单的不等式和代数转换之后可以得出，答案应为B

## 总结

这是本人目前根据psl上的题目得出的答案推算，最终结果请参考老师打分

如有疑问请在下方评论。