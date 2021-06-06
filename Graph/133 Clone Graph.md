# 133. Clone Graph
## Solution 1: Recursive
```
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;
    public Node() {
        val = 0;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val) {
        val = _val;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val, ArrayList<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}
*/

class Solution {
    HashMap<Node, Node> visited = new HashMap<Node, Node>();
    public Node cloneGraph(Node node) {
       if(node == null) {
    		return null;
    	}
    	
    	if(visited.containsKey(node)) {
    		return visited.get(node);
	    }
    	
    	visited.put(node, new Node(node.val));
    	for(Node n : node.neighbors) {
    		visited.get(node).neighbors.add(cloneGraph(n));
    	}
    	
    	return visited.get(node);
    }
}
```
### Time complexity: O(n)
#### Where n is node of graph
### Space complexity: O(n)
### Where n is node of graph
---
## Solution 2: Iterative
```
/*
// Definition for a Node.
class Node {
    public int val;
    public List<Node> neighbors;
    public Node() {
        val = 0;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val) {
        val = _val;
        neighbors = new ArrayList<Node>();
    }
    public Node(int _val, ArrayList<Node> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
}
*/

class Solution {
    public Node cloneGraph(Node node) {
        if(node == null) {
    		return null;
    	}
        HashMap<Node, Node> nodeAddress = new HashMap<Node, Node>();
    	Queue<Node> nodeQueue = new LinkedList<Node>();
    	ArrayList<Node> visited = new ArrayList<Node>();
    	
    	nodeQueue.add(node);
    	visited.add(node);
    	while(!nodeQueue.isEmpty()) {
    		Node cur = nodeQueue.poll();
    		
    		for(Node n : cur.neighbors) {
    			nodeAddress.put(n, new Node(n.val));
    			if(!visited.contains(n)) {
    				nodeQueue.add(n);
    				visited.add(n);
    			}
    			
    		}
    		nodeAddress.put(node, new Node(node.val));
    	}
    	
    	visited = new ArrayList<Node>();
    	nodeQueue = new LinkedList<Node>();
    	nodeQueue.add(node);
		visited.add(node);
    	while(!nodeQueue.isEmpty()) {
    		Node cur = nodeQueue.poll();
    		for(Node n : cur.neighbors) {
    			nodeAddress.get(cur).neighbors.add(nodeAddress.get(n));
    			
    			if(!visited.contains(n)) {
    				nodeQueue.add(n);
    				visited.add(n);
    			}
    		}
    	}
    	
    	return nodeAddress.get(node);
    }
}
```
### Time complexity: O(n)
#### Where n is node of graph
### Space complexity: O(n)
#### Where n is node of graph