---
description: 'https://www.coderefer.com/hackland-election-coding-question/'
---

# HackerLand Election



{% tabs %}
{% tab title="Problem" %}
There are n citizens voting in this year’s Hackland election. Each voter writes the name of their chosen candidate on a ballot and places it in a ballot box. The candidate with the highes number of votes win the election; if two or more candidates have the same number of votes, then the tied candidates’ names are ordered alphabetically and the last name wins.



Complete the election Winner function in your editor. It has 1 parameter:L an array of strings, votes, describing the votes in the ballot box. This function must review these votes and return a string representing the name of the winning candidate.



**Constraints**

1&lt;= n &lt;= 10^4 Input Format An array of Strings

Output Format Name of the person who has the max votes. If there are multiple people with same number of votes\(max\) then print the last name of the list arranged in dictionary order.



**Input Example:**

5

Vamsi

Krishna

Vamsi

Krishna

Tallapudi



**Output**:

Vamsi
{% endtab %}

{% tab title="Hints" %}
Use Custom Comparator for sorting string alphabetically
{% endtab %}

{% tab title="Solution" %}
```java
String winner(String[] votes) {
    Map<String, Integer> map = new HashMap<>();

    for (String v : votes) {
        if (map.containsKey(v)) {
            map.put(v, map.get(v)+1);
        } else {
            map.put(v, 1);
        }
    }

    List<String> maxList = new ArrayList<>();
    int maxVotes = 0;

    for (Map.Entry<String, Integer> entry : map.entrySet()) {
        int curVotes = entry.getValue();

        if (curVotes > maxVotes) {
            maxList = new ArrayList<>();
            maxList.add(entry.getKey());
            maxVotes = curVotes;
        } else if (curVotes == maxVotes) {
            maxList.add(entry.getKey());
        }
    }

    maxList.sort(new Comparator<String>() {
        @Override
        public int compare(String o1, String o2) {
            int smaller = Math.min(o1.length(), o2.length());

            for (int i=0;i<smaller; i++) {
                if (o1.charAt(i) == o2.charAt(i)) continue;
                else if (o1.charAt(i) > o2.charAt(i)) return 1;
                else if (o1.charAt(i) < o2.charAt(i)) return -1;
            }

            if (o1.length() > o2.length()) return 1;
            if (o1.length() < o2.length()) return -1;

            return 0;
        }
    });

    return maxList.get(0);
}

@DataProvider(name = "testCases")
private Object[][] testCases() {
    return new Object[][]{
            { new String[] {"James", "James", "Jamess", "Jamess"}, "James"},
            { new String[] {"James", "Barbara", "Apple"}, "Apple"},
            { new String[] {"Apple", "Barbara", "James", "Barbara"}, "Barbara"},
            { new String[] {"James"}, "James"},
    };
}

@Test(dataProvider = "testCases")
public void tests(String[] votes, String expected) {
    assertThat(winner(votes)).isEqualTo(expected);
}
```
{% endtab %}
{% endtabs %}

