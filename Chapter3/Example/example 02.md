## 例2 
一个数如果恰好等于它因子之和（包括1，但不包括这个数本身），这个数就被称为“完数”。例如，28的因子为1，2，4，7，14，而28=1+2+4+7+14。因此28是“完数”。编写算法找出1000以内所有完数，并按照下面格式输出因子：28 it's factors are 1,2,4,7,14。

### 算法设计
```c
#include<stdio.h>
int IsPerNum(int i);
int k, a[20];
int main()
{
    int i, j, n = 1000;
    for (i = 2;i <= n;i++)
        if (IsPerNum(i))
        {
            printf("%3d it's factors are %d", i, 1);
            for (j = 0;j < k;j++)
                printf(", %d", a[j]);
            printf("\n");
        }
    return 0;
}
int IsPerNum(int i)
{
    int j, sum;
    sum = 1;
    k = 0;
    for (j = 2;j < i;j++)
    {
        if (i%j == 0)
        {
            sum = sum + j;
            a[k] = j;
            k++;
        }
    }
    if (sum == i) return 1;
    else return 0;
}
```


