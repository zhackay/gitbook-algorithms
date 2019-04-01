# Java

## String

### equals\(\) vs. ==

* == compares the Object pointers to see if two strings are actually the same object.
* equals\(\) compares the value of string object. Thus, **equals\(\) is preferred**.

### Useful String methods

* `length()` – Returns the length of the string
* `charAt(int i)` – Returns the character at index `i`
* **`substring(int i, int j)`** – Returns the substring from `i` to `j` \(inclusive of index `i` and exclusive of index `j`\)
* **`contains(String s)`** – Returns a True if `s` is contained in the string
* **`indexOf(String s)`** – Returns the starting index of the first occurrence of `s`
* **`toCharArray()`** – Converts a string to a character array \(useful if we want to repeatedly modify the string\)
* `toLowerCase()` - Returns lower case version of the string
* Java String does not have sort method on its own. To sort string in java, you should ...

  ```java
  String sort(String s1) {
      char[] c1 = s1.toCharArray();
      Arrays.sort(c1);
      return new String(c1);
  }
  ```

## Arrays



## Collections





