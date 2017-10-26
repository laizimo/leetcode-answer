# Arranging Coins

**题目：**

You have a total of *n* coins that you want to form in a staircase shape, where every *k*-th row must have exactly *k* coins.

Given *n*, find the total number of **full** staircase rows that can be formed.

*n* is a non-negative integer and fits within the range of a 32-bit signed integer.

**翻译：**

你拥有一个总计n的硬币去形成一个阶梯式的形状，其中每k层必须满足k个硬币

给定n，找到所形成的满足阶梯式形状的总和

n一定是非负整数，并且适合32位整数

**例子：**

```
n = 5

The coins can form the following rows:
¤
¤ ¤
¤ ¤

Because the 3rd row is incomplete, we return 2.
```

```
n = 8

The coins can form the following rows:
¤
¤ ¤
¤ ¤ ¤
¤ ¤

Because the 4th row is incomplete, we return 3.
```

**思路：**

* 就是去建立一个循环，然后减每次的i，然后当n小于i时，返回i

**代码实现：**

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var arrangeCoins = function(n) {
   for(let i = 1;;i++){
       if(n >= i)
           n -= i;
       else
           return i - 1;
   } 
};
```

