# Merge Two Sorted Lists

**题目：**

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**翻译：**

合并两个已经排好序的链表，并且返回它作为一个新的链表。新链表应该由分离第一二链表的所有节点组成

**思路：**

* 递归方法
* 首先，判断两个链表中，是否一个为空，如果是的话，返回另外一个
* 然后建立一个新的节点，进行两个链表当前节点的比较
* 如果l1的nodeVal小于l2的nodeVal，那么将l1的节点值赋值给新节点，然后将新节点的next进行递归
* 反之，亦然

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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    if(!l1)
        return l2;
    if(!l2)
        return l1;
    let head = new ListNode();
    if(l1.val < l2.val){
        head = l1;
        head.next = mergeTwoLists(l1.next, l2);
    }else{
        head = l2;
        head.next = mergeTwoLists(l1, l2.next);
    }
    return head;
};
```

* 循环方式
* 首先建立一个空节点，然后创建一个对象指针，指向这个空节点
* 然后建立循环，判断l1和l2是否都不为空，如果都不为空的话，就比较它们的大小，然后对应的向下移动
* 同样的，对象指针也需要向下移动
* 之后，跳出循环，然后去判断两个链表中，l1是否为空，如果l1为空，那么将l2赋值给对象指针
* 然后返回空节点

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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function(l1, l2) {
    let newList = new ListNode();
    let curr = newList;
    while(l1 && l2){
        if(l1.val < l2.val){
            curr.next = l1;
            l1 = l1.next;
        }else{
            curr.next = l2;
            l2 = l2.next;
        }
        curr = curr.next;
    }
    curr.next = l1 ? l1 : l2;
    return newList.next;
};
```

