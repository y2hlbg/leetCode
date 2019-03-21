# Linked List Cycle II

Given a linked list, return the node where the cycle begins. If there is no cycle, return `null`.

To represent a cycle in the given linked list, we use an integer `pos` which represents the position (0-indexed) in the linked list where tail connects to. If `pos` is `-1`, then there is no cycle in the linked list.

**Note:** Do not modify the linked list.

 

**Example 1:**

```
Input: head = [3,2,0,-4], pos = 1
Output: tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

![img](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

**Example 2:**

```
Input: head = [1,2], pos = 0
Output: tail connects to node index 0
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

![img](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

**Example 3:**

```
Input: head = [1], pos = -1
Output: no cycle
Explanation: There is no cycle in the linked list.
```

![img](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)





分析：

没什么思路，看了网上别人的解答。学到了。判断链表是否有环，其实可以使用快慢指针，如果列表有环，则快慢指针肯定会汇合。就比如两个人在操场长跑，甲的速度是乙的二倍，那么总有一个时间点，甲乙会相遇。

当相遇的时候，快指针指向相遇点，慢指针回到head，快指针也每次走一步。因为速度相同，所以单位时间内走的路程相同，最后相遇的点就是环的入口



至于为什么相交可以参考下图

![301735018146408](/Users/dingchen/Documents/临时截图/301735018146408.jpg)



详细解释参考链接如下

<https://blog.csdn.net/willduan1/article/details/50938210>



代码

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
var detectCycle = function(head) {
    if (head === null || head.next === null) {
        return null
    }
    let fp = head, sp = head; 
    while (fp !== null && fp.next !== null) {
        sp = sp.next
        fp = fp.next.next
        if (sp === fp) {
            break
        }
    }
    if (fp === null || fp.next === null) {
        return null
    }
    sp = head
    while(sp !== fp) {
        sp = sp.next
        fp = fp.next
    }
    return sp
};
```



