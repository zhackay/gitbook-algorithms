---
description: 'https://leetcode.com/problems/maximum-subarray/'
---

# Max Sum SubArray

{% embed url="https://leetcode.com/problems/maximum-subarray/" %}

{% embed url="https://www.educative.io/collection/page/5642554087309312/5679846214598656/50002" %}

{% tabs %}
{% tab title="Problem" %}
#### [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

Difficulty: **Easy**

Given an integer array `nums`, find the contiguous subarray \(containing at least one number\) which has the largest sum and return its sum.

**Example:**

```text
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

**Follow up:**

If you have figured out the O\(_n_\) solution, try coding another solution using the divide and conquer approach, which is more subtle.
{% endtab %}

{% tab title="Clarification" %}
* Do we also consider an empty array?

  * If yes, then, maxSum of {} = 0

* This is computing the sum, not the max num.
{% endtab %}

{% tab title="Hints" %}
Kadane's algorithm - keep track of

* currentMax
* globalMax

{% hint style="danger" %}
Code Rust explanation is not great. Look at the youtube at "Approach". 
{% endhint %}
{% endtab %}

{% tab title="Approach" %}
### Kadane's algorithms

#### Assumption: 

* empty array is also considered, so, max of {} is 0
  * negative numbers cannot be the max, because, there will always be 0.

#### Idea:

* With a single pass, for each i
  * What is max sum of subarray, ending at i?
* At the end, we compare these sums at each i, and return max of these.

#### Kadane's algorithms

{% embed url="https://www.youtube.com/watch?v=86CQq3pKSUw" caption="Kadane\'s algorithms starts at 3:15" %}

* With the same idea above, Kadane's algorithms is saying that
  * If we know the maxSum for the previous index, then, the maxSum at the current index is either

    * the current element, or

            // A\[i\]

    * the current element + the maxSum for the previous index 

      // A\[i\] + max\_current

    * So, the new max\_current = max of the above two

            // max\(A\[i\], A\[i\] + max\_current\)

  * except the first index. 

    * We will just take the value at the first index for the first maxSum

            // max\_current = max\_global = A\[0\]

  * At each i, compare currentMaxSum \(c\) at current index with the globalMaxSum, then update the globalMaxSum \(g\)

![](../../../.gitbook/assets/image%20%2820%29.png)
{% endtab %}

{% tab title="Solution" %}
```java
int maxSumSubArray(int[] a) {
    if (a.length == 0) return 0; 
    int currentMax = a[0];
    int globalMax = a[0];
    
    for (int i=1; i<a.length; i++) {
        currentMax = Math.max(a[i], a[i] + currentMax);
        if (currentMax > globalMax) globalMax = currentMax;
    }
    
    return globalMax
}
```
{% endtab %}
{% endtabs %}

