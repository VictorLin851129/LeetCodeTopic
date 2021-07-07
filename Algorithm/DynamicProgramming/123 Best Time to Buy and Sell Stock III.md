# 123. Best Time to Buy and Sell Stock III
## Solution 1: DP
```
class Solution {
    public int maxProfit(int[] prices) {
        // i means at which day; 
    	//j means at which transaction;
    	//dp[i][j] means the max profit with j times transaction till day i
    	//dp[i][j] i means at which day;
    	int[][] dp = new int[3][prices.length]; 
    	
    	//dp[k][i] = Max(dp[k][i - 1], prices[i] - prices[j] + dp[k - 1][j - 1])
    	//we need to find the min = Min(prices[j] - dp[k - 1][j - 1])
    	//then get Max(dp[k][i - 1], prices[i] - min)
    	
    	for(int k = 1; k <= 2; k++) {
    		int min = prices[0];
    		for(int i = 1; i < prices.length; i++) {
    			//int min = prices[0];
//    			for(int j = i; j > 0; j--) {
//    				min = Math.min(min, prices[j] - dp[k - 1][j - 1]);
//    			}
//    			dp[k][i] = Math.max(dp[k][i - 1], prices[i] - min);
    			min = Math.min(min, prices[i] - dp[k - 1][i - 1]);
    			dp[k][i] = Math.max(dp[k][i - 1], prices[i] - min);
    			
    		}
    	}
    	
    	return dp[2][prices.length - 1];
    }
}
```
### Time complexity: O(k * n)
#### Where k is transaction day which is two
#### Where n is length of prices
### Space complexity: O(k * n)
#### Where k is transaction day which is two
#### Where n is length of prices
---
## Solution 2: State machine
```
class Solution {
    public int maxProfit(int[] prices) {
        int Buy1 = Integer.MAX_VALUE, Sold1 = 0,
    			Buy2 = Integer.MAX_VALUE, Sold2 = 0;
    	
    	for(int price : prices) {
    		Buy1 = Math.min(Buy1, price);
    		Sold1 = Math.max(Sold1, price - Buy1);
    		Buy2 = Math.min(Buy2, price - Sold1);
    		Sold2 = Math.max(Sold2, price - Buy2);
    	}
    	
    	return Sold2;
    }
}


```
### Time complexity: O(n)
#### Where n is length of prices
### Space complexity: O(2k)
#### Where k is transaction day which is two