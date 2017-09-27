# Relative Ranks

**题目：**

Given scores of N athletes, find their relative ranks and the people with the top three highest scores, who will be awarded medals: "Gold Medal", "Silver Medal" and "Bronze Medal".

**翻译：**

给定一组N个运动员的成绩，找到他们相对的排名，并且找到三名将成绩最高的人，授予奖牌："Gold Medal", "Silver Medal" and "Bronze Medal"

**例子：**

```
Input: [5, 4, 3, 2, 1]
Output: ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]
Explanation: The first three athletes got the top three highest scores, so they got "Gold Medal", "Silver Medal" and "Bronze Medal". 
For the left two athletes, you just need to output their relative ranks according to their scores.
```

**思路：**

* 首先，重新定义一个数组，对其进行排序
* 然后遍历原数组，就排序好的数组，对当前的元素进行查找
* 如果下标是0，1，2的元素，替换当前元素为"Gold Medal", "Silver Medal" and "Bronze Medal"
* 然后对于其他的数组元素，都替换他们查找到的下标加一的字符串

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {string[]}
 */
var findRelativeRanks = function(nums) {
    const arr = [...nums];
    arr.sort((item1, item2) => item2 - item1);
    for(let i = 0; i < nums.length; i++){
        let index = arr.indexOf(nums[i]);
        switch(index){
            case 0:
                nums[i] = "Gold Medal";
                break;
            case 1:
                nums[i] = "Silver Medal";
                break;
            case 2:
                nums[i] = "Bronze Medal";
                break;
            default:
                nums[i] = (index + 1).toString();
        }
    }
    return nums;
};
```