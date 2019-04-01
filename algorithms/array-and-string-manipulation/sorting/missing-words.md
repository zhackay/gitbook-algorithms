# Missing Words



{% tabs %}
{% tab title="Problem" %}
Julia and Samantha are playing with strings. Julia has a string S, and Samantha has a string T which is a subsequence of string S. They are trying to find out what words are missing in T. Help Julia and Samantha to solve the problem. List all the missing words in T, such that inserting them at the appropriate positions in T, in the same order, results in the string S.

Constraints 1 &lt;= \|T\| &lt;= \|S\| &lt;= 106, where \|X\| denotes the length of string X. The length of each word will be less than 15.

Function Parameter You are given a function missingWords that takes the strings S and T as its arguments.

Function Return Value Return an array of the missing words.

Sample Input I am using hackerrank to improve programming am hackerrank to improve

Sample Output I using programming Explanation

Missing words are: 1. I  
2. using  
3. programming
{% endtab %}

{% tab title="Solution" %}


```java
List<String> findMissingWords(String[] s, String[] t) throws Exception {
    if (t.length > s.length) throw new Exception("t should be subsequence of s");
    if (t.length == 0) return Arrays.asList(s);

    List<String> missing = new LinkedList<>();
    int i = 0, j = 0;

    while (j < t.length) {
        if (!s[i].equals(t[j])) {
            missing.add(s[i]);
        } else {
            j++;
        }
        i++;
    }

    while (i < s.length) missing.add(s[i++]);

    return missing;
}

@DataProvider(name = "testCases")
private Object[][] testCases() {
    return new Object[][]{
            {new String[] {"I", "know", "hacker", "rank"},
             new String[] {"know", "hacker"},
             Arrays.asList("I", "rank")},
            {new String[] {"I", "know", "hacker", "rank"},
             new String[] {"I", "know", "hacker", "rank"},
             Arrays.asList()}
    };
}

@Test(dataProvider = "testCases")
public void tests(String[] s, String[] t, List<String> expected) throws Exception {
    assertThat(findMissingWords(s, t)).isEqualTo(expected);
}

@Test(expectedExceptions = Exception.class)
public void testE1() throws Exception {
    assertThat(findMissingWords(
            new String[] {},
            new String[] {"I", "know", "hacker", "rank"})).isEqualTo(new LinkedList<>());
}

@Test(expectedExceptions = Exception.class)
public void testE2() throws Exception {
    assertThat(findMissingWords(
            new String[] {"Different"},
            new String[] {"I", "know", "hacker", "rank"})).isEqualTo(new LinkedList<>());
}
```
{% endtab %}
{% endtabs %}

