# Distribute Candies

**题目：**



Given an integer array with **even** length, where different numbers in this array represent different **kinds** of candies. Each number means one candy of the corresponding kind. You need to distribute these candies **equally** in number to brother and sister. Return the maximum number of **kinds** of candies the sister could gain.



**翻译：**



给一个长度为**偶数**的整数数组，其中不同的数字代表着不同种类的蜡烛。每个数字的代表着相应种类的蜡烛。你需要去均分这些蜡烛给弟弟和姐姐。返回姐姐手中可以获得的最大蜡烛种类的数量



**例子：**



```
Input: candies = [1,1,2,2,3,3]
Output: 3
Explanation:
There are three different kinds of candies (1, 2 and 3), and two candies for each kind.
Optimal distribution: The sister has candies [1,2,3] and the brother has candies [1,2,3], too. 
The sister has three different kinds of candies. 
```



> 解释：数组中有三个不同种类的蜡烛(1, 2, 3)，并且每个种类的蜡烛各2个。
>
> 最优分配：姐姐有蜡烛[1, 2, 3]，弟弟也有蜡烛[1, 2, 3]。姐姐有三个不同种类的蜡烛



**思路：**



* 首先，知道蜡烛中一共有多少种类(数组去重)
* 然后，与之前数组的一半进行比较，去小的那个数
* 使用通俗一点的话讲，就是如果你数组中的种类数大于原数组的一半，那么，我只能分配数组一半的蜡烛给姐姐；那么如果数组中的种类数小于原数组的一半，那么，我就直接讲所有种类的蜡烛都给姐姐



**代码实现：**



```javascript
/**
 * @param {number[]} candies
 * @return {number}
 */
var distributeCandies = function(candies) {
    return Math.min(new Set([...candies]).size, candies.length / 2)
};
```

