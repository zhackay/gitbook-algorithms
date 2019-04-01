---
description: >-
  http://javabypatel.blogspot.com/2017/10/top-10-matrix-interview-questions-in-java.html
---

# Matrix

```java
int[][] matrix = new int[][] {
    {1,2,3},
    {4,5,6},
    {7,8,9}
};
```

In the above matrix, `matrix[row][col]`

* is actually, `matrix[y][x]` , so, need to be aware!!!

## Rotate Array by 90 degree

{% tabs %}
{% tab title="Problem" %}


```java

```
{% endtab %}

{% tab title="Approach" %}

{% endtab %}

{% tab title="Solution" %}

{% endtab %}

{% tab title="Trivial Knowledge" %}

{% endtab %}
{% endtabs %}

## Print matrix in spiral form

{% tabs %}
{% tab title="problem" %}
### [54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)

Difficulty: **Medium**

Given a matrix of _m_ x _n_ elements \(_m_ rows, _n_ columns\), return all elements of the matrix in spiral order.

**Example 1:**

```text
Input:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
Output: [1,2,3,6,9,8,7,4,5]
```

**Example 2:**

```text
Input:
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
```
{% endtab %}

{% tab title="approach" %}


{% embed url="http://javabypatel.blogspot.com/2016/11/print-matrix-in-spiral-order.html" %}
{% endtab %}

{% tab title="solution" %}


```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {

    }
}
```
{% endtab %}

{% tab title="Trivial Knowledge" %}
When 2d matrix looks like this

```java
int[][] matrix;
/**********************
 [
  [ 1, 2, 3 ],
  [ 4, 5, 6 ],
  [ 7, 8, 9 ]
 ];
***********************/
```

Length of 

* rows

```java
int m = matrix.length;
```

* cols

```java
int n = matrix[0].length;
```

Iterate 

* left to right \(-&gt;\)

```java
// (x...m, y)  
for (int 
```

* top to bottom

```java
// (x, y...n)

```

* right to left \(&lt;-\)

```java
// (m...x, n...y)

```

* bottom to top

```java
// (m...x, n...y)

```

Iterate the whole matrix

* left to right, top to bottom

```text

```

* spiral way - Iteratively

```text

```

* spiral way - Recursively

```text

```

* only right and bottom allowed

```text

```

* only right, bottom and diagonal allowed

```text

```
{% endtab %}
{% endtabs %}



