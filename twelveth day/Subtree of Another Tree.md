# Subtree of Another Tree

**题目：**

Given two non-empty binary trees s and t, check whether tree t has exactly the same structure and node values with a subtree of s. A subtree of s is a tree consists of a node in s and all of this node's descendants. The tree s could also be considered as a subtree of itself.

**翻译：**

给定两个非空二叉树s和t，检查t二叉树是否恰好与s的子树有相同的结构和节点值。s的一个子树是一棵树包含s中的节点和所有的这个节点的后代。s树也可以考虑作为它自己的子树

**例子：**

```
Given tree s:

     3
    / \
   4   5
  / \
 1   2
Given tree t:
   4 
  / \
 1   2
Return true, because t has the same structure and node values with a subtree of s.
```

```
Given tree s:

     3
    / \
   4   5
  / \
 1   2
    /
   0
Given tree t:
   4
  / \
 1   2
Return false.
```

**思路：**

* 首先，编写一个数相同的比较函数compareTree
* 然后循环整个树，比较s的节点与t之间是否存在相同，如果存在相同，则返回true；不存在，则返回false

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
 * @param {TreeNode} s
 * @param {TreeNode} t
 * @return {boolean}
 */
var isSubtree = function(s, t) {
    const queue = [s];
    while(queue.length){
        let node = queue[0];
        if(compareTree(node, t))
            return true;
        if(node.left)
            queue.push(node.left);
        if(node.right)
            queue.push(node.right);
        queue.shift();
    }
    return false;
};

function compareTree(s, t){
    if(!s && !t)
        return true;
    else if((!s && t) || (s && !t))
        return false;
    else
        return s.val === t.val && compareTree(s.left, t.left) && compareTree(s.right, t.right);
}
```