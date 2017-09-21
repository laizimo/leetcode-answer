# Reverse Words in a String III

**题目：**



Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.



**翻译：**



给一个字符串，你需要去转换句子中每个单词的字母顺序，而依旧保持空格和原始单词的顺序



**例子：**



```
Input: "Let's take LeetCode contest"
Output: "s'teL ekat edoCteeL tsetnoc"
```



> 在字符串中，每个单词都被空格分开，你不可以增加额外的空格



**思路：**



* 首先将单词以空格为标识拆分成数组
* 然后将数组中的单词逐一转换顺序
* 最后拼接数组，返回字符串



**代码实现：**



```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    const arr = s.split(' ');
    return arr.map(item => [...item].reverse().join('')).join(' ');
};
```

