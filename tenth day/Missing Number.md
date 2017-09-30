# Missing Number

**题目：**

Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.

**翻译：**

给定一个数组包含n不同的数组来自于0，1，2，...，n，找到数组中丢失的那个

**例子：**

Given nums = [0, 1, 3] return 2.

**思路：**

* 首先计算数组的总和
* 然后，计算0-n的总和
* 返回它们的差值

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function(nums) {
    let sum = nums.reduce((item1, item2) => item1 + item2);
    let n = nums.length;
    return (n + 1) * n / 2 - sum;
};
```