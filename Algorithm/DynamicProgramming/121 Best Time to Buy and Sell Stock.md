# 121. Best Time to Buy and Sell Stock
## Solution
```
class Solution {
    public int maxProfit(int[] prices) {
        int retval = 0;
    	
    	for(int i = 1; i < prices.length; i++) {
    		if(prices[i] > prices[i - 1]) {
    			if(prices[i] - prices[i - 1] > retval) {
    				retval = prices[i] - prices[i - 1];
    			}
    			prices[i] = prices[i - 1];
    		}
    	}
    	
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of prices
### Space complexity: O(1)