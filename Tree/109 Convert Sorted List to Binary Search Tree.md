# 109. Convert Sorted List to Binary Search Tree
## Solution
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
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
    public TreeNode sortedListToBST(ListNode head) {
        return arrToBST(head);
    }

	private static TreeNode arrToBST(ListNode start) {
		if(start == null) {
			return null;
		}
		if(start.next == null) {
			return new TreeNode(start.val);
		}
		//find mid
		ListNode front = start;
		ListNode rear = start;
		ListNode pre = null;
		
		while(rear != null && rear.next != null) {
			pre = front;
			front = front.next;
			rear = rear.next.next;
		}
		if(pre != null)
			pre.next = null;
		
		TreeNode root = new TreeNode(front.val);
		root.left = arrToBST(start);
		root.right = arrToBST(front.next);
		
		return root;
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree