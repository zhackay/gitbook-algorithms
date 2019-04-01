---
description: 'https://leetcode.com/problems/merge-two-sorted-lists/'
---

# Merge Two Sorted Linked List

{% tabs %}
{% tab title="Problem" %}
#### [21. Merge Two Sorted ListsCopy](https://leetcode.com/problems/merge-two-sorted-lists/)

Difficulty: **Easy**

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

```text
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

\*\*\*\*
{% endtab %}

{% tab title="Clarification" %}
1. Can I alter the original two lists to merge? or, do I need to create a new merged list?
2. Can two lists have duplicate values?
{% endtab %}

{% tab title="Hint" %}
merge two arrays
{% endtab %}

{% tab title="Solution" %}
**Solution**

Language: **Java**

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    if (l1 == null && l2 == null) return null;
    if (l1 == null) return l2;
    if (l2 == null) return l1;
    
    ListNode head = new ListNode(-1);
    ListNode cur = head;
    
    while (l1 != null && l2 != null) {
        if (l1.val == l2.val) {
            cur.next = l1;
            l1 = l1.next;
            cur = cur.next;
    ​
            cur.next = l2;
            l2 = l2.next;
            cur = cur.next;
        } else if (l1.val < l2.val) {
            cur.next = l1;
            l1 = l1.next;
            cur = cur.next;                
        } else if (l2.val < l1.val) {
            cur.next = l2;
            l2 = l2.next;
            cur = cur.next;     
        }
    }

    if (l1 == null) cur.next = l2;
    else cur.next = l1;
    
    ListNode merged = head.next;
    head = null;
    return merged;
    }
}
```
{% endtab %}
{% endtabs %}

