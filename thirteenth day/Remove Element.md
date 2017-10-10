# Remove Element

**题目：**

Given an array and a value, remove all instances of that value in place and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**翻译：**

给定一个数组和一个值，移除所有这个值的位置，并且返回一个新的距离

不要为其他数组分配额外的空间。你必须执行在当前的操作下

元素的顺序可以被改变，你留下超过新长度部分是没问题的。

**例子：**

Given input array *nums* = `[3,2,2,3]`, *val* = `3`

Your function should return length = 2, with the first two elements of *nums* being 2.

**思路：**

* 由于不能分配额外的空间，所以在数组上进行操作
* 遍历数组，然后判断当前的元素是否等于给定的元素，如果不等于，则将当前的元素赋给下标为i的元素
* 最终，返回i

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @param {number} val
 * @return {number}
 */
var removeElement = function(nums, val) {
    let i = 0;
    for(let j = 0; j < nums.length; j++){
        if(nums[j] !== val){
            nums[i] = nums[j];
            i++;
        }
    }
    return i;
};
```

