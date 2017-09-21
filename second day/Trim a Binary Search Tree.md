# Trim a Binary Search Tree

**题目：**



Given a binary search tree and the lowest and highest boundaries as `L` and `R`, trim the tree so that all its elements lies in `[L, R]` (R >= L). You might need to change the root of the tree, so the result should return the new root of the trimmed binary search tree.



**翻译：**



给一个二叉搜索树，一个最小边界L和最大边界R，修剪二叉树，使得它的所有元素在[L, R]之间。你可能需要去改变树的根节点，所以结果应该返回一个新的被修剪过的二叉搜素树的根节点



**例子：**



```
Input: 
    1
   / \
  0   2

  L = 1
  R = 2

Output: 
    1
      \
       2
```



```
Input: 
    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

Output: 
      3
     / 
   2   
  /
 1
```





> 注：二叉搜索树，是一种特殊的二叉树，它满足一个特性，每个节点的值比左子女(如果存在的话)的值大，同时比右子女(如果存在的话)的值小



**思路：**



树的大部分操作都是可以通过递归解决的。



递归解法：

(1). 我们需要判断当前节点是否为空。为空的话，直接返回。

(2). 之后判断当前节点的值是否比R大。如果比R大，只需要返回其左子树的剪枝结果。

(3). 判断当前节点的值是否比L小。如果比L小，只需要返回其右子树的剪枝结果。

(4). 如果两种情况都不满足，就表明当前节点是满足条件的；那么接下来，只要将其左子树剪枝结果赋值给其左节点；将其右子树剪枝结果赋值给其右节点。之后，返回root



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
 * @param {number} L
 * @param {number} R
 * @return {TreeNode}
 */
var trimBST = function(root, L, R) {
    if(!root) return root;
    if(root.val > R) return trimBST(root.left, L, R);
    if(root.val < L) return trimBST(root.right, L, R);
    
    root.left = trimBST(root.left, L, R);
    root.right = trimBST(root.right, L, R);
    return root;
};
```



