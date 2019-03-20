---
title: （转载）漫画：如何将一个链表“逆序”？
date: 2019-03-20 22:49:37
img: https://upload-images.jianshu.io/upload_images/14484228-cb4e22460f2303b3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: （转载）漫画：如何将一个链表“逆序”？,数据结构-链表逆序
categories: 分享
tags:
  - 数据结构
  - 链表
  - 转载
---
声明：本文转载自微信公众号**程序员小灰**，以获作者授权转载
![](https://upload-images.jianshu.io/upload_images/14484228-cb4e22460f2303b3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-d7408b70b61c39d3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
<center>------第二天-------</center>

![](https://upload-images.jianshu.io/upload_images/14484228-8ae376c01b1f7349.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-00e6674f32a9d0bd.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-1f8fbb7c0bafa40e.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-65b9bc4ee4a3f7bb.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-0b4358cb3da169c7.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-9d0f546519bf16c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-447a04f4a48b521d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-81b0895c78e1a31e.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-78ad295430a3491d.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
（现实里的小灰在刚入行的时候，面试官也问了我这个问题，当时小灰就傻傻的问面试官是单链表还是双链表？然后就没然后了......）
***
![](https://upload-images.jianshu.io/upload_images/14484228-31488f15a61e494f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-cf5860149f92c74f.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-5b8d3f33099a4d70.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-34ed4811378a8d82.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-0b4e47836ea6681a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-1beb05c1519be4f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-2cd160a2febbd672.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-3607e44d7748183d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-02fc7791ea3dee90.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-cb0591d346e9c5c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-31265798ade6d339.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

让我们从链表头部开始，建立三个临时节点的引用，分别为p1，p2，p3。它们分别指向头节点、第二个节点、第三个节点。

![](https://upload-images.jianshu.io/upload_images/14484228-0e6f8a3fad5ec787.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

实现链表逆序的完整步骤如下：

1. 以p2节点为视角，把p2节点原本指向p3的next指针倒转，指向p1。
![](https://upload-images.jianshu.io/upload_images/14484228-7952044da7e225fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 三个临时节点引用p1，p2，p3分别向后移动一格位置。
![](https://upload-images.jianshu.io/upload_images/14484228-322432dfeaaf0597.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 重复第1步的工作，以p2节点为视角，把p2节点原本指向p3的next指针倒转，指向p1。
![](https://upload-images.jianshu.io/upload_images/14484228-4c0c4975c258c55b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 重复第2步的工作，三个临时节点引用p1，p2，p3分别向后移动一格位置。
![](https://upload-images.jianshu.io/upload_images/14484228-d4a2cd2d93646035.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
.......
.......

5. 继续像这样子迭代下去，一直到p2是空为止。
![](https://upload-images.jianshu.io/upload_images/14484228-8b39745e489c0498.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6. 最后，把head节点的next指向空，成为逆序链表的尾节点。并且把p1赋值给head，让p1所在的节点成为逆序链表的头节点。
![](https://upload-images.jianshu.io/upload_images/14484228-ee4ee60c03499905.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-e97bbf305a186106.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-64d00c433eed1d41.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

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

链表反转的逻辑本身，都在reverseLinkedList方法当中。在这里我们把链表的头节点作为了静态成员，实际上也可以作为方法参数传入，只是逻辑上需要一些小小的修改。

![](https://upload-images.jianshu.io/upload_images/14484228-e251580228482082.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-16dcd7f3e50b6bc7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-d7e6a1df05192e50.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/14484228-08c637cb5d85a7a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**如果喜欢小灰的漫画，可以长按下图关注订阅号程序员小灰，收看更多精彩内容哦**

![](https://upload-images.jianshu.io/upload_images/14484228-2e504c60210295e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)










