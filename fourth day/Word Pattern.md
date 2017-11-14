# Word Pattern

**题目：**

Given a `pattern` and a string `str`, find if `str` follows the same pattern.

Here **follow** means a full match, such that there is a bijection between a letter in `pattern` and a **non-empty** word in `str`.

**翻译：**

给定一个模式和一个字符串str，找寻str是否遵循相同模式。

这里的遵循以事实一个完全的匹配，即在pattern中的一个字符和str中的非空单词相对应。

**例子：**

1. pattern = `"abba"`, str = `"dog cat cat dog"` should return true.
2. pattern = `"abba"`, str = `"dog cat cat fish"` should return false.
3. pattern = `"aaaa"`, str = `"dog cat cat dog"` should return false.
4. pattern = `"abba"`, str = `"dog dog dog dog"` should return false.

**思路：**

* 首先，将str按照空格进行拆分成arr。
* 然后，判断arr的长度和pattern的长度是否相同，如果不相同，返回false
* 之后，设置一个map和一个value的对象，对之后的内容进行映射
* 然后循环pattern，去判断map中对应i的arr单词是否具备一个相同的pattern，如果具备，那么将arr中的对应的i替换成pattern中对应的i
* 如果存在，在判断value中是否出现过pattern[i]，如果出现过，那么，将arr中相应的元素替换成空格
* 如果不存在，那么，将这些内容存入map和value中，然后将arr替换成相应的pattern
* 最后，返回组合的字符串与pattern之间的比较

**代码实现：**

```javascript
/**
 * @param {string} pattern
 * @param {string} str
 * @return {boolean}
 */
var wordPattern = function(pattern, str) {
    const arr = str.split(' ');
    if(arr.length !== pattern.length) return false;
    const map = {};
    const value = {};
    for(let i = 0; i < pattern.length; i++){
        if(map[arr[i]]){
            arr[i] = map[arr[i]];
        }else{
            if(value[pattern[i]]){
                arr[i] = '';
            }else{
                map[arr[i]] = pattern[i];
                value[pattern[i]] = true;
                arr[i] = pattern[i];
            }
        }
    }
    return arr.join('') === pattern;
};
```

