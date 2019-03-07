# Merge Two Sorted Lists


Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```



分析：

合并两个有序的链表

如果其中一个为空，则返回另一个链表即可

对于不固定的长度，如果想遍历下去，要么用 while 判断下个节点是null，要么使用递归的思想调用表本身（如果使用递归，需要注意的是参数问题，需要让参数指向下一个节点）

对于固定的长度，如果想遍历，for，while，比较好



以上为暂时见解，仅做记录，不做推荐



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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */

var mergeTwoLists = function(l1, l2) {
    if (l1===null) return l2;
    if (l2===null) return l1;
    
    if (l1.val <= l2.val) {
        l1.next = mergeTwoLists(l1.next,l2);
        return l1;
    } else {
        l2.next = mergeTwoLists(l1,l2.next);
        return l2;
    }
}
```



