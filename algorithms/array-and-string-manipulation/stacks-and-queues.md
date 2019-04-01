# Stacks and Queues

## Valid Parentheses

{% tabs %}
{% tab title="Problem" %}
## [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

Difficulty: **Easy**

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Example 1:**

```text
Input: "()"
Output: true
```

**Example 2:**

```text
Input: "()[]{}"
Output: true
```

**Example 3:**

```text
Input: "(]"
Output: false
```

**Example 4:**

```text
Input: "([)]"
Output: false
```

**Example 5:**

```text
Input: "{[]}"
Output: true
```
{% endtab %}

{% tab title="Hints" %}
Stack

{% hint style="warning" %}
open/closing brackets are very confusing
{% endhint %}

{% hint style="danger" %}
always check for emptiness before stack's pop\(\) operation
{% endhint %}
{% endtab %}

{% tab title="Solution" %}
```java
boolean isValid(String s) {
    if (s.length() == 0) return true;

    Stack<Character> stk = new Stack<>();
    stk.push(s.charAt(0));
    
    for (int i=1; i<s.length(); i++) {
        char bracket = s.charAt(i);

        if (isOpening(bracket))
            stk.push(bracket);
        else {
            // be very careful of doing the pop operation.
            // always check for empty() before doing the op.
            if (stk.empty()) return false;
            if (!isMatching(stk.pop(), bracket)) return false;
        }
    }

    return stk.empty();
}

boolean isMatching(char opening, char closing) {
    Map<Character, Character> map = new HashMap<Character, Character>() {{
        put('}', '{');
        put(']', '[');
        put(')', '(');
    }};
    
    if (!map.containsKey(opening)) return false;
    return map.get(opening) == closing;
    
}
            
boolean isOpening(char c) {
    return c == '{' || c == '[' || c == '('; 
}
```
{% endtab %}
{% endtabs %}

