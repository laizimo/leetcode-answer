# Find All Numbers Disappeared in an Array

**题目：**

Given an array of integers where 1 ≤ a[i] ≤ *n* (*n* = size of array), some elements appear twice and others appear once.

Find all the elements of [1, *n*] inclusive that do not appear in this array.

Could you do it without extra space and in O(*n*) runtime? You may assume the returned list does not count as extra space.



**翻译：**

给你一个整数数组，其中1≤a[i]≤n(n是数组的长度)，一些元素出现两次，其他的出现一次



找出[1,n] 中没有出现过的所有元素



你可以在没有使用额外空间和O(n)的时间复杂度的情况下完成它吗？强调一下返回的列表不属于额外的空间



**例子：**



```
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```



思路：

> 分析：由于时间复杂度要求是O(n)，所以注意循环次数



##### O(n)解法：没有额外空间浪费

* 首先循环整个nums数组
  * 然后循环判断当前元素是否是它的下标加一，然后当前元素减一对应下标的元素是否等于当前元素
    * 如果不满足，就交换两个数
* 再循环数组，然后去判断它的数是否为下标加一的大小，之后，再将不相等的放入结果数组



**代码实现：**



```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
    const res = [];
    for(let i = 0; i < nums.length; i++){
        while(nums[i] !== i + 1 && nums[nums[i] - 1] !== nums[i]){
            let temp = nums[i];
            nums[i] = nums[temp - 1];
            nums[temp - 1] = temp;
        }
    }
    for(let i = 0; i < nums.length; i++){
        if(nums[i] !== i+1){
            res.push(i+1);
        }
    }
    return res;
};
```





##### O(n)解法：需要使用map

* 首先初始化map，将数组长度的map设置为0
* 之后将对应的元素在map中设置为1
* 之后在遍历map，将为0的数字放入结果数组



**代码实现：**



```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
    const map = new Map();
    const res = [];
    for(var i = 1; i <= nums.length; i++){
        map.set(i, 0);
    }
    for(var i = 0; i < nums.length; i++){
        if(!map.get(nums[i]))
            map.set(nums[i], 1);
    }
    for(var i = 1; i <= nums.length; i++){
        if(!map.get(i))
            res.push(i);
    }
    return res;
};
```

