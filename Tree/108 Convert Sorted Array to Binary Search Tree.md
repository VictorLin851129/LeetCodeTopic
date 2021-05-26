# 108. Convert Sorted Array to Binary Search Tree
## Solution
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
    public TreeNode sortedArrayToBST(int[] nums) {
        int start = 0;
    	int end = nums.length - 1;
    	
    	return CreateBST(start, end, nums);
    }

	private static TreeNode CreateBST(int start, int end, int[] nums) {
		if(start > end) {
			return null;
		}
		
		int mid = (start + end) / 2;
		TreeNode root = new TreeNode(nums[mid]);
		
		root.left = CreateBST(start, mid - 1, nums);
		root.right = CreateBST(mid + 1, end, nums);
		
		return root;
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree