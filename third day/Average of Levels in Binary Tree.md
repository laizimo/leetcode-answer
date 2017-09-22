# Average of Levels in Binary Tree

**题目：**

Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.

**翻译：**

给予一个非空二叉树，返回一个由每层节点的值的平均值组成的数组

**例子：**

```
Input:
    3
   / \
  9  20
    /  \
   15   7
Output: [3, 14.5, 11]
Explanation:
The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].
```

> 解释： 第0层的节点平均数是3，第一层是13.5，第二层是11，然后返回[3, 14.5, 11]

**思路：**

> 分析：我们可以利用两个队列，js中是数组

* 将根节点放入第一个队列
* 外层循环，跳出条件是第一个队列中的内容为空
  * 遍历队列，将队列中的节点值相加
    * 判断当前节点的左右子女是否为空，若非空的话，将之放入第二个队列
  * 之后求当前层的平均值，总和/第一个队列的长度
  * 之后将第二个队列内容赋值给第一个队列
  * 将第二个队列置空
  
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
var averageOfLevels = function(root) {
    let queue1 = [];
    let queue2 = [];
    const res = [];
    queue1.push(root);
    while(queue1.length){
        let sum = 0;
        for(var item of queue1){
            sum += item.val;
            if(item.left)
                queue2.push(item.left);
            if(item.right)
                queue2.push(item.right);
        }
        res.push(sum / queue1.length);
        queue1 = queue2;
        queue2 = [];
    }
    return res;
};
```
