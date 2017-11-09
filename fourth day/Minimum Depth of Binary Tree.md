# Minimum Depth of Binary Tree

**题目：**

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**翻译：**

给定一个二叉树，找到它的最小深度。

最小深度是从根节点到最近叶子节点通过最短路径的节点个数。

**思路：**

* 如果节点不存在，则返回0
* 如果节点存在，同时不存在左子节点和右子节点，那么返回1
* 如果节点存在，只存在左子节，那么递归左子节点，深度加1
* 如果节点存在，只存在右子节，那么递归右子节点，深度加1
* 如果节点存在，同时左右子节点都存在，那么选择它们其中深度比较小的，深度加1

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
var minDepth = function(root) {
    if(!root) return 0;
    if(root && !root.right && !root.left)
        return 1;
    else if(root && root.right && !root.left)
        return minDepth(root.right) + 1;
    else if(root && root.left && !root.right)
        return minDepth(root.left) + 1;
    else
        return Math.min(minDepth(root.left), minDepth(root.right)) + 1;
};
```

