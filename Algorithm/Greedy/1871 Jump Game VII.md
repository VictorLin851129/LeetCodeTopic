# 1871. Jump Game VII
## Solution
```
class Solution {
    public boolean canReach(String s, int minJump, int maxJump) {
        if(s.length() - 1 == '1') {
    		return false;
    	}
    	Queue<Integer> queue = new LinkedList<Integer>();
    	
    	for(int i = 0; i < s.length(); i++) {
    		if(!queue.isEmpty() && queue.peek() < i - maxJump) {
    			queue.poll();
    		}
    		if(i == 0 || (!queue.isEmpty() && s.charAt(i) == '0' && queue.peek() <= i - minJump)) {
    			if(i == s.length() - 1) {
    				return true;
    			}
    			queue.add(i);
    		}
    	}
    	
        return false;
    }
}
```
### Time complexity: O(n)
#### Where n is length of s
### Space complexity: O(n)
#### Where n is length of s