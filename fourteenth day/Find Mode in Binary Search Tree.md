# Find Mode in Binary Search Tree

**题目：**

Given a binary search tree (BST) with duplicates, find all the [mode(s)](https://en.wikipedia.org/wiki/Mode_(statistics)) (the most frequently occurred element) in the given BST.

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys **less than or equal to** the node's key.
- The right subtree of a node contains only nodes with keys **greater than or equal to** the node's key.
- Both the left and right subtrees must also be binary search trees.

**翻译：**

给定一个有重复的二叉搜索树，找出所有mode(s)(出现最频繁的元素)在给定的二叉搜索树中

一个二叉树由以下规则定义：

* 节点的左子树仅含有节点的值小于或等于当前节点的值
* 节点的右子树仅含有节点的值大于或等于当前节点的值
* 左右子树都必须是二叉搜索树

**例子：**

Given BST `[1,null,2,2]`,

```
   1
    \
     2
    /
   2

```

return `[2]`.

**思路：**

* 首先，使用一个map记录树中节点值的数量，而且同时使用count变量记录最多出现次数
* 然后遍历树的每个节点，如果之前在map中存在，则将该值加一，否则设置map中该值的value为1
* 同时，比较当前元素在map中的值与count，如果大于count，就给count赋值map中的value
* 然后遍历map的key数组，然后比较map中的值是否等于count，如果等于，就将该值放入res数组中
* 返回res数组

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
 * @return {number[]}
 */
var findMode = function(root) {
    const map = new Map();
    const res = [];
    const queue = root ? [root] : [];
    let count = 0;
    while(queue.length){
        let node = queue[0];
        if(map.has(node.val)){
            let num = map.get(node.val) + 1;
            if(num > count)
                count = num;
            map.set(node.val, num);
        }else{
            map.set(node.val, 1);
            if(count < 1)
                count = 1;
        }
        if(node.left)
            queue.push(node.left);
        if(node.right)
            queue.push(node.right);
        queue.shift();
    }
    for(let key of map.keys()){
        if(map.get(key) === count)
            res.push(key);
    }
    return res;
};
```

