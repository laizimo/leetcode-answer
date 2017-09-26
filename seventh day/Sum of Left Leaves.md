#  Sum of Left Leaves

**题目：**

Find the sum of all left leaves in a given binary tree.

**翻译：**

计算给定二叉树所有左叶子节点的值

**例子：**

```
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.
```

**思路：**

* 首先遍历整个二叉树，然后去判断是否是左叶子节点，判断条件当前节点的左节点存在，且其左子节的子女都为null，这时加上左子节点的值

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
var sumOfLeftLeaves = function(root) {
    if(!root)
        return 0;
    const queue1 = [];
    let sum = 0;
    queue1.push(root);
    while(queue1.length){
        let node = queue1[0];
        if(node.left)
            queue1.push(node.left);
        if(node.right)
            queue1.push(node.right);
        if(node.left && !node.left.left && !node.left.right)
            sum += node.left.val;
        queue1.shift();
    }
    return sum;
};
```

