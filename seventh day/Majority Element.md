# Majority Element

**题目：**

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

**翻译：**

给定一个尺寸为n的数组，找到最大元素。最大元素是出现n/2次的元素

你必须假定数组是非空的，而且最大元素一定存在于数组

**思路：**

* 将数组排序，然后输出数组长度的一半的位置

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    nums.sort((item1, item2) => item1 - item2);
    const midLen = Math.floor(nums.length / 2);
    return nums[midLen];
};
```

