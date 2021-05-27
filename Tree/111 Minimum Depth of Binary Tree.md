# 111. Minimum Depth of Binary Tree
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
    public int minDepth(TreeNode root) {
        if(root == null) {
    		return 0;
    	}else if(root.left == null || root.right == null) {
    		return Math.max(1 + minDepth(root.left), 1 + minDepth(root.right));
    	}
    	
        return Math.min(1 + minDepth(root.left), 1 + minDepth(root.right));
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
class Solution {
    public int minDepth(TreeNode root) {
        Queue<TreeNode> treeQueue = new LinkedList<TreeNode>();
    	treeQueue.add(root);
    	int Depth = 0;
    	
    	while(root != null && !treeQueue.isEmpty()) {
    		int layerNode = treeQueue.size();
    		Depth++;
    		for(int i = 0; i < layerNode; i++) {
	    		root = treeQueue.poll();
	    		if(root.left == null && root.right == null) {
	    			return Depth;
	    		}
	    		if(root.left != null) {
	    			treeQueue.add(root.left);
	    		}
	    		if(root.right != null) {
	    			treeQueue.add(root.right);
	    		}
    		}
    	}
    	
    	return Depth;
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree