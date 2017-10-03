## 例７
任给十进制的正整数，请从低位到高位逐位输出各位数字<br>
(将以下两个算法中10用变量m代替，就可以将输入的十进制数转换为m进制数输出。)
### 算法设计
循环算法
```c
#include<stdio.h>
int main()
{
    int n;
    printf("输入n值： ");
    scanf_s("%d", &n);
    printf("从低位到高位逐位输出：");
    while (n>=10)
    {
        printf("%d ", n % 10);
        n /= 10;
    }
    printf("%d\n", n);
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
    printf("从低位到高位逐位输出：");
    fac(n);
    printf("\n");
    return 0;
}
void fac(int n)
{
    if (n < 10)
        printf("%d", n);
    else
    {
        printf("%d ", n % 10);
        fac(n / 10);
    }
}
```

