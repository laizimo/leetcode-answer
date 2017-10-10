# Reverse Vowels of a String

**题目：**

Write a function that takes a string as input and reverse only the vowels of a string.

**翻译：**

写一个函数，接收一个字符串作为输入，然后仅翻转字符串中的元音字符

**例子：**

Example 1:
Given s = "hello", return "holle".

Example 2:
Given s = "leetcode", return "leotcede".

**思路：**

* 首先，将字符串转化为数组，然后设置两个变量i和j，分别从0和从s.length - 1开始
* 初始化一个元音对象，将元音字符都置为1
* 然后遍历数组，当碰到两个位置都是元音时，就将他们相互替换，如果只是其中一个为元音，就将其他另一位向后转移一位
* 然后将数组拼接成字符串，返回

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseVowels = function(s) {
    const str = [...s];
    let i = 0;
    let j = s.length - 1;
    const vowal = {a: 1, e: 1, i: 1, o: 1, u: 1, A: 1, E: 1, I: 1, O: 1, U: 1};
    while(i < j){
        if(vowal[str[i]] && vowal[str[j]]){
            let temp = str[j];
            str[j] = str[i];
            str[i] = temp;
        }else if(vowal[str[i]]){
            j--;
            continue;
        }else if(vowal[str[j]]){
            i++;
            continue;
        }
        i++;
        j--;
    }
    return str.join('');
};
```