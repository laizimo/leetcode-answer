# Contains Duplicate

**题目：**

Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

**翻译：**

给定一个整数数组，查找这个数组中是否含有重复的项。一旦有值在数组中出现两次，你的函数应该返回true，并且如果每个元素都是单一的，你应该返回false

**思路：**

* 首先，将数组进行排序
* 然后遍历数组，对每个元素与其下一个元素进行对比，如果有相同的，就返回true
* 遍历完数组，没有返回true的，直接返回false

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    nums.sort((item1, item2) => item1 - item2);
    for(let i = 0; i < nums.length - 1; i++){
        if(nums[i] == nums[i+1])
            return true;
    }
    return false;
};
```

