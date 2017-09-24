# Range Addition II

**题目：**

Given an m * n matrix **M** initialized with all **0**'s and several update operations.

Operations are represented by a 2D array, and each operation is represented by an array with two **positive** integers **a** and **b**, which means **M[i][j]** should be **added by one** for all **0 <= i < a** and **0 <= j < b**. 

You need to count and return the number of maximum integers in the matrix after performing all the operations.

**翻译：**

给一个m*n的矩阵M，其中初始化所有值初始化为0，并且有些更新操作

操作组通过一个二位数组代表，并且每个操作使用两个整数a和b的数组来表示，这就意味着M数组中所有0≤i<a和0≤b<0的元素增加1

你需要去统计，并且返回在所有操作之后，在矩阵中最大整数的个数

**例子：**

```
Input: 
m = 3, n = 3
operations = [[2,2],[3,3]]
Output: 4
Explanation: 
Initially, M = 
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]

After performing [2,2], M = 
[[1, 1, 0],
 [1, 1, 0],
 [0, 0, 0]]

After performing [3,3], M = 
[[2, 2, 1],
 [2, 2, 1],
 [1, 1, 1]]

So the maximum integer in M is 2, and there are four of it in M. So return 4.
```

**思路：**

* 因为它都是从0-a和0-b增加的，所以开头部分的矩阵中的数字一定会增加
* 所以，我们需要去找到操作集合中，横向操作最小的数，和纵向操作最小的数
* 然后，返回这两个数值的 乘积

**代码实现：**

```javascript
/**
 * @param {number} m
 * @param {number} n
 * @param {number[][]} ops
 * @return {number}
 */
var maxCount = function(m, n, ops) {
    let w = m;
    let h = n;
    for(let i = 0; i < ops.length; i++){
        let arr = ops[i];
        if(arr[0] < w){
            w = arr[0];
        }
        if(arr[1] < h){
            h = arr[1];
        }
    }
    return w*h;
};
```

