# Second Minimum Node In a Binary Tree

**题目：**

Given a non-empty special binary tree consisting of nodes with the non-negative value, where each node in this tree has exactly two or zero sub-node. If the node has two sub-nodes, then this node's value is the smaller value among its two sub-nodes.

Given such a binary tree, you need to output the second minimum value in the set made of all the nodes' value in the whole tree.

If no such second minimum value exists, output -1 instead.

**翻译：**

给定一个非空的特殊二叉树，其包含的节点值均为非负整数，其中每个节点恰好只有两个或0个子节点。如果节点具备两个子节点，那么它节点的值比它的两个子节点的值更小

给定这样一个二叉树，你需要去输出第二小的值在这棵树的所有节点值组成的集合中。

如果没有这样的第二小的值存在，输出-1代替。

**例子：**

```
Input: 
    2
   / \
  2   5
     / \
    5   7

Output: 5
Explanation: The smallest value is 2, the second smallest value is 5.
```

```
Input: 
    2
   / \
  2   2

Output: -1
Explanation: The smallest value is 2, but there isn't any second smallest value.
```

**思路：**

* 首先，设置一个队列存放根节点，然后设置一个较大的值secMin。
* 循环根节点，如果根节点的值小于secMin，但是大于根节点的值，就将这个值赋值给secMin。
* 之后，将当前节点的左右接到放入队列
* 最后，将当前节点移除，循环跳出条件队列为空
* 判断secMin是否等于之前设置的较大值，如果等于，返回-1；如果不等于，则返回这个值。

**代码实现：**

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var findSecondMinimumValue = function(root) {
    if(!root)
        return -1;
    let secMin = 9999;
    const queue = [root];
    while(queue.length){
        let node = queue[0];
        if(node.val < secMin && node.val > root.val)
            secMin = node.val;
        if(node.left)
            queue.push(node.left);
        if(node.right)
            queue.push(node.right);
        queue.shift();
    }
    return secMin === 9999 ? -1 : secMin;
};
```