### 例18
编程实现高精度数据*长整数的运算
### 算法设计1
```c
#include<stdio.h>
#include<string.h>
int main()
{
    int i, j, len;
    long b, c, d;
    char str[256];
    int r[256];

    printf("input a great number: ");
    //scanf_s("%s", str);
    gets(str);                                  //用字符型数组读取高精度数据
    printf("input a long integer number: ");
    scanf_s("%ld", &c);                         //用长整型变量读取长整数

    len = strlen(str);
    d = 0;                                      //d存储进位，初始为零
    for (i = 0, j = len - 1;i < len;i++, j--)   //由于高精度数从高位到低位存储的，所以从低位起与长整数相乘
    {
        b = (str[j] - 48) * c + d;              //b存储高精度数据每位和长整数相乘并加上进位的结果
        r[i] = b % 10;                          //结果存储在数组r中，从r[0]开始存储结果的每一位
        d = b / 10;
    }
    while (d != 0)                              //若进位未等于0，则继续扩展结果数的高位数
    {
        r[len] = d % 10;
        d = d / 10;
        len++;
    }

    for (i = len - 1;i >= 0;i--)
        printf("%d", r[i]);
    printf("\n");
    return 0;
}
```