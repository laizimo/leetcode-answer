# Intersection of Two Arrays II

**题目：**

Given two arrays, write a function to compute their intersection.

**翻译：**

给定两个数组，写一个函数去求他们的交集

**例子：**

Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2, 2].

**思路：**

* 首先，我们建立一个map表，然后遍历nums1数组
* 对nums1中的元素的数量进行记录
* 然后，遍历nums2数组，去判断map中是否存在当前元素，且值大于0，如果存在，则将这个元素放到交集中，然后该元素的数量减一

**代码实现：**

```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    const map = new Map();
    const inters = [];
    for(let i = 0; i < nums1.length; i++){
        if(map.has(nums1[i]))
            map.set(nums1[i], map.get(nums1[i]) + 1);
        else
            map.set(nums1[i], 1);
    }
    for(let i = 0; i < nums2.length; i++){
        if(map.get(nums2[i])){
            inters.push(nums2[i]);
            map.set(nums2[i], map.get(nums2[i]) - 1);
        }
    }
    return inters;
};
```