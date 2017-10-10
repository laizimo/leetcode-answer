# Symmetric Tree

**题目：**

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

**翻译：**

给定一个二叉树，检测它是否是他自身的镜子(即，根据它的中心对称)。

**例子：**

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:

```
    1
   / \
  2   2
 / \ / \
3  4 4  3

```

But the following `[1,2,2,null,3,null,3]` is not:

```
    1
   / \
  2   2
   \   \
   3    3
```

**思路：**

* 首先，编写一个函数nodeSymmetric，比较两个节点之间是否对称
* 判断两个节点是否都为空，如果都为空，则返回true
* 然后判断两个节点都存在，然后比较两个节点的值是否相等，并且递归一个节点的左子节点和另一个节点的右子节点比较结果，加上一个节点的右节点与另一个节点的左节点比较结果
* 如果两种情况都不是，返回false

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
var isSymmetric = function(root) {
    if(!root)
        return true;
    else
        return nodeSymmetric(root.left, root.right);
};

function nodeSymmetric(node1, node2){
    if(!node1 && !node2){
        return true;
    }else if(node1 && node2){
        return node1.val === node2.val && nodeSymmetric(node1.left, node2.right) && nodeSymmetric(node1.right, node2.left);
    }else{
        return false;
    }
}
```

