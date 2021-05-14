# 23. Merge k Sorted Lists
## Solution 1: Divide and Conquer
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
    public ListNode mergeKLists(ListNode[] lists) {
        if(lists.length == 0) {
    		return null;
    	}else if(lists.length == 1) {
    		return lists[0];
    	}
    	int left = 0, right = lists.length - 1;
    	
    	return DivideAndConquer(left, right, lists);
    }
    public static ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    	ListNode start = new ListNode();
    	ListNode retval = start;
    	
    	while(l1 != null || l2 != null) {
    		int l1val = l1 == null ? Integer.MAX_VALUE : l1.val;
    		int l2val = l2 == null ? Integer.MAX_VALUE : l2.val;
    		
    		if(l1val < l2val) {
				ListNode newNode = new ListNode(l1val);
				start.next = newNode;
    			l1 = l1 == null ? null : l1.next;
    		}else {
    			ListNode newNode = new ListNode(l2val);
    			start.next = newNode;
    			l2 = l2 == null ? null : l2.next;
    		}
    		start = start.next;
    	}
    	
        return retval.next;
    }
    
    public static ListNode DivideAndConquer(int left, int right, ListNode[] lists) {
    	if(left == right) {
    		return lists[left];
    	}
        if (left > right) {
            return null;
        }
    	int middle = (left + right)/ 2;
    	
		ListNode l1 = DivideAndConquer(left, middle, lists);
		ListNode l2 = DivideAndConquer(middle + 1, right, lists);
		return mergeTwoLists(l1, l2);
    }
}
```
### Time complexity: O(k * log(n))
#### Where n is length of lists
#### Where k is length of max node in lists[]
### Space complexity: O(m)
#### Where m is all nodes in lists
---
## Solution2: Put to list and sort
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
    public ListNode mergeKLists(ListNode[] lists) {
        ArrayList<Integer> listNotSort = new ArrayList<Integer>();
    	
    	for(int i = 0; i < lists.length; i++) {
    		ListNode temp = lists[i];
    		while(temp != null) {
    			listNotSort.add(temp.val);
    			temp = temp.next;
    		}
    	}
    	
    	Collections.sort(listNotSort);
    	ListNode pointer = new ListNode();
    	ListNode ans = pointer;
    	for(Integer i : listNotSort) {
    		ListNode node = new ListNode(i);
    		pointer.next = node;
    		pointer = pointer.next;
    	}
    	
    	return ans.next;
    }
}
```
### Time complexity: O(k * log(k))
#### Where k is length of max node in lists[]
### Space complexity: O(m)
#### Where m is all nodes in lists
---
## Solution 3: Merge one by one
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
    public ListNode mergeKLists(ListNode[] lists) {
        if(lists.length < 1 || (lists.length == 1 && lists[0] == null)) {
    		return null;
    	}else if(lists.length == 1) {
    		return lists[0];
    	}
    	
    	ListNode ans = mergeTwoLists(lists[0], lists[1]);
    	
    	for(int i = 2; i < lists.length; i++) {
    		ans = mergeTwoLists(ans, lists[i]);
    	}
    	
        return ans;
    }
    
    public static ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    	ListNode start = new ListNode();
    	ListNode retval = start;
    	
    	while(l1 != null || l2 != null) {
    		int l1val = l1 == null ? Integer.MAX_VALUE : l1.val;
    		int l2val = l2 == null ? Integer.MAX_VALUE : l2.val;
    		
    		if(l1val < l2val) {
				ListNode newNode = new ListNode(l1val);
				start.next = newNode;
    			l1 = l1 == null ? null : l1.next;
    		}else {
    			ListNode newNode = new ListNode(l2val);
    			start.next = newNode;
    			l2 = l2 == null ? null : l2.next;
    		}
    		start = start.next;
    	}
    	
        return retval.next;
    }
}
```
### Time complexity: O(k * n)
#### Where n is length of lists
#### Where k is length of max node in lists[]
### Space complexity: O(m)
#### Where m is all nodes in lists