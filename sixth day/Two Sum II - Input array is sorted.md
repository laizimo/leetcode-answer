# Two Sum II - Input array is sorted

**题目：**

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution and you may not use the same element twice.

**翻译：**

给定一个已经按升序排序过的整数数组，查找两个它的相加等于给定目标数字的数字

twoSum函数应该返回两个数字的下标，其中index1必须小于index2。请注意你返回的答案(含有index1和index2)不能是空的。

**例子：**

```
Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2
```

**思路：**

* 设置两个循环变量，变量i从数组头开始，变量j从数组尾部开始
* 当两个数字之和大于target的时候，j减一
* 当两个数字之和小于target的时候，i加一
* 当两个数字之和等于target的时候，放入结果数组，跳出循环

**代码实现：**

```javascript
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
    let i = 0;
    let j = numbers.length - 1;
    const res = [];
    while(i < j){
        let item1 = numbers[i];
        let item2 = numbers[j];
        if(target - item1 < item2)
            j--;
        else if(target - item1 > item2)
            i++
        else{
            res.push(i+1);
            res.push(j+1);
            break;
        }
    }
    return res;
};
```