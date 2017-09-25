# Minimum Absolute Difference in BST

**题目：**

Given a binary search tree with non-negative values, find the minimum absolute difference between values of any two nodes.

**翻译：**

给予一个二叉搜索树具有非负值，查找任意两个节点值间的最小不同差

**例子：**

```
Input:

   1
    \
     3
    /
   2

Output:
1

Explanation:
The minimum absolute difference is 1, which is the difference between 2 and 1 (or between 2 and 3).
```

**思路：**

* 首先，去遍历整个二叉树，使用中序遍历的方式，将节点存入数组，这样可以保证数组是从小到大排列的。
* 这样之后，我们可以遍历数组，通过这样的方式，来计算最小值

**代码实现：**

```javascript
Input:

   1
    \
     3
    /
   2

Output:
1

Explanation:
The minimum absolute difference is 1, which is the difference between 2 and 1 (or between 2 and 3).
```