---
title: 把字符串转换成整数
date: 2019-04-21 17:51:00
img: https://upload-images.jianshu.io/upload_images/14484228-45e79649ee869a59.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer：49、把字符串转换成整数
categories: 剑指 offer
tags:
  - 字符串
---
### [49\. 把字符串转换成整数](https://www.nowcoder.com/practice/1277c681251b4372bdef344468e4f26e?tpId=13&tqId=11202&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
将一个字符串转换成一个整数(实现Integer.valueOf(string)的功能，但是string不符合数字要求时返回0)，要求不能使用字符串转换整数的库函数。 数值为0或者字符串不是一个合法的数值则返回0。

#### 输入描述
> 输入一个字符串,包括数字字母符号,可以为空

#### 输出描述
> 如果是合法的数值表达则返回该数字，否则返回0

#### 示例
> 输入
>> +2147483647
>>
>> 1a33
>
> 输出
>> 2147483647
>>
>> 0

### 解题思路：
本题目要将字符串转换成整数，方法并不复杂，但是要考虑异常处理：
+ 字符串是否为空
+ 字符串对正负号进行处理
+ 输入值是否合法
+ 返回值类型为int，所以要考虑是否有溢出，int范围(-2147483648 ~ 2147483647)

### 解答：

```cpp
class Solution {
public:
    int StrToInt(string str) {
        int len = str.size();
        // 判断字符串是否为空
        if(len == 0)
            return 0;
        int begin = 0, isNegative = 0;
        // 处理'+', '-'
        if(str[0] == '+')
        {
            isNegative = 0;
            begin = 1;
        }
        else if(str[0] == '-')
        {
            isNegative = 1;
            begin = 1;
        }
        int position = 1;
        // 以long long 类型存储转换结果
        long long res = 0;
        for(int i = len -1; i >= begin; --i)
        {
            if(str[i] < '0' || str[i] > '9')
                return 0;
            res += (str[i] - '0') * position;
            position *= 10;
        }
        // 判断是否溢出
        if((isNegative == 0 && res > 0x7fffffff) || (isNegative == 1 && res > 0x80000000))
            return 0;
        else
            res = isNegative ? -res : res;
        return res;
    }
};
```