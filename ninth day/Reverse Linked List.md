# Reverse Linked List

**题目：**

Reverse a singly linked list.

**翻译：**

翻转一个单链表

**思路：**

* 首先，我们需要三个节点进行辅助，第一个节点是当前节点curr，第二个节点是之前的一个节点prev，还有一个就是下一个节点
* 然后我们首先设置prev为null，因为本来头部节点的之前是没有节点的；然后设置当前节点为head节点；
* 根据curr节点来遍历整个链表，循环条件就是curr不为null
* 然后先保存下一个节点设置为nextNode，在将当前的节点的next指向之前的节点，然后将prev和curr都往下移一位
* 最后返回prev，因为跳出条件是null，所以之前的最后一个节点，即为头节点

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
 * @return {ListNode}
 */
var reverseList = function(head) {
    let prev = null;
    let curr = head;
    while(curr){
        let nextNode = curr.next;
        curr.next = prev;
        prev = curr;
        curr = nextNode;
    }
    return prev;
};
```

