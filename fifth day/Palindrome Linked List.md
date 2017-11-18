# Palindrome Linked List

**题目：**

Given a singly linked list, determine if it is a palindrome.

**翻译：**

给定一个单链表，判断它是否是回文的

**思路：**

- 首先，初始化一个数组arr
- 然后，将链表的节点值都放入数组中
- 然后，判断数组与倒置后的数组相等

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
 * @return {boolean}
 */
var isPalindrome = function(head) {
    const arr = [];
    while(head){
        arr.push(head.val);
        head = head.next;
    }
    return arr.join('') === arr.reverse().join('');
};
```

