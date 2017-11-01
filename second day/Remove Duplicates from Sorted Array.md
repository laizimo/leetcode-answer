# Remove Duplicates from Sorted Array

**题目：**

Given a sorted array, remove the duplicates in place such that each element appear only *once* and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

**翻译：**

给定一个排好序的数组，移除相应位置的重复项即每个元素仅出现一次，并且返回新的长度。

不要分配额外的空间，你必须在当前的内存中进行操作

**例子：**

Given input array *nums* = `[1,1,2]`,

Your function should return length = `2`, with the first two elements of *nums* being `1` and `2` respectively. It doesn't matter what you leave beyond the new length.

**思路：**

* 比较当前元素与之后的元素是否相等，如果相等，移除当前元素，否则，i向后移动一位
* 返回新数组的长度

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    for(let i = 0;i < nums.length - 1;){
        if(nums[i] === nums[i + 1]){
            nums.splice(i, 1);
        }else{
            i++;
        }
    }
    return nums.length;
};
```

