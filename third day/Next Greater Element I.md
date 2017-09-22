# Next Greater Element I

**题目：**


You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.

The Next Greater Number of a number x in nums1 is the first greater number to its right in nums2. If it does not exist, output -1 for this number.

**翻译：**

给予你两个数组（没有重复）nums1和nums2，其中nums1是nus2的子集。为nums1中的所有元素查找接下来更好的数在nums2数组中相应的位置。

数字x的接下来更大的数是在nums2相对应的位置的右边的第一个比x大的数

**例子：**

```javascript
Input: nums1 = [4,1,2], nums2 = [1,3,4,2].
Output: [-1,3,-1]
Explanation:
    For number 4 in the first array, you cannot find the next greater number for it in the second array, so output -1.
    For number 1 in the first array, the next greater number for it in the second array is 3.
    For number 2 in the first array, there is no next greater number for it in the second array, so output -1.
```

> 解释：
>
> 对于第一个数组中的数字4，你不可以找它在第二个数组中的下一个最大的数字，因此输出-1
> 
> 对于第一个数组中的数字1，在第二个数组中的下一个最大的数字是3
>
> 对于第一个数组中的数字2，在第二个数组中没有下一个最大的数字，因此输出-1

**思路：**

* 遍历第一个数组，以数组中元素为单位
   * 在第二个数组中查找当前元素的下标
   * 然后遍历第二个数组该位置及其之后的元素
   * 判断是否有数字大于当前元素，如果大于，将该数字放入结果数组中，跳出循环；否则，继续，直到最后在结果数组中放入-1
   
```javascript
/**
 * @param {number[]} findNums
 * @param {number[]} nums
 * @return {number[]}
 */
var nextGreaterElement = function(findNums, nums) {
    const res = [];
    for(let item of findNums){
        let index = nums.indexOf(item);
        let found = false;
        for(let i  = index + 1; i < nums.length; i++){
            if(nums[i] > item){
                res.push(nums[i]);
                found = true;
                break;
            }
        }
        if(!found)
            res.push(-1);
    }
    return res;
};
```
