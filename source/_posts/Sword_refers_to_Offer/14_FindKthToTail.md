---
title: 链表中倒数第k个节点
date: 2019-04-23 19:00:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190423-1.jpg
summary: 剑指 offer：14、链表中倒数第k个节点
categories: 剑指 offer
tags:
  - 链表
  - 鲁棒性
---
### [14\. 链表中倒数第k个节点](https://www.nowcoder.com/practice/529d3ae5a407492994ad2a246518148a?tpId=13&tqId=11167&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
输入一个链表，输出该链表中倒数第k个结点。

### 解题思路：
+ 定义两个指针，第一个指针从链表头部开始遍历至第`k-1`个节点，第二个指针保持不懂；
+ 第二个指针指向链表头部，然后两个指针同时向后遍历，由于两个指针的距离始终保持`k-1`，所以当第一个指针到达链表的尾节点是，第二个指针正好指向倒数第`k`个节点

异常处理：
1. 输入为空指针
2. 链表节点数小于k
3. k为0

### 解答：

```cpp
/*
struct ListNode {
	int val;
	struct ListNode *next;
	ListNode(int x) :
			val(x), next(nullptr) {
	}
};*/
class Solution {
public:
    ListNode* FindKthToTail(ListNode* pListHead, unsigned int k) {
        if(pListHead == nullptr || k == 0)
            return nullptr;
        ListNode* pAhead = pListHead;
        ListNode* pBehind = nullptr;
        for(int i = 0; i < k - 1; ++i)
        {
            if(pAhead->next != nullptr)
                pAhead = pAhead->next;
            else
                return nullptr;
        }
        pBehind = pListHead;
        while(pAhead->next != nullptr)
        {
            pAhead = pAhead->next;
            pBehind = pBehind->next;
        }
        return pBehind;
    }
};
```