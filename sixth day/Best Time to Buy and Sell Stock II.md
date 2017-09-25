# Best Time to Buy and Sell Stock II

**题目：**

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

**翻译：**

据说你有一个数组，里面的第i个元素是当天给予一只股票的价格

设计一个算法去找到最大的利润。你可以完成许多次交易(例如，买一只和卖一只股票，频繁操作很多次)。然而，你只能在相同时间交易多次(你必须保证在你再次买之前卖完股票)

**例子：**

```javascript
Input: [1, 4, 2]

Ouput: 3

解释：因为在第一天你手里有1只1块的股票，在第二天你卖出去，赚了3元，之后的股票没有办法交易

```

**思路：**

* 想要获取最大利益，我们必须保证在股票增长的时候卖出，如果第二天股票降价，在前一天相当于卖出
* 我们可以遍历数组，判断当前元素于之前股票的价格之间的差异，如果为正，就加上收益，否则，就将股票替换

**代码实现：**

```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    let sum = 0;
    let stock = prices[0];
    for(let i = 0; i < prices.length; i++){
        if(prices[i] > stock){
            sum += prices[i] - stock;
            stock = prices[i];
        }else{
            stock = prices[i];
        }
    }
    return sum;
};
```