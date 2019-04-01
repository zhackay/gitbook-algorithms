# Trivial

## Tasks

* [ ] **Swap**
* [ ] **Shuffle**
* [ ] **Reverse String**
* [ ] **Has Duplicate**
* [ ] **Find Min/Max**
* [ ] \*\*\*\*

## Swap

```java
void swap(char[] str, int i, int j) {
    char temp = str[i];
    str[i] = str[j];
    str[j] = temp;
}
```

## Reverse String

```java
void reverse(char[] str) {
    // do I really need to do this? 
    // Ask interviewer as some tend to get irritated by not doing it.
    if (str == null) throw new Exception(""); 
    
    int m = (str.length - 1)/2;
    for (int i=0, j=str.length; i < m; i++, j--) {
        swap(str, i, j);
    } 
}

// even simpler solution
void reverse(char[] str, int i, int j) {
    while (i>j) {
        swap (str, i, j);
    }  
}
```

## HasDuplicate

{% tabs %}
{% tab title="Clarification" %}
Is the array sorted?
{% endtab %}

{% tab title="Solution" %}
```java
boolean hasDuplicate(int[] arr) {
    if (a == null) throw new Exception("");
    
    Set<Integer> set = new HashSet<>();
    for (int a : arr) {
        if (set.contains(a)) return false;
        set.add(a);
    }
    return true;
}
```
{% endtab %}

{% tab title="Trivial Knowledge" %}
```text
// forEach block in Java
for (int a : array) 
```
{% endtab %}
{% endtabs %}



