## 例6 求n!
```c
#include<stdio.h>
int fact(int n);
int main()
{
    int n;
    printf("输入n值: ");
    scanf_s("%d", &n);
    printf("n! = %d\n", fact(n));
    return 0;
}
int fact(int n)
{
    if(n == 1)
        return 1;
    else
        return n * fact(n-1);
}
```
