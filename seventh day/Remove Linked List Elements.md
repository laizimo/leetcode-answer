# Remove Linked List Elements

**题目：**

Remove all elements from a linked list of integers that have value **val**.

**翻译：**

移除整数链表中的所有值为val的元素

**例子：**

***Given:*** 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6,  **val** = 6
***Return:*** 1 --> 2 --> 3 --> 4 --> 5

**思路：**

* 首先，我们需要去遍历链表的头元素，看它的元素值是否等于给定的val
* 如果相等，那么我们将head往后移一位，否则，跳出循环
* 然后，判断head是否为空，如果为空的话，就返回head
* 否则将head赋值给prev变量，之后设定一个curr变量等于prev的next对象
* 然后，循环，判断curr变量是否为空。
* 循环中，判断curr的val值是否等于给定的val值，如果等于的话，就将curr的next值赋值给prev的next，然后将curr赋值为prev的next对象
* 不相等的话，则将顺序往后延一位。

**代码实现：**

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
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
    while(head) {
        if(head.val === val) {
            head = head.next;
        }else {
            break;
        }
    }
    if(!head) return head;
    let prev = head;
    let curr = prev.next;
    while(curr) {
        if(curr.val === val) {
            prev.next = curr.next;
            curr = prev.next;
        }else {
            prev = curr;
            curr = curr.next;
        }
    }
    return head;
};
```

