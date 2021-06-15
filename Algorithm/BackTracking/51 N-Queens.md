# 51. N-Queens
## Solution
```
class Solution {
    public List<List<String>> solveNQueens(int n) {
        ArrayList<List<String>> retval = new ArrayList<List<String>>();
        backTracking(0, n, new ArrayList<String>(n), retval);
        return retval;
    }

	private static boolean backTracking(int row, int n, ArrayList<String> subRet, ArrayList<List<String>> retval) {
		if(subRet.size() == n) {
			retval.add(new ArrayList<String>(subRet));
			return true;
		}
		char[] Empty = new char[n];
		for(int s = 0 ; s < n; s++) {
			Empty[s] = '.';
		}
		for(int j = 0; j < n; j++) {
			if(isValid(row, j, subRet)) {
				Empty[j] = 'Q';
				subRet.add(new String(Empty));
				if(!backTracking(row + 1, n, subRet, retval)) {
					Empty[j] = '.';
				}
				subRet.remove(subRet.size() - 1);
			}
		}
		return false;
	}

	private static boolean isValid(int row, int col, ArrayList<String> subAns) {
		int n = subAns.size();
		for(int i = 0; i < n; i++) {
			if(subAns.get(i).charAt(col) == 'Q') {
				return false;
			}
		}
		for(int i = row - 1, j = 1; i >= 0; i--, j++) {
			if(col - j >= 0 && subAns.get(i).charAt(col - j) == 'Q') {
				return false;
			}
			if(col + j < subAns.get(i).length() && subAns.get(i).charAt(col + j) == 'Q') {
				return false;
			}
		}
		return true;
	}
}
```
### Time complexity: O(n!)
#### Where n is given
### Space complexity: O(k)
#### where k is length of solution