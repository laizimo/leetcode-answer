# Balanced Binary Tree

**题目：**

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of *every* node never differ by more than 1.

**翻译：**

给定一个二叉树，决定它是否是高度平衡的

对于这一个问题，一个高度平衡的二叉树被定义为一个二叉树中两个子树的每个节点之间的深度差从不超过1

**思路：**

* 首先，编写一个计算节点高度的函数getDep
* 通过这个去计算每个的左子树和右子树的高度，去进行比较，然后递归每个子树，进行判断。

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
 * @return {boolean}
 */
var isBalanced = function(root) {
    if(!root)
        return true;
    return Math.abs(getDep(root.left) - getDep(root.right)) <= 1 && isBalanced(root.left) && isBalanced(root.right);
};

function getDep(node){
    if(!node)
        return 0;
    let rightDep = node.right && getDep(node.right);
    let leftDep = node.left && getDep(node.left);
    return Math.max(rightDep, leftDep) + 1;
}
```

