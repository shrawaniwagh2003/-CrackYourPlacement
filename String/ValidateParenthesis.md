# Valid Parentheses Algorithm

## Problem Statement
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['`, and `']'`, determine if the input string is valid. An input string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

## Algorithm

1. **Initialize a Stack:**
   - Create an empty stack to keep track of opening brackets.

2. **Iterate through Each Character in the String:**
   - If the character is an opening bracket (`'('`, `'{'`, `'['`), push it onto the stack.
   - If the character is a closing bracket (`')'`, `'}'`, `']'`), check the following:
     - The stack should not be empty.
     - The top of the stack should be the corresponding opening bracket.
   - If both conditions are met, pop the top of the stack; otherwise, return `false`.

3. **Final Check:**
   - After the loop, return `true` if the stack is empty, indicating all opening brackets had matching closing brackets in the correct order; otherwise, return `false`.

## Pseudocode

1. Initialize an empty stack.
2. For each character in the string:
   - If it is an opening bracket, push it onto the stack.
   - If it is a closing bracket, check if the stack is not empty and the top of the stack matches the corresponding opening bracket. If true, pop the stack; otherwise, return `false`.
3. After the loop, return `true` if the stack is empty; otherwise, return `false`.

## Code

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();

        for (char ch : s.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                stack.push(ch);
            } else if (!stack.isEmpty() && ((stack.peek() == '(' && ch == ')') || 
                                             (stack.peek() == '{' && ch == '}') || 
                                             (stack.peek() == '[' && ch == ']'))) {
                stack.pop();
            } else {
                return false;
            }
        }

        return stack.isEmpty();
    }
}