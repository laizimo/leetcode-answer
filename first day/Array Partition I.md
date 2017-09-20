# Array Partition I

**题目：**



Given an array of **2n** integers, your task is to group these integers into **n** pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.



**翻译：**



给一个2n的整数数组，你的任务是去组织这些整数到n对的整数，例如(a1,b1)，(a2, b2)，…，(an, bn) ,之后每个(ai, bi)的和，为所有1到n尽可能大。



**例子：**



```
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
```



**思路：**



(这一题理解起来不是特别的好)，大致做法就是将数组排序一下，然后取每对的第一个字符



# 代码步骤

* 对数组进行排序
* 循环遍历排序后的数组
* 累加每对的第一个整数



```javascript
/**
*
*@param {number[]} nums
*@return {number}
*/
var arrayPairSum = function (nums) {
    nums.sort((item1, item2) => item1 - item2);
    
  	var sum = 0;
    
  	for(var i = 0; i < nums.length;){
        sum += nums[i];
    }
  	
  	return sum;
}
```



