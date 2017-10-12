### 例15
一个顾客买了价值x元的商品（不考虑角，分），并将y元的钱交给售货员。编写算法：在各种币值的钱都很充分的情况下，使售货员能用张数最少的钱币找给顾客。
### 问题分析
无论买商品的价值x是多少，找给他的钱最多需要以下7种币值，即100，50，20，10，5，2，1.
### 算法设计1
```c
#include<stdio.h>
int main()
{
    int i, x, y, z, n, a[7] = { 0 }, rmb[7] = { 100,50,20,10,5,2,1 };
    printf("input the value of x, y(x <= y):");
    scanf_s("%d %d", &x, &y);
    n = y - x;
    for (i = 0;i < 7;i++)
    {
        if (n == 0) break;
        else if (n >= rmb[i])
        {
            a[i] = n / rmb[i];          //数组a保存各个币值的数目
            n = n - a[i] * rmb[i];
        }
    }
    printf("%d - %d = %d :\n", y, x, y-x);
    for (i = 0;i < 7;i++)
        printf("%3d --- %2d\n", rmb[i], a[i]);
    printf("\n");
    return 0;
}
```
