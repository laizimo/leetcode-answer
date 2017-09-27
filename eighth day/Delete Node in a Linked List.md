# Delete Node in a Linked List

**题目：**

Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

Supposed the linked list is 1 -> 2 -> 3 -> 4 and you are given the third node with value 3, the linked list should become 1 -> 2 -> 4 after calling your function.

**翻译：**

写一个在一个单链表中删除节点(除了尾部)的函数，仅仅给定一个连接的节点

假设单链表是1 -> 2 -> 3 -> 4，并且你将被给予第三个值为3的节点，调用函数之后，这个链表应该变成1 -> 2 -> 4

**思路：**

> 一开始并没有怎么理解这道题目，不过实现起来挺简单的

* 只需要将给定节点的值变成下一个节点的值，然后给定节点的链接变成下一个节点的链接就可以了

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
 * @param {ListNode} node
 * @return {void} Do not return anything, modify node in-place instead.
 */
var deleteNode = function(node) {
    node.val = node.next.val;
    node.next = node.next.next;
};
```