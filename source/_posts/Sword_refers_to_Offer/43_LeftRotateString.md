---
title: 左旋转字符串
date: 2019-04-21 18:23:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190421-2.jpg
summary: 剑指 offer：43、左旋转字符串
categories: 剑指 offer
tags:
  - 字符串
---
### [43\. 左旋转字符串](https://www.nowcoder.com/practice/12d959b108cb42b1ab72cef4d36af5ec?tpId=13&tqId=11196&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
汇编语言中有一种移位指令叫做循环左移（ROL），现在有个简单的任务，就是用字符串模拟这个指令的运算结果。对于一个给定的字符序列S，请你把其循环左移K位后的序列输出。例如，字符序列S=”abcXYZdef”,要求输出循环左移3位后的结果，即“XYZdefabc”。是不是很简单？OK，搞定它！

### 解题思路：
+ 思路1: 首先确定左移之后第一个字符在原字符串中的位置`begin`，然后从`begin`向后遍历完原字符串，然后从0开始遍历到`begin`，将两部分拼接即可
+ 思路2: `begin`为分界线，将两侧字符串分别反转，然后再将整个字符串反转

### 解答：

```cpp
// 解法1:
class Solution {
public:
    string LeftRotateString(string str, int n) {
        int len = str.size();
        if(len == 0)
            return "";
        string res = "";
        int begin = n % len;
        for(int i = begin; i < len; ++i)
            res += str[i];
        for(int i = 0; i < begin; ++i)
            res += str[i];
        return res;
    }
};
// 解法2:
class Solution {
public:
    string LeftRotateString(string str, int n) {
        int len = str.size();
        if(len == 0)
            return "";
        int begin = n % len;
        reverse(str.begin(), str.begin() + begin);
        reverse(str.begin() + begin, str.end());
        reverse(str.begin(), str.end());
        return str;
    }
};
```