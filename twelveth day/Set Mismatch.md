# Set Mismatch

**题目：**

The set S originally contains numbers from 1 to n. But unfortunately, due to the data error, one of the numbers in the set got duplicated to another number in the set, which results in repetition of one number and loss of another number.

Given an array nums representing the data status of this set after the error. Your task is to firstly find the number occurs twice and then find the number that is missing. Return them in the form of an array.

**翻译：**

一个原始的集合S包含数字从1到n。但是不幸的是，由于数据错误，其中的一个数字被复制到集合中的另一个数字，这导致其中一个数字重复和另一个数字丢失

给定一个数字数组代表了这个发生错误之后的集合。你的任务是先找到那个出现两次的数字和另一个丢失的数字。以数组形式返回它们

**例子：**

```
Input: nums = [1,2,2,4]
Output: [2,3]
```

**思路：**

* 去创建一个n长的数组，然后将数组中的每一位都初始化成0
* 然后去遍历给定的数组nums，将当前元素对应的下标加1，然后去判断结果为是否为2，如果为2，将其放入结果数组
* 循环结束后，查找数组中0的下标，然后将其加一后放入结果数组

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findErrorNums = function(nums) {
    let len = nums.length;
    const res = [];
    const arr = new Array(len);
    for(let i = 0; i < len; i++)
        arr[i] = 0;
    for(let i = 0; i < len; i++){
        arr[nums[i] - 1]++;
        if(arr[nums[i] - 1] === 2)
            res.push(nums[i]);
    }
    let index = arr.indexOf(0);
    res.push(index + 1);
    return res;
};
```