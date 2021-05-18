# 25. Reverse Nodes in k-Group
## Solution 1: Iterative
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
    public ListNode reverseKGroup(ListNode head, int k) {
        ListNode retval = new ListNode(0);
    	ListNode addRetval = retval;
    	
    	ListNode subHead = null;
    	int index = 0;
    	while(head != null && head.next != null) {
    		ListNode sub = new ListNode(head.val);
	    	head = head.next;
	    	subHead = sub;
	    	index = 1;
	    	while(head != null && index < k) {
	    		sub.next = new ListNode(head.val);
	    		head = head.next;
	    		sub = sub.next;
	    		index++;
	    	}
	    	if(head == null && index < k) {
	    		break;
	    	}
	    	addRetval.next = reverseFunc(subHead);
	    	while(addRetval.next != null) {
	    		addRetval = addRetval.next;
	    	}
    	}
    	
    	if(index < k) {
    		addRetval.next = subHead;
    	}
    	
    	if(head != null) {
    		addRetval.next = head;
    	}
    	
		return retval.next;
    }
    
    public static ListNode reverseFunc(ListNode head) {
    	ListNode previous = null;
    	ListNode current = head;
    	ListNode next = null;
    	
    	while(current != null) {
			next = current.next;
			current.next = previous;
			previous = current;
			current = next;
    	}
    	
    	return previous;
    }
}
```
### Time complexity: O(n)
#### Where n is length of listNode
### Space complexity: O(1)
---
## Solution2: Recursive
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
    public ListNode reverseKGroup(ListNode head, int k) {
        if(!checkEnough(head, k)) {
    		return head;
    	}
    	
    	int index = 0;
    	ListNode previous = null;
    	ListNode current = head;
    	ListNode next = null;
    	while(index < k) {
			next = current.next;
			current.next = previous;
			previous = current;
			current = next;
    		index++;
    	}
    	head.next = reverseKGroup(next, k);
    	head = previous;
    	
		return head;
    }
    
    private static boolean checkEnough(ListNode head, int k) {
    	ListNode checkList = head;
		int index = 0;
		while(checkList != null && index < k) {
			checkList = checkList.next;
			index++;
		}
		return index == k;
	}
}
```
### Time complexity: O(n)
#### Where n is length of listNode
### Space complexity: O(n)
#### Where n is length of listNode