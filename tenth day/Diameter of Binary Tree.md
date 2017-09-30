# Diameter of Binary Tree

**题目：**

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

**翻译：**

给定一个二叉树，你需要去计算树路径的长度。二叉树的路径是在树中任意两个节点间的最长距离。这个路径有可能不穿过根节点

**例子：**

Given a binary tree 

```
          1
         / \
        2   3
       / \     
      4   5 
```

Return 3, which is the length of the path [4,2,1,3] or [5,2,1,3].

**思路：**

* 首先，我们需要去定义一个计算节点深度的函数，因为两个节点之间的路径的距离是它们公共节点到他们两个的深度之和。
* 因为这个路径有可能不穿过根节点，所以我们需要去计算每个节点的最长路径，通过递归的方式

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
var diameterOfBinaryTree = function(root) {
    if(!root)
        return 0;
    let deepSum = deep(root.left) + deep(root.right);
    return Math.max(deepSum, diameterOfBinaryTree(root.right), diameterOfBinaryTree(root.left));
};

function deep(node){
    if(!node)
        return 0;
    return Math.max(deep(node.left), deep(node.right))+1;
}
```