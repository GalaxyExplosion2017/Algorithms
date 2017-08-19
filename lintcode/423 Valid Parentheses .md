## [**423 Valid Parentheses **](http://www.lintcode.com/en/problem/valid-parentheses/#)

##### Description

Given a string containing just the characters `'(', ')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

##### Example

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.

##### Solution

创建一个栈，遍历给定字符串中的每个字符，当前字符为左半边的时，将右半边入栈，若当前字符为右半边括号与当前栈顶出栈字符不相同或者栈为空不能出栈时，返回false；最后若栈为空返回true，若不为空返回false。

```java
public class Solution {
    /**
     * @param s A string
     * @return whether the string is a valid parentheses
     */
    public boolean isValidParentheses(String s) {
        // Write your code here
        Stack<Character> stack = new Stack<Character>();
        for(char c : s.toCharArray()){
            if(c == '(') stack.push(')');
            else if(c == '{') stack.push('}');
            else if(c == '[') stack.push(']');
            else if(stack.isEmpty() || stack.pop() != c) return false;
        }
        return stack.isEmpty();
    }
}
```

