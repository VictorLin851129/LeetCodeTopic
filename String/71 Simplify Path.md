# 71. Simplify Path
```
class Solution {
    public String simplifyPath(String path) {
        String[] str =  path.split("/");
    	Stack<String> strStack = new Stack<String>();
    	
    	for(int i = 1; i < str.length; i++) {
    		if(str[i].equals("..")) {
    			if(strStack.size() != 0) {
    				strStack.pop();
    			}
    		}else if(str[i].equals(".")) {
    			continue;
    		}else if(str[i].length() > 0){
    			strStack.add(str[i]);
    		}
    	}
    	StringBuilder retval = new StringBuilder();
    	
    	for(int i = 0; i < strStack.size(); i++) {
    		retval.append("/");
    		retval.append(strStack.get(i));
    	}
        
        if(strStack.size() == 0){
            retval.append("/");
        }
    	
        return retval.toString();
    }
}
```
### Time complexity: O(n)
#### Where n is length of path
### Space complexity: O(n)
#### Where n is length of path