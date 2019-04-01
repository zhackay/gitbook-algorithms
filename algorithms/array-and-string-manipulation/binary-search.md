# Binary Search

## Tasks

* [ ] Binary Search
* [ ] Search Rotated Array
* [ ] Find Rotated Point
* [ ] Hi/Lo Index
* [ ] MORE ...

## Binary Search

{% tabs %}
{% tab title="Solution" %}
```java
int binarySearch(int a[], int k, int s, int e) {
    int m = s + (e-s)/2;
    
    if (s > e) return -1;
    if (a[m] == k) return m;
    else if (k < a[m]) return binarySearch(a, k, s, m-1);
    else return binarySearch(a, k, m+1, e);
}
```
{% endtab %}

{% tab title="Trivial Knowledge" %}
Find Middle

```java
// given s(tart) and e(nd) of an array
int m = s + (e-s)/2; 

// given an array, a
int m = (a.length - 1) / 2;
/* 
    []        : (0 - 1) / 2 = -1/2 = 0
    [1]       : (1 - 1) / 2 = 0/2 = ?
    [1,2]     : (2 - 1) / 2 = 1/2 = 0
    [1,2,3]   : (3 - 1) / 2 = 2/2 = 1
*/
```
{% endtab %}
{% endtabs %}

{% hint style="warning" %}
 Make sure that even for simple question, clarify. For instance, ...
{% endhint %}

## Search Rotated Array

> [https://www.educative.io/collection/page/5642554087309312/5679846214598656/100002](https://www.educative.io/collection/page/5642554087309312/5679846214598656/100002)

{% tabs %}
{% tab title="Problems" %}
Search for the key k in a sorted, but, rotated array.
{% endtab %}

{% tab title="Clarification" %}
1. Is array sorted?
2. Does it have duplicate values?
{% endtab %}

{% tab title="Hints" %}
binary search
{% endtab %}

{% tab title="Approach" %}
There are 6 cases. 2 base cases. 4 cases for binary search.

Base cases

```java
if (s>e) return -1;
if (a[m] == k) return m;
```

4 cases for binary search

![](../../../.gitbook/assets/1fba3e84-55d1-4c18-8c58-dd9aa6273caa.jpeg)
{% endtab %}

{% tab title="Solution" %}
```java
int binarySearchRotated(int[] a, int k) {
    return binarySearchRotated(a, k, 0, a.length-1);
}

int binarySearchRotated(int[] a, int k, int s, int e) {
    int m = s + (e-s)/2;
    
    if (e < s) return -1;
    if (a[m] == k) return m;
    
    if (a[s] <= k && k < a[m])                      // 1
        return binarySearchRotated(a, k, s, m-1);
    else if (a[m] < k && k <= a[e])                 // 2
        return binarySearchRotated(a, k, m+1, e);
    else if (k <= a[e])                             // 3
        return binarySearchRotated(a, k, m+1, e);
    else if (k >= a[s])                             // 4
        return binarySearchRotated(a, k, s, m-1);

    return -1;
}
```
{% endtab %}
{% endtabs %}

## Find Rotated Point



## Find Lo/Hi Index

