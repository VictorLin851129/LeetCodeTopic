# 93. Restore IP Addresses
```
class Solution {
    public List<String> restoreIpAddresses(String s) {
        List<String> retval = new ArrayList<String>();
        if(s.length() < 4 || s.length() > 12) {
        	return Collections.emptyList();
        }
        int subIP = 4;
        subIp(s, "", subIP, retval);
        
        return retval;
    }
    public static void subIp(String s, String ans, int level, List<String> retval) {
    	if(level == 1) {
    		if(Integer.parseInt(s) >= (s.length() == 1 ? 0 : Math.pow(10, s.length() - 1)) && Integer.parseInt(s) <= 255) {
    			retval.add(ans.concat(s));
    		}
    	}else {
    		for(int i = 1; i < s.length() && i <= 3; i++) {
    			if(Integer.parseInt(s.substring(0, i)) >= ((i == 1) ? 0 : Math.pow(10, i - 1)) && Integer.parseInt(s.substring(0, i)) <= 255) {
    				subIp(s.substring(i), ans.concat(s.substring(0, i)).concat("."), level - 1, retval);
    			}
    		}
    	}
    }
}
```