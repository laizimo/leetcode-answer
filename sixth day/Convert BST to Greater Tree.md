# Convert BST to Greater Tree

**题目：**

Given a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus sum of all keys greater than the original key in BST.

**翻译：**

给一个二叉搜索树(BST)，使用一个更大的数去改造它即每个原始节点的值通过累加这个二叉树中比它的值更大的值来修改

**例子：**

```
Input: The root of a Binary Search Tree like this:
              5
            /   \
           2     13

Output: The root of a Greater Tree like this:
             18
            /   \
          20     13
```

**思路：**

* 我们可以使用先遍历整个树，然后将树的节点存放到一个数组中，记得使用右子树->根节点->左节点的方式遍历，这样可以保证值最大的节点存放在数组的开始
* 之后，累加数组中的每个值
* 返回节点

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
 * @return {TreeNode}
 */
var convertBST = function(root) {
    const arr = loopBST(root);
    let sum = 0;
    for(let i = 0; i < arr.length; i++){
        arr[i].val += sum;
        sum = arr[i].val;
    }
    return root;
};

function loopBST(root){
    if(!root)
        return [];
    return loopBST(root.right).concat([root], loopBST(root.left));
}
```