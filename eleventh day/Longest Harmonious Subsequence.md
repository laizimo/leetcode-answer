# Longest Harmonious Subsequence

**题目：**

We define a harmonious array is an array where the difference between its maximum value and its minimum value is exactly 1.

Now, given an integer array, you need to find the length of its longest harmonious subsequence among all its possible subsequences.

**翻译：**

我们定义一个和谐数组是其中最大元素和最小元素之间的差值是恰好为1

现在，给定一个整数数组，你需要去找到它的最长和谐子集的长度在它所有的可能的子集中

**例子：**

```
Input: [1,3,2,2,5,2,3,7]
Output: 5
Explanation: The longest harmonious subsequence is [3,2,2,2,3].
```

**思路：**

* 首先，我们建立一个map数组
* 统计数组中每个元素的数量
* 然后遍历map中的key值，比较key+1元素是否存在
* 如果存在，去比较key的数量和key+1的数量之和是否大于结果，如果大于赋值给结果

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findLHS = function(nums) {
    const map = new Map();
    let Mcount = 0;
    let arr = [];
    for(let i = 0; i < nums.length; i++){
        if(map.has(nums[i]))
            map.set(nums[i], map.get(nums[i]) + 1);
        else
            map.set(nums[i], 1);
    }
    for(let item of map.keys()){
        if(map.has(item + 1)){
            if(map.get(item) + map.get(item + 1) > Mcount)
                Mcount = map.get(item) + map.get(item + 1);
        }
    }
    return Mcount;
};
```