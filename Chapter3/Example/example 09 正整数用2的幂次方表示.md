## 例9
任何一个正整数都可以用2的幂次方表示。a^b可表示a(b)，同时约定几次方用括号表示。比如：<br> 
137=2^7+2^3+2^0=2(7)+2(3)+2(0)，其中7=2^2+2+2^0=2(2)+2+2(0)(2^1用2表示)，3=2+2^0=2+2(0)，即137最后可表示为:<br>
2(2(2)+2+2(0))+2(2+2(0))+2(0)<br>
要求：
+ 输入：正整数(n<=20000)
+ 输出：符合设定的n的0,2表示（在表示中不能有空格）
### 算法设计
```c
#include<stdio.h>
void fac(int n, int r);
int main()
{
    int n;
    printf("input the n: ");
    scanf_s("%d", &n);
    if (n >= 1)
        fac(n, 0);
    else
        printf("Data Error!");
    printf("\n");
    return 0;
}
void fac(int n, int r)
{
    if (n == 1)
    {
        switch (r) 
        {
        case 0:printf("2(0)");break;
        case 1:printf("2");break;
        case 2:printf("2(2)");break;
        default:
            printf("2(");
            fac(r, 0);
            printf(")");
            break;
        }
    }
    else
    {
        fac(n / 2, r + 1);
        if (n % 2 == 1)
            switch (r)
            {
            case 0:printf("+2(0)");break;
            case 1:printf("+2");break;
            case 2:printf("+2(2)");break;
            default:
                printf("+2(");
                fac(r, 0);
                printf(")");
                break;
            }
    }
}
```

