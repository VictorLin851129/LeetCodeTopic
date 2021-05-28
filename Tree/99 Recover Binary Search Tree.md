# 99. Recover Binary Search Tree
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
    TreeNode pre = null;
	TreeNode FirstWrong = null;
	TreeNode SecondWrong = null;
    
    public void recoverTree(TreeNode root) {
        
       inOrderRecover(root);
	   int temp = FirstWrong.val;
	   FirstWrong.val = SecondWrong.val;
	   SecondWrong.val = temp; 
	   
   }
   
   private void inOrderRecover(TreeNode root) {
        if(root == null) {
		   return;
	    }
		inOrderRecover(root.left);
		
		if(pre != null && pre.val >= root.val) {
			if(FirstWrong == null) {
				FirstWrong = pre;
			}
			SecondWrong = root;
		}
		pre = root;
		inOrderRecover(root.right);
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
    public void recoverTree(TreeNode root) {
       Stack<TreeNode> treeStack = new Stack<TreeNode>();
   	
	   TreeNode pre = null;
	   TreeNode FirstWrong = null;
	   TreeNode SecondWrong = null;
	   while(root != null || !treeStack.isEmpty()) {
		   while(root != null) {
			   treeStack.push(root);
			   root = root.left;
		   }
		   root = treeStack.pop();
		   
		   if(pre != null && pre.val >= root.val) {
			   if(FirstWrong == null) {
				   FirstWrong = pre;
			   }
			   SecondWrong = root;
		   }
	
		   pre = root;
		   root = root.right;
	   }
	   
	   int temp = FirstWrong.val;
	   FirstWrong.val = SecondWrong.val;
	   SecondWrong.val = temp;
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree