# Convert Sorted Array to Binary Search Tree

**题目：**

Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

**翻译：**

给定一个根据升序进行排序的数组，将它转化成一个相对平衡的二叉搜索树

**思路：**

* 因为数组已经根据升序进行排序了，所以要保持相对平衡，就得保证每次插入的节点是中间的元素
* 然后新建一个节点，将当前数组的中间元素赋值给树的当前节点
* 然后去判断数组的长度是否大于1，如果大于1的话，直接返回节点，否则，对它的左右子树进行递归、
* 首先根据mid来进行拆分成两个左右数组
* 然后调用相同的函数

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
 * @param {number[]} nums
 * @return {TreeNode}
 */
var sortedArrayToBST = function(nums) {
    if(!nums.length)
        return null;
    let root = new TreeNode();
    let mid = Math.floor(nums.length / 2);
    root.val = nums[mid];
    if(nums.length > 1){
        const leftNum = nums.slice(0, mid);
        const rightNum = nums.slice(mid + 1);
        root.left = sortedArrayToBST(leftNum);
        root.right = sortedArrayToBST(rightNum);
    }
    return root;
};
```