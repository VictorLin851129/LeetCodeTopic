# 116(117). Populating Next Right Pointers in Each Node
## Solution 1: Recursive
```
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}
    
    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
};
*/

class Solution {
    public Node connect(Node root) {
       helper(root);
    	
		return root;
    }

	private static void helper(Node root) {
		if(root == null || (root.left == null && root.right == null)) {
			return;
		}
		
		if(root.left != null && root.right != null) {
			root.left.next = root.right;
		}else if(root.left != null) {	//root.right == null
			root.left.next = findNext(root.next);
		}
		if(root.right != null){							//might right have next
			root.right.next = findNext(root.next);
		}
        
        helper(root.right);
		helper(root.left);
	}

	private static Node findNext(Node root) {
		if(root == null) {
			return null;
		}
		if(root.left != null) {
			return root.left;
		}
		if(root.right != null) {
			return root.right;
		}
		return findNext(root.next);
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(1)
---
## Solution 2: Iterative
```
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node next;

    public Node() {}
    
    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _left, Node _right, Node _next) {
        val = _val;
        left = _left;
        right = _right;
        next = _next;
    }
};
*/

class Solution {
    public Node connect(Node root) {
     Node FirstLeft = new Node(0);
    	Node prior = FirstLeft;
    	Node cur = root;
    	
    	while(cur != null) {
    		if(cur.left != null) {
    			prior.next = cur.left;
    			prior = prior.next;
    		}
    		if(cur.right != null) {
    			prior.next = cur.right;
    			prior = prior.next;
    		}
    		if(cur.next != null) {
    			cur = cur.next;
    		}else {
    			cur = FirstLeft.next;
    			FirstLeft.next = null;
    			prior = FirstLeft;
    		}
    	}
    	
		return root;
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(1)