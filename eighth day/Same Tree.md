# Same Tree

**题目：**

Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

**翻译：**

给定两个二叉树，写一个函数去检测他们是否相等

如果两个二叉树的结构相同并且他们节点具备相同的值，那么可以判定两个二叉树是相等的

**思路：**

* 使用递归的方法，对两颗树的每个节点进行判断
* 判断的情况可分为三种情况：
* 1. 两个节点都存在，那么就对他们的值进行判断，然后递归判断它们的左节点和右节点
* 2. 其中一个节点存在，而另一个节点不存在，则返回false
* 3. 两个节点都不存在，返回true

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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {boolean}
 */
var isSameTree = function(p, q) {
    if(p && q){
        return p.val === q.val && isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }else if((p && !q) || (!p && q)){
        return false;
    }else{
        return true;
    }
};
```