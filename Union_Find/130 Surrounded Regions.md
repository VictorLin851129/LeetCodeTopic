# 130. Surrounded Regions (Union Find)
## Solution
```
class Solution {
    class unionFindImpl {
        int[] nodes;
        int[] level;

        unionFindImpl(int n){
            nodes = new int[n];
            level = new int[n];
            for(int i = 0; i < n; i++) {
                nodes[i] = i;
                level[i] = 1;
            }
        }

        void union(int first, int second){
            int firstParent = find(first);
            int secondParent = find(second);

            nodes[firstParent] = secondParent;
        }

        int find(int kids) {
            ArrayList<Integer> changeParents = new ArrayList<Integer>();

            while(kids != nodes[kids]) {
                changeParents.add(kids);
                kids = nodes[kids];
            }

            for(int i : changeParents) {
                nodes[i] = kids;
            }

            return kids;
        }

    }
    
    public void solve(char[][] board) {
        int rowBound = board.length;
    	int colBound = board[0].length;
    	
    	unionFindImpl uf = new unionFindImpl(board.length * board[0].length + 1);
    	//last element is the parent which is safe
    	
    	for(int i = 0; i < rowBound; i++) {
    		for(int j = 0; j < colBound; j++) {
    			if(i == 0 || j == 0 || i == rowBound - 1 || j == colBound - 1 && board[i][j] == 'O') {
    				uf.union(i * colBound + j, rowBound * colBound);
    			}else if(board[i][j] == 'O') {
    				if(board[i][j - 1] == 'O') {
    					uf.union(i * colBound + j, i * colBound + j - 1);
    				}
    				if(board[i][j + 1] == 'O') {
    					uf.union(i * colBound + j, i * colBound + j + 1);
    				}
    				if(board[i - 1][j] == 'O') {
    					uf.union(i * colBound + j, (i - 1) * colBound + j);
    				}
    				if(board[i + 1][j] == 'O') {
    					uf.union(i * colBound + j, (i + 1) * colBound + j);
    				}
    			}
    		}
    	}
    	
    	for(int i = 0; i < rowBound; i++) {
    		for(int j = 0; j < colBound; j++) {
    			if(board[i][j] == 'O' && (uf.find(i * colBound + j) != uf.find(rowBound * colBound))) {
    				board[i][j] = 'X';
    			}
    		}
    	}
    }
}
```
### Time complexity: O(row * col)
### Space complexity: O(row * col)