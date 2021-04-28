# 119. Pascal's Triangle II
```
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> ans = new ArrayList<Integer>();
    	ans.add(1);
    	for(int i = 0; i < rowIndex; i++) {
    		for(int j = i; j > 0; j--) {
    			ans.set(j, ans.get(j) + ans.get(j - 1));
    		}
    		ans.add(1);
    	}
    	
        return ans;
    }
}
```
### Time complexity: O(n)
#### Where n is rowIndex
#### Where m is col matrix
### Space complexity: O(n)
#### Where n is rowIndex