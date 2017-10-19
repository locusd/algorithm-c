### 例19
编程求当n<=100时，n!的准确值。
### 算法设计1
```c
#include<stdio.h>
#include<math.h>
int main()
{
    int i, j, m, n;
    long a[256], b, d;
    double s = 0;
    printf("输入阶乘n值: ");
    scanf_s("%d", &n);
    for (i = 1;i <= n;i++)
    {
        s += log10(i);          //求n!结果的位数
    }
    printf("n!的位数为： %d", (int)s + 1);
    m = ((int)s + 1) / 6 + 1;
    printf("\n定义长整型数组a中每个元素存储6位结果数字。"
           "\n则数组需%d个元素来存储阶乘结果。", m);

    a[1] = 1;
    for (i = 2;i <= n;i++)
        a[i] = 0;
    d = 0;
    for (i = 2;i <= n;i++) {
        for (j = 1;j <= m;j++)
        {
            b = a[j] * i + d;       //b存储计算的中间结果
            a[j] = b % 1000000;     //d存储超过6位数后的进位
            d = b / 1000000;
        }
        if (d != 0)
        {
            a[j] = d;
        }
    }
    printf("\n%d != %ld ", n, a[m]);
    for (i = m - 1;i >= 1;i--)
    {
        if (a[i] > 99999)
            printf("%ld ", a[i]);
        else if (a[i] > 9999)
            printf("0%ld ", a[i]);
        else if (a[i] > 999)
            printf("00%ld ", a[i]);
        else if (a[i] > 99)
            printf("000%ld ", a[i]);
        else if (a[i] > 9)
            printf("0000%ld ", a[i]);
        else if (a[i] > 0)
            printf("00000%ld ", a[i]);
        else
            printf("000000 ");
    }
    printf("\n");
    return 0;
}
```