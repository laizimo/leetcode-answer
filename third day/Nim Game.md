# Nim Game

**题目：**

You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.

Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.

For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.

**翻译：**

你们正在和你朋友玩下面的尼姆游戏：在桌上有一堆石头，每次你们其中一个轮流移除1到3个石头。拿掉最后一个石头的那个将会成为赢家。你将第一个开始移石头。

你们两个都是非常聪明的，有最优的游戏策略。写一个函数通过给予石头堆的数量去判断是否你可以打赢这个游戏。

例如，如果石头堆中有4个石头，那么你将不可能赢得这场游戏：无论你移除1，2，3石头，最后一个肯定你的朋友移除

**思路：**

* 首先，找一个基准，这个基准是4
> 举个例子，无论你第一次拿多少，之后的每一轮，你们一定会保持拿走4个，因为如果你的朋友拿走1个，你可以拿3个；他拿2个，你也拿2个；同理，它也是如此，这样就可以判断最终谁赢了
* 因此，只有一种情况是你输的，即该数可以被4整除

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var canWinNim = function(n) {
    return n % 4 == 0 ? false : true;
};
```
