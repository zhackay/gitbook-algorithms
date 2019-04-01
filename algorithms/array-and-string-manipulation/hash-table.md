# TwoSum Variance

## TwoSum

{% tabs %}
{% tab title="First Tab" %}
### [1. Two Sum](https://leetcode.com/problems/two-sum/)

Difficulty: **Easy**

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have _**exactly**_ one solution, and you may not use the _same_ element twice.

**Example:**

```text
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
{% endtab %}

{% tab title="Second Tab" %}


```java
int[] twoSum(int[] a, int k) {
    Map<Integer, Integer> map = new HashMap<>();
    
    for (int i=0;i<a.length;i++)
        int target = k - a[i];
        if (map.containsKey(target)) 
            return new int[] {map.get(target), i};
        else
            map.put(a[i], i);
    }
    
    return new int[0]; 
}
```
{% endtab %}
{% endtabs %}

## K Difference Pairs

{% tabs %}
{% tab title="HackerRank" %}
[https://www.hackerrank.com/challenges/pairs/problem](https://www.hackerrank.com/challenges/pairs/problem)

You will be given an array of integers and a target value. Determine the number of pairs of array elements that have a difference equal to a target value.

For example, given an array of \[1, 2, 3, 4\] and a target value of 1, we have three values meeting the condition: 2 - 1 = 1, 3 - 2 = 1, and 4 - 3 = 1 

**Function Description**

Complete the _pairs_ function below. It must return an integer representing the number of element pairs having the required difference.

pairs has the following parameter\(s\):

* _k_: an integer, the target difference
* _arr_: an array of integers

**Input Format**

The first line contains two space-separated integers  and , the size of  and the target value.  
 The second line contains  space-separated integers of the array, arr

**Constraints**

* 2 &lt;= n &lt;= 10

each integer 

*  will be unique

**Output Format**

An integer representing the number of pairs of integers whose difference is 

.

**Sample Input**

```text
5 2  1 5 3 4 2  
```

**Sample Output**

```text
3
```

**Explanation**

There are 3 pairs of integers in the set with a difference of 2: \[5,3\], \[4,2\] and \[3,1\] .
{% endtab %}

{% tab title="Solution" %}
[https://www.geeksforgeeks.org/count-pairs-difference-equal-k/](https://www.geeksforgeeks.org/count-pairs-difference-equal-k/)

```java
int countKDiffPairs(int k, int[] arr) {    
    Set<Integer> set = new HashSet<>();
    for (int a: arr) set.add(a);
    
    int count = 0;
    for (int a: arr) {
        if (set.contains(a - k)) count++;
        if (set.contains(a + k)) count++;
        set.remove(a);
    }
    return count;
}
```
{% endtab %}
{% endtabs %}

## Distinct K Difference Pairs

{% tabs %}
{% tab title="First Tab" %}
### [532. K-diff Pairs in an Array](https://leetcode.com/problems/k-diff-pairs-in-an-array/)

Difficulty: **Easy**

Given an array of integers and an integer **k**, you need to find the number of **unique** k-diff pairs in the array. Here a **k-diff** pair is defined as an integer pair \(i, j\), where **i** and **j** are both numbers in the array and their is **k**.

**Example 1:**

```text
Input: [3, 1, 4, 1, 5], k = 2
Output: 2
Explanation: There are two 2-diff pairs in the array, (1, 3) and (3, 5).Although we have two 1s in the input, we should only return the number of unique pairs.
```

**Example 2:**

```text
Input:[1, 2, 3, 4, 5], k = 1
Output: 4
Explanation: There are four 1-diff pairs in the array, (1, 2), (2, 3), (3, 4) and (4, 5).
```

**Example 3:**

```text
Input: [1, 3, 1, 5, 4], k = 0
Output: 1
Explanation: There is one 0-diff pair in the array, (1, 1).
```

**Note:**

1. The pairs \(i, j\) and \(j, i\) count as the same pair.
2. The length of the array won't exceed 10,000.
3. All the integers in the given input belong to the range: \[-1e7, 1e7\].
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

## Distinct Pairs with Sum

{% tabs %}
{% tab title="First Tab" %}
[https://www.hackerrank.com/challenges/pairs/problem](https://www.hackerrank.com/challenges/pairs/problem)
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}











