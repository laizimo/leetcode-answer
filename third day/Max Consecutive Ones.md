# Max Consecutive Ones



**题目：**



Given a binary array, find the maximum number of consecutive 1s in this array.



**翻译：**



给予一个二进制数组，查找在数组中最大连续1的数量



**例子：**



```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```



> 解释：第一个两个数字或者最后一个三个数字是连续的1，最大连续1数量是3



> 提示：输入的内容只有0和1



**思路：**

* 设置一个计数器count和一个结果值res


* 遍历数组
  * 如果当前元素是1，那么count加一
  * 如果当前元素是0，那么将res的值与count的值进行比较。如果res小于count，则将count的值赋给res；之后，将count重置
* 结束循环，在对count和res进行一次判断，因为最后一位可能是1



**代码实现：**



```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
    let res = 0;
    let count = 0;
    for(let item of nums){
        if(item){
            count++
        }else{
            if(res < count)
                res = count;
            count = 0;
        }
    }
    if(res < count)
        res = count;
    return res;
};
```

