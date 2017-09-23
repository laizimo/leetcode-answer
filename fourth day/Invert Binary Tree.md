# Invert Binary Tree

**题目：**



Invert a binary tree.

```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

to

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```



**翻译：**



转换二叉树：将左右子树的节点调换位置



**思路：**



>  分析：可以使用递归的方法去做完成



* 递归函数跳出条件：当节点为空的时候，直接返回节点
* 首先使用一个中间节点，来进行左右子树的交换
* 然后递归交换左右子树
* 返回当前节点



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
 * @return {TreeNode}
 */
var invertTree = function(root) {
    if(!root)
        return root;
    let node = root.left;
    root.left = root.right;
    root.right = node;
    root.left = invertTree(root.left);
    root.right = invertTree(root.right);
    return root;
};
```

