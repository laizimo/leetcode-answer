# Student Attendance Record I

**题目：**

You are given a string representing an attendance record for a student. The record only contains the following three characters:

1. 'A' : Absent.
2. 'L' : Late.
3. 'P' : Present.

A student could be rewarded if his attendance record doesn't contain more than one 'A' (absent) or more than two continuous 'L' (late).

You need to return whether the student could be rewarded according to his attendance record.

**翻译：**

你被给予一个字符串代表一个学生的出勤记录。这个记录只包含三个字符：

1. 'A'：缺席
2. 'L'：迟到
3. 'P'：出席

如果他的出席记录不包含超过1个A或者超过两个连续L，这个同学将被奖励。

你需要根据他的出席记录判断他是否会被奖励。

**例子：**

```
Input: "PPALLP"
Output: True
```

```
Input: "PPALLL"
Output: False
```

**思路：**

* 首先，建立一个对象，对于三个字符进行记录
* 然后对s字符串中的字符的数字进行记录
* 对A的数量进行判断，如果大于1的话，返回false
* 对L的数量进行判断，如果大于2的话，返回false
* 这里需要对L进行特殊处理，因为L需要判断连续的，所以，当前元素不为L时，需要将L的数量置为0
* 遍历完循环之后，返回true

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var checkRecord = function(s) {
    let record = {'A': 0, 'L': 0, 'P': 0};
    for(let i = 0; i < s.length; i++){
        record[s[i]]++;
        if(record['A'] > 1)
            return false;
        if(record['L'] > 2)
            return false;
        if(s[i] !== 'L'){
            record['L'] = 0;
        }
    }
    return true;
};
```