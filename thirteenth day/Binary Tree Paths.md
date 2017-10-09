# Binary Tree Paths

**题目：**

Given a binary tree, return all root-to-leaf paths.

**翻译：**

给定一个二叉树，返回所有根节点到叶子节点的路径

**例子：**

For example, given the following binary tree:

```
   1
 /   \
2     3
 \
  5

```

All root-to-leaf paths are:

```
["1->2->5", "1->3"]
```

**思路：**

* 首先，判断当前节点是否为空，如果为空返回空数组
* 然后，判断当前节点是否为叶子节点，如果是的话，则返回当前节点的字符串的值
* 之后，通过自身函数调用获得左节点的数组；同样的方式，获得右节点的数组
* 之后，遍历这两个数组，与当前节点进行拼接，然后结果数组

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
 * @return {string[]}
 */
var binaryTreePaths = function(root) {
    if(!root)
        return [];
    if(root && !root.right && !root.left){
        return [root.val.toString()];
    }
    const left = root.left ? binaryTreePaths(root.left) : [];
    const right = root.right ? binaryTreePaths(root.right) : [];
    const res = [];
    for(let item of left){
        res.push(root.val + '->' + item);
    }
    for(let item of right){
        res.push(root.val + '->' + item);
    }
    return res;
};
```

