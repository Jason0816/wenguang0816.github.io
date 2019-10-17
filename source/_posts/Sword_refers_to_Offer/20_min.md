---
title: 包含min函数的栈
date: 2019-08-11 18:40:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20191017-1.jpg
summary: 剑指 offer：20、包含min函数的栈
categories: 剑指 offer
tags:
  - 栈
---
### [20\. 包含min函数的栈](https://www.nowcoder.com/practice/4c776177d2c04c2494f2555c9fcc1e49?tpId=13&tqId=11173&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

### 解题思路：
这道题我们需要创建两个栈，一个栈`base`来作为栈结构主体，个辅助栈`sMin`来记录入栈的最小值，根据题目接口，我们需要实现四个方法：
1. void push(int value): 在每次入栈时，如果入栈值`value`小于`sMin`中的元素，则将`value`压栈到`sMin`，这样能够保证最小元素永远在`sMin`栈顶
2. void pop(): 如果出栈元素等于`sMin`栈顶元素时，`sMin`栈顶元素出栈
3. int top(): 返回栈`base`的栈顶元素
4. int min(): 返回栈`sMin`的栈顶元素

笔者展示的代码只是简单的实现了题目要求的包含min函数的栈，并且通过了牛客网的测试用例。不过代码并不完整，比如在调用`pop()`方法时应该去判断`base`和`sMin`是否为空，如果为空应该抛出异常。有兴趣的读者可以进一步完善代码。

### 解答：

```cpp
class Solution {
public:
    void push(int value) {
        base.push(value);
        if(sMin.empty())
            sMin.push(value);
        if(value < sMin.top())
        {
            sMin.push(value);
        }
    }
    void pop() {
        if(base.top() == sMin.top())
            sMin.pop();
        base.pop();
    }
    int top() {
        if(!base.empty())
            return base.top();
        else
            return 0x7fffffff;
    }
    int min() {
        if(!sMin.empty())
            return sMin.top();
        else
            return 0x7fffffff;
    }
private:
    stack<int> base, sMin;
};
```