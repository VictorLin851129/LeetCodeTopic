# 210. Course Schedule II
## Solution : BFS
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
### Space complexity: O(V + E)
#### Where V is length of numCourses
#### Where E is length of prerequisites