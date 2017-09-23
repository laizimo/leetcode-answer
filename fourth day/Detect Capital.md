# Detect Capital

**题目：**



Given a word, you need to judge whether the usage of capitals in it is right or not.

We define the usage of capitals in a word to be right when one of the following cases holds:

1. All letters in this word are capitals, like "USA".
2. All letters in this word are not capitals, like "leetcode".
3. Only the first letter in this word is capital if it has more than one letter, like "Google".

Otherwise, we define that this word doesn't use capitals in a right way.



**翻译：**



给你一个单词，你需要去判断其中大写字母使用是否正确。



当出现以下几种情况的时候，我们可以定义单词中大写的用法是正确的：

1. 单词中所有字母都是大写的，像“USA”。
2. 单词中所有字母都不是大写的，像“leetcode”。
3. 如果单词有多个字母，只有首字母是大写的，像“Google”。

否则，我们就可以判断这个单词没有正确的使用大写字母



**例子：**



```
Input: "USA"
Output: True

Input: "FlaG"
Output: False
```



> 提示：输入的是一个非空的单词



**思路：**



- 最直接的方式，使用正则表达式来进行判断，通过正则表达式分别匹配三种情况



**代码实现：**



```javascript
/**
 * @param {string} word
 * @return {boolean}
 */
var detectCapitalUse = function(word) {
    return /(^[A-Z][a-z]+)|([A-Z]+)|([a-z]+)/.exec(word).indexOf(word) !== -1;
};
```



* 第二种方法就是分别对三种情况进行判断
* 全部大写的情况，将整个单词大写化，与原词进行比较，如果是相等，返回true
* 全部小写的情况，将整个单词小写化，与原词进行比较，如果相等，返回true
* 提取首字母，然后将之后的单词小写化，再拼接之后，再与原词进行比较，如果相等，返回true



**代码实现：**



```javascript
/**
 * @param {string} word
 * @return {boolean}
 */
var detectCapitalUse = function(word) {
    const first = word[0];
    const second = word.slice(1);
    const newWord = first.toUpperCase() + second.toLowerCase();
    if(word.toUpperCase() === word)
        return true;
    else if(word.toLowerCase() == word)
        return true;
    else if(newWord === word)
        return true;
    else
        return false;
};
```

