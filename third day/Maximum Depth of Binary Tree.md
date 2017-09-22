# Maximum Depth of Binary Tree



**题目：**



Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.



**翻译：**



给一个二叉树，找到它的最大深度。



最大深度是从根节点到最深子节点的路径上的节点数量



**思路：**



> 此处提供两种方法：1. 递归深度(好处，复杂度低，但是容易爆栈)    2. 使用循环处理(空间复杂度高)



* 递归方法
* 定义一个计算深度的函数
  * 函数跳出条件是当节点为空时，返回0
  * 节点非空时，通过递归计算左子树的深度和右子树的深度
  * 返回其中一个比较大的数，然后加一



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
var maxDepth = function(root) {
    return root ? Math.max(dfs(root.left), dfs(root.right)) + 1 : 0;
};

function dfs(root){
    if(!root)
        return 0;
    const dep_left = dfs(root.left);
    const dep_right = dfs(root.right);
    
    return Math.max(dep_left, dep_right) + 1;
}
```



* 循环方法
* 首先，我们需要两个数组来存放每一层的节点，并且设置一个层数的变量
* 如果root存在的话，将其放入arr1中
* 循环，跳出条件arr1为空时
  * 遍历arr1，判断当前元素的左右节点
  * 如果左节点存在，放入arr2；如果右节点存在，放入arr1；
  * 遍历完arr1之后，dep加一，然后将arr2赋值给arr1，重置arr2



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
var maxDepth = function(root) {
    let arr1 = [], arr2 = [];
    let dep = 0;
    if(root)
        arr1.push(root);
    while(arr1.length){
        for(let item of arr1){
            if(item.left)
                arr2.push(item.left);
            if(item.right)
                arr2.push(item.right);
        }
        dep++;
        arr1 = arr2;
        arr2 = [];
    }
    return dep;
};
```

