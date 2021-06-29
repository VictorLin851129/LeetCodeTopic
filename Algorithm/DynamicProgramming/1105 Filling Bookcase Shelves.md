# 1105. Filling Bookcase Shelves
## Solution
```
class Solution {
    public int minHeightShelves(int[][] books, int shelf_width) {
        int[] dp = new int[books.length + 1];
    	
    	for(int i = 1; i <= books.length; i++) {
    		dp[i] = dp[i - 1] + books[i - 1][1];
    		int height = books[i - 1][1];
    		int width = books[i - 1][0];
    		for(int j = i - 1; j > 0 && books[j - 1][0] + width <= shelf_width; j--) {
    			height = Math.max(books[j - 1][1], height);
    			width += books[j - 1][0];
    			//System.out.println((i) + " " + height + " " + dp[j - 1] + " " + j);
    			dp[i] = Math.min(dp[i], dp[j - 1] + height); 
    		}
    	}
    	
    	return dp[books.length];
    }
}
```
### Time complexity: O(n * n)
#### Where n is length of books
### Space complexity: O(n)
#### Where n is length of books