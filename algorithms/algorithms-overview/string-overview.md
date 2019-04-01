---
description: 'https://www.byte-by-byte.com/strings/'
---

# String Overview

## Using a Length-256 Integer Array

![](../../../.gitbook/assets/image%20%2810%29.png)

In case, we need to count the occurrences of each character in a string, the obvious approach might be to use some sort of hashtable or dictionary.

However, we can also use a length-256 array \(let’s assume we’re using ASCII\) where the index in the array represents the ASCII value of the character and the value at that index represents the count. 

Therefore, if we had the string `"aaabb"`, `arr[97] = 3` and `arr[98] = 2`.

Why?

* arrays are a much simpler data structure. That means that the computer can manipulate them much faster and you will improve the efficiency of your code.

Why Not?

* you may be allocating space that you don’t need. 
  * A hashmap only allocates space for the characters present in the string. 
  * However, this is a small price to pay and the array is a relatively small fixed size, so it is usually worth the cost.

#### Anagrams

{% tabs %}
{% tab title="Question" %}
Given two strings, write a function to determine whether they are anagrams.

{% embed url="https://www.byte-by-byte.com/anagrams/" %}

For IDE, [https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)
{% endtab %}

{% tab title="Clarification" %}
1. Does the string contain only alphabetic characters? or Others as well? 
   * _Only Alphabetic characters_
2. _Does 'A' and 'a' regarded as the same, or different?_ 
   * _The same_

\_\_
{% endtab %}

{% tab title="Approaches" %}
1. Approach 1: Sort, then, if same, then, return true, O\(n log n\)\)
2. Approach 2: Count character from s1, remove count from s2, if everything is zero then, true. O\(6n+26\)
{% endtab %}

{% tab title="Solution" %}
Approach 1

```java
boolean isAnagram(String s1, String s2) {
    if (s1.length() != s2.length()) return false;
    char[] c1 = s1.toLowerCase().toCharArray();
    char[] c2 = s2.toLowerCase().toCharArray();
    Arrays.sort(c1); // Java String does not have sort method on its own
    Arrays.sort(c2);
    
    for (int i=0;i<c1.length;i++) {
        if (c1[i] != c2[i]) return false;
    }
    return true;
}
```

Approach 2

```java
boolean isAnagram(String s1, String s2) {
    char[] countArray = new char[26];
    char[] c1 = s1.toLowerCase().toCharArray();
    char[] c2 = s2.toLowerCase().toCharArray();
    for (char c : c1) countArray[c - 97]++;
    for (char c : c2) countArray[c - 97]--;
    for (int i=0;i<26;i++) if (i != 0) return false;
    return true;  
}
```

Note: We don't need to know 97 for 'a', but, just subtract 'a' from integer.

So, this is the better version.

```java
    int[] alphabet = new int[26];
    for (char c : c1) alphabet[c - 'a']++;
    for (char c : c2) alphabet[c - 'a']--;
    for (int i : alphabet) if (i != 0) return false;
    return true;
```
{% endtab %}
{% endtabs %}

#### Sort string of characters

{% tabs %}
{% tab title="Question" %}
Java String class doesn’t have any method that directly sort a string.

Given a string of lowercase characters from ‘a’ – ‘z’. We need to write a program to print the characters of this string in sorted order.

{% embed url="https://www.geeksforgeeks.org/sort-string-characters/" caption="Only look at C++ solution" %}
{% endtab %}

{% tab title="Solution" %}
Standard Java

```java
String sorted(String s) {
    char[] c = s.toCharArray();
    Arrays.sort(c);
    return new String(c);
}
```

Custom using Bucket - O \(n\)

```java
String sorted(String s) {
    char[] alphabet = new char[26];

    for (int i = 0; i < s.length(); i++) {
        alphabet[s.charAt(i) - 'a']++;
    }

    char[] sorted = new char[s.length()];

    int j=0;
    for (int i=0;i<alphabet.length;i++) {
        int cnt = alphabet[i];
        if (cnt > 0) {
            while (cnt-- > 0) {
                sorted[j] = (char) (i + 'a');
                j++;
            }
        }
    }

    return new String(sorted);
}
```
{% endtab %}
{% endtabs %}

#### Longest Substring Without Repeating Characters

{% tabs %}
{% tab title="Question" %}
### [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

Difficulty: **Medium**

Given a string, find the length of the **longest substring** without repeating characters.

**Example 1:**

```text
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3\.
```

**Example 2:**

```text
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```text
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3\. 
    Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
{% endtab %}

{% tab title="Clarification" %}
1. Substring - does it mean it is consecutive \(contiguous\)? 
   * Yes \(it is not subsequence\)
2. 
{% endtab %}

{% tab title="Approach" %}

{% endtab %}

{% tab title="" %}


```java
public int lengthOfLongestSubstring(String str) {
    int s = 0, e = 0, maxLen = 0;
​
    Set<Character> set = new HashSet<>();
    while (s < str.length() && e < str.length()) {
        if (set.contains(str.charAt(e))) {
            set.remove(str.charAt(s++));
        } else {
            set.add(str.charAt(e++));
            if (maxLen < (e - s)) maxLen = e - s;
        }
    }
    return maxLen;
}
```
{% endtab %}
{% endtabs %}

## Using 2 Pointers





## String Math





## String Sliding Windows





## String Comparison, Alignment, and Matching





## Regular Expressions

#### 

#### 

## String Algorithms





## Common String Mistakes





## Common String Problems



