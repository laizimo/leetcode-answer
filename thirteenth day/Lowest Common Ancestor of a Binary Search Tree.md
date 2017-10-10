# Lowest Common Ancestor of a Binary Search Tree

**题目：**

Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes v and w as the lowest node in T that has both v and w as descendants (where we allow **a node to be a descendant of itself**).”

**翻译：**

给定一个二叉搜索树(BST)，在这棵树中，找到给定两个节点的最小共同祖先。

根据维基百科上LCA的定义：“最小的共同祖先在两个节点v和w之间定义为T中具有v和w作为后代的最低节点（我们允许节点是其自身的后代）。”

**例子；**

```
        _______6______
       /              \
    ___2__          ___8__
   /      \        /      \
   0      _4       7       9
         /  \
         3   5

```

For example, the lowest common ancestor (LCA) of nodes `2` and `8` is `6`. Another example is LCA of nodes `2` and `4` is `2`, since a node can be a descendant of itself according to the LCA definition.

**思路：**

* 首先，定义一个函数，去根据给定的两个节点的数值，去进行查找最小搜索树
* 去判断当前节点于给定两个节点的大小。
* 如果当前节点数值小于最小值，那么在节点的右子树查找
* 如果当前节点数值大于最大值，那么在节点的左子树查找
* 如果处于他们之间，则返回当前节点
* 然后，再在原函数中去判断两个节点的值的大小，然后分别调用之前的函数

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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function(root, p, q) {
    if(p.val > q.val)
        return findAncestor(root, q.val, p.val);
    else
        return findAncestor(root, p.val, q.val);
};

function findAncestor(node, Nmin, Nmax){
    if(node.val < Nmin)
        return findAncestor(node.right, Nmin, Nmax);
    else if(node.val > Nmax)
        return findAncestor(node.left, Nmin, Nmax);
    else
        return node;
}
```

