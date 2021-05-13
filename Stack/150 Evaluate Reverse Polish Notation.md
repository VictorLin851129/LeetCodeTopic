# 150. Evaluate Reverse Polish Notation
## Solution 1: Stack
```
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<Integer>();
    	
    	int rear = 0, front = 0;
    	for(String s : tokens) {
    		switch(s) {
    		case "+":
    			rear = stack.pop();
    			front = stack.pop();
    			stack.push(front + rear);	
    			break;
    		case "-":
    			rear = stack.pop();
    			front = stack.pop();
    			stack.push(front - rear);	
    			break;
    		case "*":
    			rear = stack.pop();
    			front = stack.pop();
    			stack.push(front * rear);	
    			break;
    		case "/":
    			rear = stack.pop();
    			front = stack.pop();
    			stack.push(front / rear);	
    			break;
    		default:
    			stack.push(Integer.parseInt(s));	
    		}
    	}
    	
        return stack.pop();
    }
}
```
### Time complexity: O(n)
#### Where n is length tokens
### Space complexity: O(1)
---
## Solution2: Recursive
```
class Solution {
    static int back;
    public int evalRPN(String[] tokens) {
        back = tokens.length - 1;
    	return calculate(tokens);
    }
    
    private static int calculate(String[] tokens) {
		String str = tokens[back--];
		if(str.equals("+") || str.equals("-") || str.equals("*") ||str.equals("/")) {
			int second = calculate(tokens), first = calculate(tokens);
			if(str.equals("+")) {
				return first + second;
			}else if(str.equals("-")) {
				return first - second;
			}else if(str.equals("*")) {
				return first * second;
			}else if(str.equals("/")) {
				return first / second;
			}
		}
		return Integer.parseInt(str);
	}
}
```
### Time complexity: O(n)
#### Where n is length of tokens
### Space complexity: O(1)