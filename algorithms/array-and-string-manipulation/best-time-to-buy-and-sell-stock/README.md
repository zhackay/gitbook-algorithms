---
description: 'https://leetcode.com/problems/best-time-to-buy-and-sell-stock/'
---

# Best Time to buy and sell stock

{% tabs %}
{% tab title="Problem" %}


{% embed url="https://www.educative.io/collection/page/5642554087309312/5679846214598656/240001" %}
{% endtab %}

{% tab title="Approach" %}
#### Leetcode explanation is good

#### Some observed properties

* need to track 
  * if \(minPrice\) buy  
    * and update minPrice
  * else if \(bestProfit\) sell
    * and update bestProfit
  * current price at index \(= currentPrice - minPrice\)
    * current index is always later than the index of minPrice
  * maxProfit = current\_best\_sell - current\_best\_buy

```text
min = 0;
maxProfit = 0;

for (i : prices) 
    if (prices[i] < prices[min]) 
        min = i
    else if (prices[i] - prices[min] > maxProfit) 
        // currentPrice = prices[i] - prices[min]
        maxProfit = prices[i] - prices[min];

return maxProfit;
```
{% endtab %}

{% tab title="Solution" %}
```java
public int maxProfit(int[] prices) {
    if (prices.length == 0) return 0;
    int minPrice = prices[0];
    int maxProfit = 0;
    
    for (int i=1;i<prices.length;i++) {
        int curProfit = prices[i] - minPrice;
        
        if (prices[i] < minPrice) {
            minPrice = prices[i];
        }
        else if (curProfit > maxProfit) {
            maxProfit = curProfit; 
        }
    }
    return maxProfit;
}
```
{% endtab %}
{% endtabs %}

