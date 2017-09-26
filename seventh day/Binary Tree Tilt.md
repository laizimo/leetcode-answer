# Binary Tree Tilt

**题目：**

Given a binary tree, return the tilt of the **whole tree**.

The tilt of a **tree node** is defined as the **absolute difference** between the sum of all left subtree node values and the sum of all right subtree node values. Null node has tilt 0.

The tilt of the **whole tree** is defined as the sum of all nodes' tilt.

**翻译：**

给定一个二叉树，返回整棵树的倾斜

一个树节点的倾斜被定义为所有左子树的节点的和与所有右子树的节点的和之间绝对值的差值

整个树的倾斜被定义为所有节点倾斜的和

**例子：**

```
Input: 
         1
       /   \
      2     3
Output: 1
Explanation: 
Tilt of node 2 : 0
Tilt of node 3 : 0
Tilt of node 1 : |2-3| = 1
Tilt of binary tree : 0 + 0 + 1 = 1
```

**思路：**

* 首先，定义一个计算所有子节点值的函数sumTree，返回一个值
* 然后根据分别计算当前节点的左子树节点的和与右子树节点的和
* 然后递归计算，最后将总和返回

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
var findTilt = function(root) {
    if(!root)
        return 0;
    sum = Math.abs(sumTree(root.left) - sumTree(root.right));
    return sum + findTilt(root.right) + findTilt(root.left);
};

function sumTree(root){
    if(!root)
        return 0;
    return root.val + sumTree(root.left) + sumTree(root.right);
}
```

