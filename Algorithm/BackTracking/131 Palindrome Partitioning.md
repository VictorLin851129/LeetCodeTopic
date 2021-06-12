# 131. Palindrome Partitioning (BackTracking)
## Solution
```
class Solution {
    public List<List<String>> partition(String s) {
       ArrayList<List<String>> retval = new ArrayList<List<String>>();
    	ArrayList<String> subRet = new ArrayList<String>();
    	
    	backTracking(s, subRet, retval);
    	
    	return retval;
    }

	private static void backTracking(String s, ArrayList<String> subRet, ArrayList<List<String>> retval) {
		if(s.equals("")) {
			retval.add(new ArrayList<String>(subRet));
		}
		
		for(int i = 1; i <= s.length(); i++) {
			String temp = s.substring(0, i);
			if(IsPalindrome(temp)) {
				subRet.add(temp);
				backTracking(s.substring(i), subRet, retval);
				subRet.remove(subRet.size() - 1);
			}
		}
		
	}

	private static boolean IsPalindrome(String substring) {
		for(int j = 0, i = substring.length() - 1; i > j; i--, j++) {
			if(substring.charAt(i) != substring.charAt(j)) {
				return false;
			}
		}
		return true;
	}
}
```
### Time complexity: $$O(n*2^n)$$
#### Where n is length of nums(n is copy)
### Space complexity: O(n)
#### Where n is length of nums