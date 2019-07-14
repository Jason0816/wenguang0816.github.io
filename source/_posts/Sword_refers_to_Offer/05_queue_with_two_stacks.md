---
title: 用两个栈实现队列
date: 2019-04-18 09:20:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190418-1.jpg
summary: 剑指 offer：5、用两个栈实现队列
categories: 剑指 offer
tags:
  - 栈
  - 队列
---
### [5\. 用两个栈实现队列](https://www.nowcoder.com/practice/54275ddae22f475981afa2244dd448c6?tpId=13&tqId=11158&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。

### 解题思路：
入队：将元素进栈A
出队：判断栈B是否为空，如果为空，则将栈A中所有元素依次出栈，并压栈进入栈B，之后栈B出栈；如果不为空，栈B直接出栈。

### 解答：

```cpp
class Solution
{
public:
    void push(int node) {
        stack1.push(node);
    }

    int pop() {
        if(stack2.empty() && stack1.empty())
        {
            // 队列为空，异常处理
            throw "The queue is empty!";
        }
        if(stack2.empty())
        {
            while(!stack1.empty())
            {
                int tmp = stack1.top();
                stack1.pop();
                stack2.push(tmp);
            }
        }
        int top = stack2.top();
        stack2.pop();
        return top;
    }

private:
    stack<int> stack1;
    stack<int> stack2;
};
```