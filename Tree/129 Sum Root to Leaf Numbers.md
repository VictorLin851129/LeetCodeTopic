# 129. Sum Root to Leaf Numbers
## Solution 1: Recursive
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
    public int sumNumbers(TreeNode root) {
        return helper(root, 0);
    }

	private static int helper(TreeNode root, int curTotal) {
		if(root == null) {
			return 0;
		}
		
		if(root.left == null && root.right == null) {
			return curTotal * 10 + root.val;
		}
		
		return helper(root.left, curTotal* 10 + root.val) + helper(root.right, curTotal* 10 + root.val);
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
    public int sumNumbers(TreeNode root) {
        Stack<TreeNode> treeStack = new Stack<TreeNode>();
    	int ans = 0;
    	
    	while(root != null || !treeStack.isEmpty()) {
    		while(root != null) {
    			treeStack.push(root);
    			if(root.left != null) {
    				root.left.val += root.val * 10;
    			}
    			root = root.left;
    		}
    		root = treeStack.pop();
    		if(root.right == null && root.left == null) {
				ans += root.val;
			}else if(root.right != null){
				root.right.val += root.val * 10;
			}
    		root = root.right;
    	}
    	
    	
    	return ans;
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree