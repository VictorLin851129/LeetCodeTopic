# 93. Restore IP Addresses(BackTacking)
## Solution
```
class Solution {
    public List<String> restoreIpAddresses(String s) {
       if(s.length() < 4 || s.length() > 12) {
    		return Collections.emptyList();
    	}
        ArrayList<String> retval = new ArrayList<String>();
        
		backTracking(s, "", 0, 0, retval);
		
		return retval;
    }

	private static void backTracking(String s, String nowS, int part, int index, ArrayList<String> retval) {
		if(s.length() + 3 == nowS.length() && part == 4) {
			retval.add(nowS);
			return;
		}
		for(int i = index, j = 1; i + j <= s.length() && j <= 3; j++) {
			String subS = s.substring(i, i + j);
			//!s.startsWith("0") && Integer.parseInt(s.substring(0, i)) <= 255
			if((j == 1 || !subS.startsWith("0")) && Integer.parseInt(subS) <= 255) {
				if(part < 3) {
					subS = subS.concat(".");
				}
				backTracking(s, nowS.concat(subS), part + 1, index + j, retval);
				
			}
		}
	}
}
```