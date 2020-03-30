---
title: 替换空格
date: 2020-02-01 18:20:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20200201-1.jpg
summary: 剑指 offer：2、替换空格
categories: 剑指 offer
tags:
  - 数组
---
### [2\. 替换空格](https://www.nowcoder.com/practice/4060ac7e3e404ad1a894ef3e17650423?tpId=13&tqId=11155&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy。

### 解题思路：
首先统计字符串中的空格数量`numberOfBlank`，那么将字符串中的空格替换为`%20`后，字符串的长度应该为`indexNew = length + 2 * numberOfBlank - 1`，这样从后向前将原有字符串的字符依次向后移动，遇到空格则替换为`%20`。

### 解答：

```cpp
class Solution {
public:
	void replaceSpace(char *str,int length) {
        if(str == nullptr || length == 0)
            return;
        // 统计空格数量
        int numberOfBlank = 0;
        for(int i = 0; i < length; ++i)
        {
            if(str[i] == ' ')
                ++numberOfBlank;
        }
        int indexOriginal = length - 1;
        int indexNew = length + 2 * numberOfBlank - 1;
        for(int i = indexOriginal; i >= 0; --i)
        {
            if(str[i] != ' ')
            {
                str[indexNew] = str[i];
                --indexNew;
            }
            else
            {
                str[indexNew--] = '0';
                str[indexNew--] = '2';
                str[indexNew--] = '%';
            }
        }
	}
};
```