# Middle of the Linked List

快慢指针，快指针到尽头，慢指针是中间节点。

- 首先我们设置两个指针slow和fast，slow指针每次移动一步，fast指针每次移动两步；

- 如果链表中节点个数为偶数时，当快指针无法继续移动时，慢指针刚好指向中点；如果链表中节点个数为奇数时，当快指针走完，慢指针指向中点前一个节点。

```javascript
var middleNode = function(head) {  
    if (!head) {  
        return head;  
    }  
    for (var p1 = head, p2 = head; true; p1 = p1.next, p2 = p2.next.next) {  
        if (!p2.next) {  
            return p1;  
        }  
        if (!p2.next.next) {  
            return p1.next;  
        }  
    }  
}; 
```





