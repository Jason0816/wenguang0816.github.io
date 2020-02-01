---
title: （转载）漫画：如何将一个链表“逆序”？
date: 2019-03-20 22:49:37
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190320-1.jpg
summary: （转载）漫画：如何将一个链表“逆序”？,数据结构-链表逆序
categories: 分享
tags:
  - 数据结构
  - 链表
  - 转载
---
声明：本文转载自微信公众号**程序员小灰**，以获作者授权转载
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-1.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-2.jpg)
<center>------第二天-------</center>

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-3.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-4.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-5.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-6.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-7.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-8.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-9.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-10.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-11.jpg)
（现实里的小灰在刚入行的时候，面试官也问了我这个问题，当时小灰就傻傻的问面试官是单链表还是双链表？然后就没然后了......）
***
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-12.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-13.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-14.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-15.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-16.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-17.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-18.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-19.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-20.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-21.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-22.jpg)

让我们从链表头部开始，建立三个临时节点的引用，分别为p1，p2，p3。它们分别指向头节点、第二个节点、第三个节点。

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-23.jpg)

实现链表逆序的完整步骤如下：

1. 以p2节点为视角，把p2节点原本指向p3的next指针倒转，指向p1。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-24.jpg)

2. 三个临时节点引用p1，p2，p3分别向后移动一格位置。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-25.jpg)

3. 重复第1步的工作，以p2节点为视角，把p2节点原本指向p3的next指针倒转，指向p1。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-26.jpg)

4. 重复第2步的工作，三个临时节点引用p1，p2，p3分别向后移动一格位置。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-27.jpg)
.......
.......

5. 继续像这样子迭代下去，一直到p2是空为止。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-28.jpg)

6. 最后，把head节点的next指向空，成为逆序链表的尾节点。并且把p1赋值给head，让p1所在的节点成为逆序链表的头节点。
![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-29.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-30.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-31.jpg)

> Java:

```java
private static Node head;
public static void reverseLinkedList()
{
    if(head == null || head.next == null)
        return;
    Node p1 = head;
    Node p2 = head.next;
    Node p3 = null;
    while(p2 != null)
    {
        p3 = p2.next;
        p2.next = p1;
        p1 = p2;
        p2 = p3;
    }
    head.next = null;
    head = p1;
}

private static class Node
{
    int data;
    Node next;
    Node(int data)
    {
        this.data = data;
    }
}

public static void main(String[] args)
{
    // 初始化链表
    head = new Node(3);
    head.next = new Node(5);
    Node temp = head.next;
    temp.next = new Node(1);
    temp = temp.next;
    temp.next = new Node(4);
    temp = temp.next;
    temp.next = new Node(9);

    // 逆序前输出链表
    temp = head;
    while(temp != null)
    {
        System.out.println(temp.data);
        temp = temp.next;
    }

    // 逆序链表
    reverseLinkedList();
    
    // 逆序后输出链表
    temp = head;
    while(temp != null)
    {
        System.out.println(temp.data);
        temp = temp.next;
    }
}
```
> C++

```cpp
#include <iostream>
using namespace std;

class Node
{
public:
    int data;
    Node* next;
    Node(int da, Node* p = nullptr)
    {
        this->data =  da;
        this->next = p;
    }
};

Node* reverseLinkedList(Node *head)
{
    if(head == nullptr || head->next == nullptr)
        return head;
    Node *p1 = head;
    Node *p2 = head->next;
    Node *p3 = nullptr;
    while(p2 != nullptr)
    {
        p3 = p2->next;
        p2->next = p1;
        p1 = p2;
        p2 = p3;
    }
    head->next = nullptr;
    head = p1;
    return head;
}

int main()
{
    // 初始化链表
    Node *head;
    head = new Node(3);
    head->next = new Node(5);
    Node *tmp = head->next;
    tmp->next = new Node(1);
    tmp = tmp->next;
    tmp->next = new Node(4);
    tmp = tmp->next;
    tmp->next = new Node(9);

    cout << "逆序前" << endl;
    // 逆序前输出链表
    tmp = head;
    while(tmp != nullptr)
    {
        cout << tmp->data << endl;
        tmp = tmp->next;
    }
    // 逆序链表
    head = reverseLinkedList(head);

    cout << "逆序后" << endl;
    // 逆序后输出链表
    tmp = head;
    while(tmp != nullptr)
    {
        cout << tmp->data << endl;
        tmp = tmp->next;
    }
}
```
链表反转的逻辑本身，都在reverseLinkedList方法当中。在这里我们把链表的头节点作为了静态成员，实际上也可以作为方法参数传入，只是逻辑上需要一些小小的修改。

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-32.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-33.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-34.jpg)

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-35.jpg)

**如果喜欢小灰的漫画，可以长按下图关注订阅号程序员小灰，收看更多精彩内容哦**

![](https://gitee.com/wenguang0816/blogPic/raw/master/20190320-36.jpg)