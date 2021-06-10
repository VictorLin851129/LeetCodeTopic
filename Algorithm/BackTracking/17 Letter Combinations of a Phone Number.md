# 17. Letter Combinations of a Phone Number
## Solution
```
class Solution {
    String[] map = {"","","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
    public List<String> letterCombinations(String digits) {
        List<String> retval = new ArrayList<String>();
        if(digits.length() == 0){
            return retval;
        }
        helper(digits, 0, retval, "");
		return retval;
    }

	private void helper(String digits, int i, List<String> retval, String BuildRet) {
		if(i == digits.length()) {
			retval.add(BuildRet);
			return;
		}
		String key = map[digits.charAt(i)-'0'];
		for(Character c : key.toCharArray()) {
			helper(digits, i + 1, retval, BuildRet.concat(c.toString()));
		}
		
	}
}
```
### Time complexity: O(4^n)
#### Where n is length of digits
### Space complexity: O(4^n)
#### Where n is length of digits