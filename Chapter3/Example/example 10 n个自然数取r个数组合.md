## 例10
找出n个自然数(1,2,3,...,n)中取r个数的组合，例如n=5，r=3时，所有组合为：  
5 4 3  
5 4 2  
5 4 1  
5 3 2  
5 3 1  
5 2 1  
4 3 2  
4 3 1  
4 2 1  
3 2 1  
total=10
### 算法分析
递归算法找出大规模问题与小规模问题之间的关系  
分析以上数据，组合数规律如下：
+ 固定第一个数5，其后就是求解n=4，r=2的组合数，共6个组合。
+ 固定第一个数4，其后就是求解n=3，r=2的组合数，共3个组合。
+ 固定第一个数3，其后就是求解n=2，r=2的组合数，共6个组合。

所以递归关系为
+ n个数中r个数的组合递归推到“n-1个数中r-1个数有组合，n-2个数中r-1个数有组合，...，r-1个数中r-1个数有组合”，共有n-r+1次递归。
+ 递归的停止条件是r=1。

### 算法设计
```c
#include<stdio.h>
void fac(int n, int r);
int a[10] = { 0 };
int main()
{
    int i, n, r;
    printf("input n,r: ");
    scanf_s("%d %d", &n, &r);
    if (r > n)
        printf("Input n,r error!");
    else
    {
        a[0] = r;
        fac(n, r);
    }
    return 0;
}
void fac(int n, int r)
{
    int i, j;
    for (i = n;i >= r;i--)
    {
        a[r] = i;
        if (r>1)
            fac(i - 1, r - 1);
        else
        {
            for (j = a[0];j > 0;j--)
                printf("%d ", a[j]);
            printf("\n");
        }
    }
}
```


