# Binary Tree Level Order Traversal II

**题目：**

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

**翻译：**

给定一个二叉树，返回它的节点的值的自底向上的顺序遍历的结果。(即，从左到右，从叶子到根)

**例子：**

```
Given binary tree [3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
return its bottom-up level order traversal as:
[
  [15,7],
  [9,20],
  [3]
]
```

**思路：**

* 首先，建立一个二维数组，将根节点放进去
* 然后循环，将每层的节点都放入一个数组中，然后将这个数组放入二维数组中
* 每次遍历一层的数组，来形成下一层的数组，然后直至最后一层
* 然后遍历二维数组，将节点替换成节点值
* 然后翻转二维数组

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
 * @return {number[][]}
 */
var levelOrderBottom = function(root) {
    const treeArr = [];
    if(!root)
        return treeArr;
    else
        treeArr.push([root]);
    let i = 0;
    while(true){
        let arr = treeArr[i];
        let nextArr = [];
        for(let j = 0; j < arr.length; j++){
            let node = arr[j];
            if(node.left)
                nextArr.push(node.left);
            if(node.right)
                nextArr.push(node.right);
        }
        if(!nextArr.length)
            break;
        treeArr.push(nextArr);
        i++;
    }
    for(let i = treeArr.length - 1; i >= 0; i--){
        for(let j = 0; j < treeArr[i].length; j++){
            treeArr[i][j] = treeArr[i][j].val;
        }
    }
    return treeArr.reverse();
};
```