# Binary Watch

**题目：**

A binary watch has 4 LEDs on the top which represent the hours (0-11), and the 6 LEDs on the bottom represent the minutes (0-59).

Each LED represents a zero or one, with the least significant bit on the right.

![image](https://upload.wikimedia.org/wikipedia/commons/8/8b/Binary_clock_samui_moon.jpg)

For example, the above binary watch reads "3:25".

Given a non-negative integer n which represents the number of LEDs that are currently on, return all possible times the watch could represent.

**翻译：**

一个二进制手表，在顶部有4盏LED灯代表小时(0-11)，并且底部有6盏LED灯代表分钟(0-59)。

每盏LED灯代表一个0或1，右边为最低有效位。

![image](https://upload.wikimedia.org/wikipedia/commons/8/8b/Binary_clock_samui_moon.jpg)

举个例子，上面二进制表可看成"3:25"。

给定一个非负整数n，它代表当前的LED灯的数量，返回所有的表可以表示的时间。

**例子：**

```
Input: n = 1
Return: ["1:00", "2:00", "4:00", "8:00", "0:01", "0:02", "0:04", "0:08", "0:16", "0:32"]
```

**思路：**

* 因为时间是固定的，所以我们可以根据时间循环来判断每个时间点，他们的数字总和是否等于给定的数字
* 写一个得到二进制中1的数量的函数getOneNum()
* 首先循环数字，跳出条件是数字等于0
* 然后判断num与1的值是否为1，如果为1，则count加一
* 然后num右移一位，直到num为0
* 返回count

**代码实现：**

```javascript
/**
 * @param {number} num
 * @return {string[]}
 */
var readBinaryWatch = function(num) {
    const strArr = [];
    for(let hour = 0; hour < 12; hour++){
        for(let minute = 0; minute < 60; minute++){
            if(getOneNum(hour) + getOneNum(minute) === num){
                let str = `${hour}:${minute < 10 ? '0'+minute : minute}`;
                strArr.push(str);
            }
        }
    }
    return strArr;
};

function getOneNum(num){
    let count = 0;
    while(num){
        if(num & 1)
            count++;
        num >>= 1;
    }
    return count;
}
```