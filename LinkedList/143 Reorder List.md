# 143. Reorder List
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
    public void reorderList(ListNode head) {
        if(head == null || head.next == null) {
    		return;
    	}
    	
    	//found middle 1->2->3->4->5->6->7
    	ListNode front = head;
    	ListNode rear = head;
    	
    	while(rear.next != null && rear.next.next != null) {
    		front = front.next;
    		rear = rear.next.next;
    	}
    	
    	//Reverse behind mid 1->2->3->4->7->6->5
    	ListNode mid = front;
    	ListNode midNext = front.next;
    	while(midNext.next != null) {
    		ListNode next = midNext.next;
    		midNext.next = next.next;
    		next.next = mid.next;
    		mid.next = next;
    	}
    	
    	//Turn to two list and combine it
    	// 1->2->3->4	7->6->5
    	// 1->7->2->6->3->5->4
    	front = head;
    	rear = mid.next;
    	mid.next = null;
    	while(front != null && rear != null) {
    		ListNode FrontNext = front.next;
    		front.next = rear;
    		ListNode RearNext = rear.next;
    		rear.next = FrontNext;
    		front = FrontNext;
    		rear = RearNext;
    	}
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
    public void reorderList(ListNode head) {
        reorderRecursive(head, head);
    	}
    private static ListNode reorderRecursive(ListNode left, ListNode right) {
		if(right == null) {				//even node
			return left;
		}else if(right.next == null) {	//odd node
			ListNode tmp = left.next;
			left.next = null;
			return tmp;
		}
		
		ListNode lead = reorderRecursive(left.next, right.next.next);
		ListNode tmp = lead.next;
		if(left.next == lead) {		//even node
			lead.next = null;
		}else {						//odd node
			tmp = lead.next;
			lead.next = left.next;
			left.next = lead;
		}
		
		return tmp;
	}

}
```
### Time complexity: O(n * log(n))
#### Where n is length of listNode
### Space complexity: O(1)