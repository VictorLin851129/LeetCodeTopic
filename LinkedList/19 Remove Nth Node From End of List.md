# 19. Remove Nth Node From End of List
## Solution 1
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode frontHead = new ListNode(0, head);
    	ListNode frontNode = frontHead;
    	ListNode rearNode = frontHead;
        
        for(int i = 0; i <= n; i++) {
    		rearNode = rearNode.next;
    	}
    	while(rearNode != null) {
    		rearNode = rearNode.next;
    		frontNode = frontNode.next;
    	}
    	frontNode.next = frontNode.next.next;  
        return frontHead.next;
    }
}
```
### Time complexity: O(n)
#### Where n is length of head
### Space complexity: O(n)
#### Where n is length of head
---
## Solution2
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
    public ListNode removeNthFromEnd(ListNode head, int n) {
       ListNode CountNode = new ListNode();
    	CountNode = head;
    	int count = 1;
    	
    	//Caculate total count in list
    	while(CountNode.next != null) {
    		count++;
    		CountNode = CountNode.next;
    	}

    	int ReplaceIndex = count - n;
    	
    	if(ReplaceIndex == 0) { //Replace first
    		if(count == 1) { //Only one element in head list
    			return null;
    		}else {
    			return head.next;
    		}
    	}else if(ReplaceIndex == count - 1) {	//Replace last index in head
    		ListNode beforeReplace = head;
    		while(beforeReplace.next.next != null) {
    			beforeReplace = beforeReplace.next;
    		}
    		beforeReplace.next = null;
    	}else {	//Replace index is in the middle of head list
    		ListNode beforeReplace = head;
    		while(ReplaceIndex > 1) {
    			beforeReplace = beforeReplace.next;
    			ReplaceIndex--;
    		}
    		beforeReplace.next = beforeReplace.next.next;
    	}
    	
        return head;
    }
}
```
### Time complexity: O(n)
#### Where n is length of head
### Space complexity: O(n)
#### Where n is length of head