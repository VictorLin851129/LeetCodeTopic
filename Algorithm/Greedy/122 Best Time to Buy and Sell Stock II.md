# 122. Best Time to Buy and Sell Stock II
## Solution
```
class Solution {
    public int maxProfit(int[] prices) {
        int profit = 0;
    	
    	for(int i = prices.length - 1; i > 0; i--) {
    			profit += prices[i] - prices[i - 1] > 0 ? prices[i] - prices[i - 1]: 0;
    	}
    	
        return profit;
    }
}
```
### Time complexity: O(n)
#### Where n is length of prices
### Space complexity: O(1)