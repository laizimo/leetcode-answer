# Search Insert Position

**题目：**

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

**翻译：**

给定一个排序好的数组和一个目标值，如果目标存在返回下标。如果不存在，返回该值应该按顺序插入的位置下标

你假定数组中没有重复值

**例子：**

`[1,3,5,6]`, 5 → 2
`[1,3,5,6]`, 2 → 1
`[1,3,5,6]`, 7 → 4
`[1,3,5,6]`, 0 → 0

**思路：**

* 顺序查找方式
* 判断当前元素是否等于target值，如果等于，返回当前元素下标
* 然后去判断当i等于0时，当前元素是否小于当前元素值，如果小于，返回0
* 判断当i等于nums.length - 1时，当前元素是否大于当前元素值，如果大于，返回nums.length
* 最后，判断当前元素是否比之前元素大，然后比之后元素小，返回i

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
    for(let i = 0; i < nums.length; i++){
        if(nums[i] === target)
            return i;
        else if(target < nums[i] && i === 0)
            return 0;
        else if(target > nums[i] && i === nums.length - 1)
            return nums.length;
        else if(target < nums[i] && target > nums[i - 1])
            return i;
    }
};
```

* 二分查找方式
* 设定两个变量i，j，分别设置两个边界
* 首先判断当前值是否大于整个数组的最大值，如果大于直接返回数组长度
* 然后进行循环，去一个mid作为中间项，然后去进行比较
* 如果这个目标值大于中间值，那么插入数的下标应该比这个数加一，所以i应该等于mid+1
* 如果这个目标值小于中间值，那么插入数的下标应该等于这个数，所以j应该等于mid
* 如果目标值与中间值相等，那么就返回它的下标

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
    let i = 0;
    let j = nums.length - 1;
    if(target > nums[j])
        return j + 1;
    while(i < j){
        let mid = Math.floor((i + j) / 2);
        if(target > nums[mid])
            i = mid + 1;
        else if(target < nums[mid])
            j = mid;
        else
            return mid;
    }
    return i;
};
```

