# 92. Reverse Linked List II
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
class Solution {
    public ListNode reverseBetween(ListNode head, int left, int right) {
        if(left == right) {
    		return head;
    	}
    	ListNode startNode = new ListNode(0, head);
    	int start = 1;
    	
    	while(start < left) {
    		startNode = startNode.next;
    		start++;
    	}
    	
    	ListNode previous = null;
    	ListNode current = startNode.next;
    	ListNode next = null;
    	while(left <= right) {
    		next = current.next;
    		current.next = previous;
    		previous = current;
    		current = next;
    		left++;
    	}
    	
    	if(next != null) {
    		startNode.next.next = next;
    	}
    	
    	if(start == 1) {
    		head =  previous;
    	}else {
    		startNode.next = previous;
    	}
    	
		return head;
    }
}
```
### Time complexity: O(n)
#### Where n is length of listNode
### Space complexity: O(1)