# Two Sum IV - Input is a BST

**题目：**

Given a Binary Search Tree and a target number, return true if there exist two elements in the BST such that their sum is equal to the given target.

**翻译：**

给一个二叉搜索树和一个目标数字，如果在二叉搜索树中存在两个元素，它们的和等于给的目标数字，则返回true。

**例子：**

```
Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

Output: True
```

```
Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

Output: False
```

**思路：**

> 之前，介绍过二叉搜索树的概念，它的特性是不存在重复的树，所以，我们并不用考虑树中会有重复树的情况
>
> 我们会使用HashSet的概念，在js中并没有HashSet的数据结构，但是我们可以使用map来代替，将值作为mao的key值，然后它的value设置成true，那么我们可以在查找的时候，去判断当前的元素是否为true

* 首先，我们去定义一个函数：
* 函数可以通过k，然后去map中匹配是否存在一个元素是否与当前节点的val相加为k的
* 如果存在，则返回true。否则，将节点加入map中
* 然后递归节点的左子树和右子树



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
 * @param {number} k
 * @return {boolean}
 */
var findTarget = function(root, k) {
    const map = new Map();
    return findOne(root, k ,map);
};

var findOne = function(root, k, map){
    if(!root)
        return false;
    if(map.get(k - root.val))
        return true;
    map.set(root.val, true);
    return findOne(root.left, k, map) || findOne(root.right, k, map);
}
```

