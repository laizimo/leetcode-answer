# Maximum Product of Three Numbers

**题目：**

Given an integer array, find three numbers whose product is maximum and output the maximum product.

**翻译：**

给定一个整数数组，找到三个数字，他们的产量是最大化的，并且输出最大化的产量

**例子：**

```
Input: [1,2,3]
Output: 6
```

```
Input: [1,2,3,4]
Output: 24
```

**思路：**

* 首先，我们去进行判断数组的长度，如果是长度为3的话，直接输出乘积
* 长度不为3的数组，对它进行排序，然后去判断它的第一第二位的乘积与倒数第二第三位的乘积
* 之后输出较大的一个与最后一位的乘积

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumProduct = function(nums) {
    const len = nums.length;
    if(len === 3)
        return nums.reduce((item1, item2) => item1 * item2);
    else{
        nums.sort((item1, item2) => item1 - item2);
        if(nums[0] * nums[1] > nums[len - 2] * nums[len - 3]){
            return nums[0] * nums[1] * nums[len - 1];
        }else{
            return nums[len - 1] * nums[len - 2] * nums[len - 3];
        }
    }
};
```