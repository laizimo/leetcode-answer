# Minimum Moves to Equal Array Elements

**题目：**

Given a **non-empty** integer array of size *n*, find the minimum number of moves required to make all array elements equal, where a move is incrementing *n* - 1 elements by 1.

**翻译：**

给定一个长度为n的非空整数数组，查找最小的被要求移动步数来使得数组所有元素相等，其中一次移动表示n-1个元素增加1

**例子：**

```
Input:
[1,2,3]

Output:
3

Explanation:
Only three moves are needed (remember each move increments two elements):

[1,2,3]  =>  [2,3,3]  =>  [3,4,3]  =>  [4,4,4]
```

**思路：**

> 这个可以通过数学来分析，假定我们有一个数组[x1, x2, x3, x4, x5, x6]
>
> 其中x1最小，x6最大
>
> 那么我们第一次移动(x6 - x1)步，使得数组变成[x6, x2+x6-x1, x3+x6-x1, x4+x6-x1, x5+x6-x1, x6]
>
> 之后，最大的是x5+x6-x1，所以我们还得移动(x5+x6-x1-x6) => (x5-x1)步，以此类推，我们只需要移动每个元素相对于最小元素的差值就可以了

* 首先，得到数组中最小的数值
* 遍历数组，然后增加与最小数值之间的差值

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var minMoves = function(nums) {
    let sum = 0;
    let Mnum = Math.min(...nums);
    for(let i = 0; i < nums.length; i++){
        sum += nums[i] - Mnum;
    }
    return sum;
};
```

