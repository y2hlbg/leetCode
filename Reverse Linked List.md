#Reverse Linked List

题目：

Reverse a singly linked list.

**Example:**

```
Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL
```

**Follow up:**

A linked list can be reversed either iteratively or recursively. Could you implement both?



##### 解题思路：

这里，用pre来存取反转之后的节点， 

首先，传入值为1的节点，那么，1的下一个指向应该是null， 

接着，传入值为2的节点，那么，2的下一个指向就是1， 

由此可得传入值的指针指向前一个值，所以要把前一个值存起来

依次类推，直到遍历到最后一个节点， 遍历操作用while判断下一个节点是否存在即可

head.next = pre

pre = head

这两行代码就是实现了上述反转的操作，

为了不断链并能继续访问下一个节点，需要先用next保存下一个节点的值，即

next = head.next;， 

当反转操作结束后，再将该值赋给head，即head = next;



##### 代码：

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var reverseList = function(head) {
    var pre = null
    var next = null
    while(head) {
        next = head.next
        head.next = pre
        pre = head
        head = next
    }
    return pre
};
```