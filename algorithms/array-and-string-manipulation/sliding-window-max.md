---
description: >-
  Given a large array of integers and a window of size w, find the current
  maximum value in the window as the window slides through the entire array.
---

# Sliding Window Max

{% tabs %}
{% tab title="Problems" %}
#### [239. Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)

Difficulty: **Hard**

Given an array _nums_, there is a sliding window of size _k_ which is moving from the very left of the array to the very right. You can only see the _k_ numbers in the window. Each time the sliding window moves right by one position. Return the max sliding window.

**Example:**

```text
Input: nums = [1,3,-1,-3,5,3,6,7], and k = 3
Output: [3,3,5,5,6,7] 
Explanation: 

Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

**More test cases**

```text
#1 
input: 
[-4,2,-5,3,6], k=3
output:
[2,2,3,6]

#2
input: 
[-4,2,-5,1,-1,6], k=3
output:
[2,2,1,6]
```

**Note:**  
You may assume _k_ is always valid, 1 ≤ k ≤ input array's size for non-empty array.

**Follow up:**  
Could you solve it in linear time?

**Solution**

Language: **Java**

```java
public int[] maxSlidingWindow(int[] nums, int k) {}
```
{% endtab %}

{% tab title="Clarification" %}
1. if windows size is bigger than array size, do we still return the max from the array, or is it an invalid state and throw an exception?
{% endtab %}

{% tab title="Hints" %}
If no clue, try Bruteforce

Then, try using Deque
{% endtab %}

{% tab title="Approach" %}
BruteForce

```text
1. as an initialization, read upto k of an array (with start/end ptr)
    * print max of the window (for loop)
2. read one more (start++, end++)
    * print max of the window (for loop)
3. when end ptr reaches the end of an array
    * print max of the window (for loop)
    * exit    
```

Deque

```text
0. Goal
input: a = [-4,2,-5,1,-1,6], k=3
output:[2,2,1,6]

deque
       front [][][][][][] back

1. Initialize the first window
    1) K=1:read from an array, deque.pushToBack the index of the array  
            front [0] back 
       where a[0] = -4
    2) K=2:read from an array, deque.pushToBack the index of the array (newVal))
            front [0][1] back
       if (curMax < newVal) remove from deque by deque.removeFromFront
           curMax = deque[front] = -3
           newVal = a[1] = 2
            front [1] back 
    3) K=3:repeat the step 2
        read from an array, deque.pushToBack the index of the array (newVal))
            front [1][2] back 
        if (!(curMax < newVal)) don't do anything
           curMax = deque[front] = 2
           newVal = a[1] = -5
            front [1][2] back
    4) When K=3, the first window is done, 
        So, resultArray.add(deque[front]);
2. 
                                
as an initialization, read upto k of an array (with start/end ptr)
    * add the max's index to deque's rear
    * 
    * 
2. read one more (start++, end++)
    * add the max to deque's rear 
        * max = Math.max(max, newVal)
    * if (size > k)
        * print (remove from front)
3. when end ptr reaches the end of an array
    * print (all items in deque)
```
{% endtab %}

{% tab title="Solution" %}

{% endtab %}

{% tab title="Trivial Knowledge" %}
#### Java Deque 

* mm

```text

```
{% endtab %}
{% endtabs %}



