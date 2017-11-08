# Valid Parentheses

**题目：**

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.

**翻译：**

给定一个字符串包含字符集`'('`, `')'`, `'{'`, `'}'`, `'['`和`']'`，判断输入字符是否是有效的。

括号必须以正确的顺序闭合， `"()"` 和 `"()[]{}"` 都是有效的，但是 `"(]"` 和 `"([)]"` 并不是。

**思路：**

* 首先，我们可以使用栈这个数据结构，将（、{、[等字符放入栈中。
* 然后，去判断)、}、]等字符是否与栈中最后一位相匹配，如果匹配的话，将栈中最后一位弹出，不然将这个字符放入栈中。
* 最后，判断栈的长度是否等于0

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const stack = [];
    for(let i = 0; i < s.length; i++) {
        if(s[i] === '(' || s[i] === '{' || s[i] === '['){
            stack.push(s[i]);
            continue;
        }
        if(s[i] === ')' && stack[stack.length - 1] === '(' || s[i] === '}' && stack[stack.length - 1] === '{' || s[i] === ']' && stack[stack.length - 1] === '[')
            stack.pop();
        else
            stack.push(s[i]);
    }
    return stack.length === 0;
};
```

