## 例6
整数的分划问题。对于一个正整数n的分划，就是把n表示成一系列正整数之和的表达式。注意，分划与顺序无关，例如6=5+1和6=1+5被认为是同一种分划。另外这个整数n本身也算一种分划。  

例如，对于正整数n，它可以分划为：  
6  
5+1  
4+2&emsp;&emsp;&emsp;&emsp;4+1+1  
3+3&emsp;&emsp;&emsp;&emsp;3+2+1&emsp;&emsp;&emsp; 3+1+1+1  
2+2+2&emsp;&emsp;&emsp;2+2+1+1&emsp;&emsp;2+1+1+1  
1+1+1+1+1+1  
对于给定正整数n,要求编写算法计算出其分划的数目P(n)（思考：写出其所有分划）。

### 数学模型
定义一个函数Q(n,m)，表示整数n的“任何加数都不超过m”的分划的数目，n的所有分划数目P(n)就应该表示为Q(n,n)。  

一般的Q(n,m)有以下递归关系
+ Q(n,n)=1+Q(n,n-1)，等式右边的“1”表示n只包含一个被加数等于n本身的分划；则其余部分表示n的所有其它分划，即最大加数m<=n-1的分划。
+ Q(n,m)=Q(n,m-1)+Q(n-m,m)&emsp;&emsp;(m<n)，等式右边的第一部分表示被加数中不包含m的分划的数目；第二部分表示被加数中包含（注意不是小于）m的分划的数目，因为如果确定了一个分划的被加数中包含m，则剩下的部分就是对n-m进行不超过m的分划。

由此，找到了大规模问题与小规模问题的递归关系，下面是递归的终止条件：
+ Q(n,1)=1，表示当最大的被加数是１时，该整数n只有一种分划，即n个１相加。
+ Q(1,m)=1，表示整数n=1只有一个分划，不管最大被加数的上限ｍ是多大。

考虑到n的分划不可能包含大于n的被加数ｍ，因为，若n<m,则Q(n,m)是无意义的。此时令Q(n,m)=Q(n,n)；同样当n<1或m<1时，Q(n,m)也是无意义的。
### 算法设计
```c
#include<stdio.h>
int Divinteger(int n, int m);
int main()
{
    int n;
    printf("输入正整数n: ");
    scanf_s("%d", &n);
    if (n < 1)
        printf("输入参数错误！\n");
    printf("\n正整数n的分划数目为%d\n",Divinteger(n, n));
    return 0;
}
int Divinteger(int n, int m)
{
    if (n == 1 || m == 1)
        return 1;
    else if (n < m)
        return Divinteger(n, n);
    else if (n == m)
        return 1 + Divinteger(n, n - 1);
    else
        return Divinteger(n, m - 1) + Divinteger(n - m, m);
}
```


