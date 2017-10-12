# Maximum Average Subarray I

**题目：**

Given an array consisting of `n` integers, find the contiguous subarray of given length `k` that has the maximum average value. And you need to output the maximum average value.

**翻译：**

给定一个长度为n的整数数组，找到拥有最大平均数的长度为k的连续子串。并且你需要去输出这个最大平均数

**例子：**

```
Input: [1,12,-5,-6,50,3], k = 4
Output: 12.75
Explanation: Maximum average is (12-5-6+50)/4 = 51/4 = 12.75
```

**思路：**

* 首先计算第一个长度为k的子串的和
* 然后将其赋值给res变量
* 然后从第二个元素开始遍历数组，sum的值就是减去之前子串的第一个值，然后加上之前子串的后一个值
* 然后比较sum的值与res的值的大小，如果他的值比res大的话，就将这个值赋值给res
* 遍历完成之后，返回res除以k的值

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findMaxAverage = function(nums, k) {
    let res, sum = 0;
    for(let i = 0; i < k; i++){
        sum += nums[i];
    }
    res = sum;
    for(let i = 1; i <= nums.length - k; i++){
        sum = sum - nums[i - 1] + nums[i + k - 1];
        if(sum > res)
            res = sum;
    }
    return res / k;
};
```

