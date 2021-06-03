# 114. Flatten Binary Tree to Linked List
## Solution 1: Recursive
```
//**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public void flatten(TreeNode root) {
       if(root == null || (root.left == null && root.right == null)) {
    		return;
    	}

		flatten(root.left);
        flatten(root.right);
        TreeNode temp = root.right;
    	root.right = root.left;
    	root.left = null;
    	TreeNode end = root.right == null ? root : root.right;
    	while(end.right != null) {
    		end = end.right;
    	}
    	end.right = temp;
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(1)
---
## Solution 2: Iterative
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
public void flatten(TreeNode root) {
        if(root == null) {
    		return;
    	}
    	Stack<TreeNode> treeStack = new Stack<TreeNode>();
    	treeStack.push(root);
    	
    	while(!treeStack.isEmpty()) {
    		TreeNode cur = treeStack.pop();
    		if(cur.right != null) {
    			treeStack.push(cur.right);
    		}
    		if(cur.left != null) {
    			treeStack.push(cur.left);
    		}
    		if(!treeStack.isEmpty()) {
    			cur.right = treeStack.peek();
                cur.left = null;
    		}
    		
    	}
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree