# Best Time to Buy and Sell Stock

**题目：**

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

**翻译：**

据说你有一个数组，其中的每个元素是给定股票的价格。

如果你仅仅被允许去完成最多一个交易(例如，买一支和卖一只股票)，设计一个算法去找出最大的收益

**例子：**

```
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
```

```
Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
```

**思路：**

* 首先去找到一个较小的值Nmin，初始化为第一个元素，再设置一个收益的变量
* 然后去循环数组，判断当前元素是否比Nmin小，如果比Nmin小，就将这个元素赋值给Nmin
* 如果当前元素比Nmin大，则去比较他们之间的差值与profit之间的大小
* 如果比profit大的话，则将这个差值赋值给profit

**代码实现：**

```javascript
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    let Nmin = prices[0];
    let profit = 0;
    for(let i = 0; i < prices.length; i++){
        if(prices[i] < Nmin){
            Nmin = prices[i];
        }else if(prices[i] - Nmin > profit){
            profit = prices[i] - Nmin;
        }
    }
    return profit;
};
```