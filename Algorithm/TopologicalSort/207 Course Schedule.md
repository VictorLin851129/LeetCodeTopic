# 207. Course Schedule
## Solution1 : DFS
```
class Solution {
    static class Graph{
		int vertex;
		ArrayList<ArrayList<Integer>> Edge = null;
		
		Graph(){
		}
		
		Graph(int Vertex){
			this.vertex = Vertex;
			Edge = new ArrayList<ArrayList<Integer>>(Vertex);
			for(int i = 0; i < Vertex; i++) {
				Edge.add(new ArrayList<Integer>());
			}
		}

		public void addEdge(int outGoing, int inComing) {
			Edge.get(outGoing).add(inComing);
		}
		
		
	}
	
	static boolean TropologicalSort(Graph g) {
		boolean[] visited = new boolean[g.vertex];
		
		for(int i = 0; i < g.vertex; i++) {
			if(!visited[i]) {
				if(!TropologicalSortTool(i, new ArrayList<Integer>(), g, visited)) {
					return false;
				}
			}
		}
		return true;
	}
	
	private static boolean TropologicalSortTool(int course, ArrayList<Integer> parents, Graph g, boolean[] visited) {
		visited[course] = true;
		ArrayList<Integer> outGoing = g.Edge.get(course);
		
		parents.add(course);
		
        if(!Collections.disjoint(parents, outGoing)) {
            return false;
        }
		
		for(int element : outGoing) {
			if(!visited[element]) {
				if(!TropologicalSortTool(element, parents, g, visited)) {
					return false;
				}
			}
		}
		parents.remove(parents.size() - 1);

		return true;
	}

    public boolean canFinish(int numCourses, int[][] prerequisites) {
        Graph g = new Graph(numCourses);
		
		for(int[] points : prerequisites) {
			g.addEdge(points[1], points[0]);
		}
		
		return TropologicalSort(g);
    }
}
```
### Time complexity: O(V + E)
#### Where V is length of numCourses
#### Where E is length of prerequisites
### Space complexity: O(V + e)
#### Where V is length of numCourses
#### Where E is length of prerequisites
---
## Solution2 : BFS
```
class Solution {
    class Graph{
		int Vertex;
		ArrayList<ArrayList<Integer>> edge = new ArrayList<ArrayList<Integer>>();
		
		Graph(int vertex){
			this.Vertex = vertex;
			for(int i = 0; i < vertex; i++) {
				edge.add(new ArrayList<Integer>());
			}
		}
		
		void addEdge(int parent, int child) {
			this.edge.get(parent).add(child);
		}
	}
	
	private  boolean TropologicalSort(Graph g) {
		int[] inDegree = new int[g.Vertex];
		Queue<Integer> queue = new LinkedList<Integer>();
		
		for(int i = 0; i < g.edge.size(); i++) {
			for(int kid : g.edge.get(i)) {
				inDegree[kid]++;
			}
		}
		
		for(int i = 0; i < inDegree.length; i++) {
			if(inDegree[i] == 0) {
				queue.add(i);
			}
		}
		
		while(!queue.isEmpty()) {
			int parent = queue.poll();
			for(int kid : g.edge.get(parent)) {
				if(--inDegree[kid] == 0) {
					queue.add(kid);
				}
			}
		}
		
		for(int i : inDegree) {
			if(i != 0) {
				return false;
			}
		}
		
		return true;
	}
    
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        Graph g = new Graph(numCourses);
		
		for(int[] points : prerequisites) {
			g.addEdge(points[1], points[0]);
		}
		
		return TropologicalSort(g);
    }
}
```
### Time complexity: O(V + E)
#### Where V is length of numCourses
#### Where E is length of prerequisites
### Space complexity: O(V + e)
#### Where V is length of numCourses
#### Where E is length of prerequisites