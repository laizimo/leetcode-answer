# Judge Route Circle

**题目：**



Initially, there is a Robot at position (0, 0). Given a sequence of its moves, judge if this robot makes a circle, which means it moves back to **the original place**. 



The move sequence is represented by a string. And each move is represent by a character. The valid robot moves are `R` (Right), `L`(Left), `U` (Up) and `D` (down). The output should be true or false representing whether the robot makes a circle.



**翻译：**



最初，在位置(0,0)的位置有一个机器人。给它一个序列移动，判断是否这个机器人做了一个圆，意思是它走回了它最初的位置



这个移动序列通过一个字符串代表。并且每次移动代表一个字符。有效的机器人移动是R(Right)、L(Left)、U(Up)和D(down)。输出应该是true或者false代表着机器人是否做了一个圆



**输入输出**



```
Input: "UD"
Output: true

Input: "LL"
Output: false
```



[题目链接](https://leetcode.com/problems/judge-route-circle/description/)



思路解析：主要判断两个方向上，是否都会到了原点



# 代码步骤



* 分别设定一个水平变量(level)和一个垂直变量(vertical)
* 遍历序列
  * 如果字符等于R：level加一
  * 如果字符等于L：level减一
  * 如果字符等于U：vertical加一
  * 如果字符等于D：vertical减一
* 判断level和vertical是否等于零



```javascript
/**
*@param {string} moves
*@return {boolean}
*/
var judgeCircle = function(moves){
    var level, vertical = 0;
  	 for(var index in moves){
        switch(moves[index]){
          case 'R':
            level += 1;
            break;
          case 'L':
            level -= 1;
            break;
          case 'U':
            vertical += 1;
            break;
          case 'P':
            vertical -= 1;
            break;
          default:
            break;
        }
    }
  	 
    if(level === 0 && vertical === 0)
      	 return true;
    return false;
}
```

