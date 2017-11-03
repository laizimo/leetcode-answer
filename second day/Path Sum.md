# Path Sum

**题目：**

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

**翻译：**

给定一个二叉树和一个值，判断他是否具备一个从根节点到叶子节点的路径，即路径上所有节点的值的累加和等于给定的值

**例子：**

Given the below binary tree and `sum = 22`,

```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1

```

return true, as there exist a root-to-leaf path `5->4->11->2` which sum is 22.

**思路：**

* 使用递归的方式，首先判断节点是否为空，如果为空直接返回false
* 然后判断节点不为空时，当前节点的值是否等于sum，并且左右子节点都为空，如果满足，则返回true
* 否则，递归左右子节点的值

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
 * @param {number} sum
 * @return {boolean}
 */
var hasPathSum = function(root, sum) {
    if(!root) return false;
    if(root.val === sum && !root.left && !root.right) return true;
    else{
        return hasPathSum(root.left, sum - root.val) || hasPathSum(root.right, sum - root.val);
    }
};
```

