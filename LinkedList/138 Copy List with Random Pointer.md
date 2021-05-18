# 138. Copy List with Random Pointer
## Solution
```
/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/

class Solution {
    public Node copyRandomList(Node head) {
        HashMap<Node, Node> nodeMap = new HashMap<Node, Node>(); // <Old, New>
    	Node copy = new Node(0);
    	Node copy = new Node(0);
    	Node retval = copy;
    	Node start = head;
    	
    	while(start != null) {
    		copy.next = new Node(start.val);
    		nodeMap.put(start, copy.next);
    		copy = copy.next;
    		start = start.next;
    	}
    	
    	copy = retval;
    	while(head != null) {
    		Node randomNode = nodeMap.get(head.random);
    		copy.next.random = randomNode;
    		copy = copy.next;
    		head = head.next;
    	}
    	
    	return retval.next;
    }
}
```
### Time complexity: O(n)
#### Where n is length of Node
### Space complexity: O(n)
#### Where n is length of Node