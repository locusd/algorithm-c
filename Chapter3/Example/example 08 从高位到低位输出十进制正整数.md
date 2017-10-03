## 例8
任给十进制的正整数，请从高位到低位逐位输出各位数字。<br>
(将以下两个算法中10用变量m代替，就可以将输入的十进制数转换为m进制数输出。)
### 算法设计
循环算法
```c
#include<stdio.h>
int main()
{
    int n,i,j,a[20];
    printf("输入n值： ");
    scanf_s("%d", &n);
    printf("从高位到低位逐位输出：");
    for(i=0;n>=10;i++)
    {
        a[i] = n % 10;              //用数组保存结果，再逆向输出
        n /= 10;
    }
    a[i] = n;
    for (j = i;j >= 0;j--)
        printf("%d ", a[j]);
    printf("\n");
    return 0;
}
```
递归算法
```c
#include<stdio.h>
void fac(int n);
int main()
{
    int n;
    printf("输入n值： ");
    scanf_s("%d", &n);
    printf("从高位到低位逐位输出：");  
    fac(n);
    printf("\n");
    return 0;
}
void fac(int n)
{
    if (n < 10)
        printf("%d ", n);
    else
    {
        fac(n / 10);
        printf("%d ", n % 10);     //与例7不同，输出操作是在回溯过程时完成的
    }
}
```

