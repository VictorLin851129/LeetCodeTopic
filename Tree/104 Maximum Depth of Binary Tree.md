# 104. Maximum Depth of Binary Tree
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
    public int maxDepth(TreeNode root) {
        return CalDepth(0, root);
    }
    
    private static int CalDepth(int i, TreeNode root) {
		if(root == null) {
			return i;
		}
		return Math.max(CalDepth(i + 1, root.left), CalDepth(i + 1, root.right));
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree
---
## Solution 2 Iterative
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

class depthIndex{
	int depth;
	TreeNode node;
	
	public depthIndex(int depth, TreeNode root) {
		this.depth = depth;
		this.node = root;
	}
}
class Solution {
    public int maxDepth(TreeNode root) {
        int depth = 0;
    	int ans = 0;
    	Stack<depthIndex> nodeStack = new Stack<depthIndex>();
    	
    	while(root != null || !nodeStack.isEmpty()) {
    		while(root != null) {
    			nodeStack.push(new depthIndex(++depth, root));
    			root = root.left;
    		}
    		depthIndex cur = nodeStack.pop();
    		root = cur.node;
    		depth = cur.depth;
    		if(ans < depth) {
    			ans = depth;
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