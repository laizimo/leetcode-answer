# Maximum Subarray

**题目：**

Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

**翻译：**

在数组中，查找一个元素和最大的连续子串(至少包含一个数)

**例子：**

For example, given the array `[-2,1,-3,4,-1,2,1,-5,4]`,
the contiguous subarray `[4,-1,2,1]` has the largest sum = `6`.

**思路：**

* 首先，我们需要找到整个数组中的最大值
* 然后我们可以设置两个变量sum和res
* 然后遍历数组，sum每次都加上当前元素
* 如果sum的值小于0，那么就将sum置为0，因为需要找到一个连续最大的子序列，必须保证相加和最好是大于0开始的
* 如果sum的值比res大的话，就将sum的值赋给res
* 遍历完数组之后，去判断res是否等于0，如果等于0，就返回最大值。如果不为0，则返回res

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    const Nmax = Math.max(...nums);
    let sum = 0;
    let res = 0;
    for(let i = 0; i < nums.length; i++){
        sum += nums[i];
        if(sum < 0)
            sum = 0;
        if(sum > res)
            res = sum;
    }
    return res === 0 ? Nmax : res;
};
```

