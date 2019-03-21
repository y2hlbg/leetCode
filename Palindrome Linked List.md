# Palindrome Linked List

Given a singly linked list, determine if it is a palindrome.

**Example 1:**

```
Input: 1->2
Output: false
```

**Example 2:**

```
Input: 1->2->2->1
Output: true
```



分析：判断回文链表



考虑两种解法：

1、全部放入数组中，双指针，遍历。第一个跟最后一个做比较

2、找到中位数，翻转后边的链表，对比两个链表的每一个节点



代码：

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
 * @return {boolean}
 */
var isPalindrome = function(head) {
    if (!head || !head.next) return true;

    var dev = null;
    var slow = head;
    var fast = head;
    while (fast && fast.next && fast.next.next) {
        fast = fast.next.next;
        slow=slow.next;
    }
    slow.next = reverseList(slow.next);
    slow = slow.next;
    while (slow) {
        if (slow.val !== head.val) {
            return false;
        }
        slow = slow.next;
        head = head.next;
    }
    return true;
};

var reverseList = function(head) {
    var prev = null;
    var next = null;
    while(head !== null) {
        next = head.next;
        head.next = prev;
        prev = head;
        head = next;
    }
    return prev;
};
```

