# 22. Generate Parentheses
## Solution
```
class Solution {
    public List<String> generateParenthesis(int n) {
        ArrayList<String> retval = new ArrayList<String>();
    	
    	backTracking(0, 0, n, "", retval);
    	
    	return retval;
    }

	private static void backTracking(int left, int right, int count, String ans, ArrayList<String> retval) {
		if(left > count || right > count) {
			return;
		}
		if(left == count && right == count) {
			retval.add(ans);
		}
		backTracking(left + 1, right, count, ans.concat("("), retval);
		if(left > right) {
			backTracking(left, right + 1, count, ans.concat(")"), retval);
		}
	}
}
```
### Time complexity: $$O(\frac{4^n}{ \sqrt[]{n}})$$
#### PS: Catalan(n) = (2n)!/((n+1)!*n!)
### Space complexity:  $$O(\frac{4^n}{ \sqrt[]{n}})$$
