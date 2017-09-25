# Intersection of Two Arrays

**题目：**

Given two arrays, write a function to compute their intersection.

**翻译：**

给予两个数组，写一个函数去计算他们的交集

**例子：**

Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].

> 1. 结果中的每个元素都必须是唯一的  2. 结果中的元素可以是任意数据

**思路：**

> 介绍一下set的两个操作：forEach函数，内部接收一个函数，主要可以用来遍历集合； has函数，可以来判断集合中是否含有当前元素

* 首先，我们可以建立两个根据两个数组建立两个数组。
* 然后，去遍历其中一个集合，然后去判断另一个集合中是否含有这个数字
* 如果含有，则将其放入结果数组中；

**代码实现：**

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
    const set1 = new Set(nums1);
    const set2 = new Set(nums2);
    const res = [];
    set1.forEach(item => {
        if(set2.has(item))
            res.push(item);
    });
    
    return res;
};
```