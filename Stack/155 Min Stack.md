# 155. Min Stack
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