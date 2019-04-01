# Reverse

## Tasks

* [ ] **Rotate Array by k**
* [ ] **Reverse Words in a sentence**
* [ ] **MORE ...**

## Rotate Array by k 

{% tabs %}
{% tab title="Example" %}
Rotate Array by K

```text
input: 
    a = [1,2,3,4,5], k = 2 
output:
    a = [4,5,1,2,3]
```
{% endtab %}

{% tab title="Approach" %}
{% hint style="info" %}
Always make sure to do it by hands, first.
{% endhint %}

```text
To satisfy the following
    a = [1,2,3,4,5], k = 2 => a = [4,5,1,2,3]

reverse the first 3, then reverse the next 2
    => [3,2,1][5,4] NOPE!!
    
reverse the whole string, then, reverse the first 2, then, the rest
    => [5,4,3,2,1] 
    => [4,5][1,2,3] YES!!
```
{% endtab %}

{% tab title="Solution" %}
```java
void rotate(int[] a, int k) {     // [1,2,3,4,5], k=2
   reverse(a, 0, a.length - 1);   // [5,4,3,2,1]  - rev whole string
   reverse(a, 0, k-1);            // [4,5][3,2,1] - rev first k  
   reverse(a, k, a.length - 1);   // [4,5][1,2,3]  - rev the rest
}
```
{% endtab %}

{% tab title="Test Cases" %}

{% endtab %}

{% tab title="Trivial Knowledge" %}
```text

```
{% endtab %}
{% endtabs %}

## Reverse Words in a sentence

Medium

{% tabs %}
{% tab title="Example" %}
"Reverse Words in a sentence" =&gt; "sentence a in Words Reverse"
{% endtab %}

{% tab title="Clarification" %}
1. Do I retain the white spaces? What do I do with them?
{% endtab %}

{% tab title="Approach" %}
```text
To Satisfy the following
    "Reverse Words in a sentence" => "sentence a in Words Reverse"

Reverse the whole string
    "ecnetnes a ni sdroW esreveR"
Reverse each word
    "sentence a in Words Reverse"
```
{% endtab %}

{% tab title="Solution" %}
If interviewer says whitespaces should all be truncated

* If interviewer allows built in methods

```java
String reverseWords(String sentence) {       // "Hi little boy"
    String[] words = sentence.split(" ");    // ["Hi", "little", "boy"]
    reverse(words, 0, words.length-1);       // ["boy", "little", "Hi"]
    return String.join(" ", words);          // "boy little Hi"
}
```

* If the interviewer does not allow built in methods

```java
public String reverseWordsWithCleaning(String s) {
    if (s == null) return null;

    char[] a = s.toCharArray();
    int n = a.length;

    // step 1. reverse the whole string
    reverse(a, 0, n - 1);
    // step 2. reverse each word
    reverseWords(a, n);
    // step 3. clean up spaces
    return cleanSpaces(a, n);
}

void reverseWords(char[] a, int n) {
    int i = 0, j = 0;

    while (i < n) {
        while (i < j || i < n && a[i] == ' ') i++; // skip spaces
        while (j < i || j < n && a[j] != ' ') j++; // skip non spaces
        reverse(a, i, j - 1);                      // reverse the word
    }
}

// trim leading, trailing and multiple spaces
String cleanSpaces(char[] a, int n) {
    int i = 0, j = 0;

    while (j < n) {
        while (j < n && a[j] == ' ') j++;             // skip spaces
        while (j < n && a[j] != ' ') a[i++] = a[j++]; // keep non spaces
        while (j < n && a[j] == ' ') j++;             // skip spaces
        if (j < n) a[i++] = ' ';                      // keep only one space
    }

    return new String(a).substring(0, i);
}
```

If interviewer says whitespaces should be retained

```java
public void reverseWords(char[] str) {
    if (str.length <= 1) return;
    reverse(0, str.length-1, str);
    int s = 0, e = 0;

    for (int i=0;i<str.length;i++) {
        if (str[i] == ' ') {
            if (e > s) {
                // word
                reverse(s, e-1, str);
                s = e;
            }
            s++;
        }
        else {
            if (e < s) e = s;
            e++;
        }
    }

    if (e > str.length - 1) reverse(s, e-1, str);
}
```
{% endtab %}

{% tab title="Test Cases" %}

{% endtab %}

{% tab title="Trivial Knowledge" %}
```java
// split string
String[] arrOfStr = str.split("@", 2);
// join string
String gfg1 = String.join(" < ", "Four", "Five", "Six", "Seven"); 
```
{% endtab %}
{% endtabs %}

