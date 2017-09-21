# Keyboard Row

**题目：**



Given a List of words, return the words that can be typed using letters of **alphabet** on only one row's of American keyboard like the image below.



![keyboard](https://leetcode.com/static/images/problemset/keyboard.png)



**翻译：**



给一列单词，返回其中满足只包含了美式键盘中一行的字母的单词。



**输入输出：**



```
Input: ["Hello", "Alaska", "Dad", "Peace"]
Output: ["Alaska", "Dad"]
```



> 1. 你可以使用同一个字母多次
> 2. 你只能够输入字母的字符



**思路：**



首先，定义一个正则表达式

然后，对数组中的单词进行过滤



```javascript
/**
 * @param {string[]} words
 * @return {string[]}
 */
var findWords = function(words) {
    const reg = /[asdfghjkl]+|[qwertyuiop]+|[zxcvbnm]+/;
    return words.filter(item => item.toLowerCase() === reg.exec(item.toLowerCase())[0]);
};
```

