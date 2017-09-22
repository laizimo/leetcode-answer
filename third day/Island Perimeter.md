# Island Perimeter

**题目：**

You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

**翻译：**

你将被给予一个由二维整数格子组成的表，其中1代表陆地，0代表水。单元格被水平或者垂直连接。这个格子被水完全围绕，并且这里有一个岛(即，一个或多个连接的单元格)。这个岛没有‘湖’(被岛环绕的，且不与其它相连接的内部水)。一个单元格是一个长度为1的正方形。这个表格是长方形，长度和宽度都不超过100.确定岛的周长

**例子：**

[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]

Answer: 16
Explanation: The perimeter is the 16 yellow stripes in the image below:
![image](https://leetcode.com/static/images/problemset/island.png)

**思路：**

> 分析：最难以判断的是表格的边界，需要去确定那条边界在外部，不然之后计算的时候会导致数组边界越界的过程。判断方法：检查值为1的四周，是否含有0，如果含有0，count加一

* 首先，我们去填充整个矩阵，在其外部填充一圈0
* 循环这个矩阵，去判断值为1的单元格，四边的情况。若含有0，则计数加一
* 最后，返回计数值

**代码实现：**

```javascript
/**
 * @param {number[][]} grid
 * @return {number}
 */
var islandPerimeter = function(grid) {
    let count = 0;
    const row = grid.length;
    const col = grid[0].length;
    const addArr = new Array(col + 2);
    for(let i = 0; i < addArr.length; i++){
        addArr[i] = 0;
    }
    for(let item of grid){
        item.unshift(0);
        item.push(0);
    }
    grid.unshift(addArr);
    grid.push(addArr);
    for(let i = 1; i < grid.length - 1; i++){
        for(let j = 1; j < grid[i].length - 1; j++){
            if(grid[i][j]){
                if(!grid[i - 1][j])
                    count++;
                if(!grid[i + 1][j])
                    count++;
                if(!grid[i][j - 1])
                    count++;
                if(!grid[i][j + 1])
                    count++;
            }
        }
    }
    return count;
};
```




