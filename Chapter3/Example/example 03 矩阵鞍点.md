## 例3 
求一个m*n矩阵的鞍点，即在行上最小而在列上最大的点

### 算法设计
```c
#include<stdio.h>
#define m 4
#define n 4
void readMtr(int a[][n], int x);
void printfMtr(int a[][n], int x);
int main()
{
    int a[m][n];
    int i, j, k, min, minj;
    readMtr(a, m);
    printfMtr(a, m);
    for (i = 0;i < m;i++)
    {
        min = a[i][0];
        minj = 0;
        for (j = 0;j < n;j++)
        {
            if (a[i][j] < min)
            {
                min = a[i][j];
                minj = j;
            }
        }
        for (k = 0;k < m;k++)
        {
            if (a[k][minj] > min)
                break;
        }
        if (k < m) continue;
        printf("The result is a[%d][%d]\n", i, minj);
        return 0;
    }
    printf("No soution!\n");
    return 0;
}
void readMtr(int a[][n], int x)
{
    int i, j;
    printf("输入%d*%d矩阵: ", x, n);
    for (i = 0;i < x;i++)
        for (j = 0;j < n;j++)
            scanf_s("%d", &a[i][j]);
}
void printfMtr(int a[][n], int x)
{
    int i, j;
    printf("输出%d*%d矩阵: \n", x, n);
    for (i = 0;i < x;i++) 
    {
        for (j = 0;j < n;j++)
            printf("%3d ", a[i][j]);
        printf("\n");
    }
}
```


