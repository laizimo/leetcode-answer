# Two Sum

**题目：**

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the *same* element twice.

**翻译：**

给定一组整数，然后两个相加和为指定目标的两个数字的下标。

你可以假定每个输出将有确定的一个解决方案，并且你不可以使用相同的元素

**例子：**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

**思路：**

* 首先，遍历一次循环，确定一个整数
* 然后，遍历这个数后面的所有数，如果满足target的话，返回下标

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for(let i = 0; i < nums.length - 1; i++){
        for(let j = i + 1; j < nums.length; j++){
            if(nums[i] + nums[j] === target){
                return [i, j];
            }
        }
    }
};
```

