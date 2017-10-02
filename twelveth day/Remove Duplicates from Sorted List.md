# Remove Duplicates from Sorted List

**题目：**

Given a sorted linked list, delete all duplicates such that each element appear only once.

**翻译：**

给定一个排序好的链表，删除所有重复的节点即每个元素只能出现一次。

**例子：**

```
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.
```

**思路：**

* 遍历链表，去判断链表中当前节点与下一个节点的值之间是否相等
* 如果相等，就将下一个节点的next赋值给当前节点
* 如果不相等，则将节点移至下一个节点

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
var deleteDuplicates = function(head) {
    let node = head;
    while(node){
        if(node.next && node.val === node.next.val){
            node.next = node.next.next;
        }else{
            node = node.next;
        }
    }
    return head;
};
```