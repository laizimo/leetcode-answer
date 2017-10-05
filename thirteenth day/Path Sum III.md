# Path Sum III

**题目：**

You are given a binary tree in which each node contains an integer value.

Find the number of paths that sum to a given value.

The path does not need to start or end at the root or a leaf, but it must go downwards (traveling only from parent nodes to child nodes).

The tree has no more than 1,000 nodes and the values are in the range -1,000,000 to 1,000,000.

**翻译：**

你被给定一个每个节点含有整数值的二叉树

找出路径和等于给定值的数量

路径不一定需要从根节点开始到叶子节点末尾，但是它必须向下(仅仅穿过父节点到子节点)

该树不超过1000个节点，并且值在-1000000到1000000之间

**例子：**

```
root = [10,5,-3,3,2,null,11,3,-2,null,1], sum = 8

      10
     /  \
    5   -3
   / \    \
  3   2   11
 / \   \
3  -2   1

Return 3. The paths that sum to 8 are:

1.  5 -> 3
2.  5 -> 2 -> 1
3. -3 -> 11
```

**思路：**

* 首先，设定一个计算当前节点路径数量的函数sumPathNum
* 该函数，会根据每次与当前节点相加后的值与给定值之间进行比较，如果相等，则在返回值中加一；否则，递归左右子节点
* 然后在主函数pathSum中，对每个节点进行判断

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
 * @param {number} sum
 * @return {number}
 */
var pathSum = function(root, sum) {
    if(!root)
        return 0;
    const queue = [root];
    let i = 0;
    let pathNum = 0;
    while(i < queue.length){
        let node = queue[i];
        if(node.left)
            queue.push(node.left);
        if(node.right)
            queue.push(node.right);
        pathNum += sumPathNum(node, 0, sum);
        i++;
    }
    return pathNum;
};

function sumPathNum(node, sum, target){
    if(!node)
        return 0;
    sum += node.val
    if(sum === target){
        return sumPathNum(node.right, sum, target) + sumPathNum(node.left, sum, target) + 1;
    }else{
        return sumPathNum(node.right, sum, target) + sumPathNum(node.left, sum, target);
    }
}
```

