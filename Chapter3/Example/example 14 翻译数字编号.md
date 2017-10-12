### 例14
编写算法将数字编号“翻译”成英文编号  
例如，将编号35760“翻译”成英文编号three-five-seven-six-zero。
### 算法设计1
```c
#include<stdio.h>
int main()
{
    long n;
    int i, a[10];
    char str[10][6] = { "zero","one","two","three","four","five","six","seven","eight","nine" };
    printf("input a number: ");
    scanf_s("%ld", &n);
    printf("%ld English exp: ",n);
    i = 0;
    while (n >= 10)
    {
        a[i++] = n % 10;
        n /= 10;
    }
    a[i] = n;
    printf("%s", str[a[i]]);
    i--;
    while (i >= 0)
    {
        printf("-%s", str[a[i]]);
        i--;
    }
    printf("\n");
    return 0;
}
```
### 算法分析
无法正确存储以零开头的编号，如“0001”，结果只能为zero。  
需要开辟数组来存储从低位到高位的每位位数，在倒着输出。
### 算法设计2
```c
#include<stdio.h>
#include<string.h>
int main()
{
    char s[20];
    int i, len;
    char str[10][6] = { "zero","one","two","three","four","five","six","seven","eight","nine" };
    printf("input a number: ");
    gets(s);
    printf("%s English exp: ", s);
    printf("%s", str[s[0] - 48]);
    len = strlen(s);
    for (i = 1;i < len;i++)
        printf("-%s", str[s[i]-48]);
    printf("\n");
    return 0;
}
```
### 算法分析
不需要开辟数组存储翻译结果  
无需通过算法运算取编号的各位数字