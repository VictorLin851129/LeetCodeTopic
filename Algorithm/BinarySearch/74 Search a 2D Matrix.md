# 69. Sqrt(x)
## Solution
```
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int column = matrix[0].length;
        int row = matrix.length;
        
        int rowStart = 0, rowEnd = row - 1;
        int columnStart = 0, columnEnd = column - 1;

        while(rowEnd >= 0 && rowStart <= rowEnd) {
        	int mid = (rowStart + rowEnd) / 2;
        	if(matrix[mid][0] < target) {
        		rowStart = mid + 1;
        	}else if(matrix[mid][0] > target) {
        		rowEnd = mid - 1;
        	}else {
        		rowEnd = mid;
        		break;
        	}
        }

        while(rowEnd >= 0 && columnEnd >= 0 && columnStart <= columnEnd) {
        	int mid = (columnStart + columnEnd) / 2;
        	if(matrix[rowEnd][mid] > target) {
        		columnEnd = mid - 1;
        	}else if(matrix[rowEnd][mid] < target) {
        		columnStart = mid + 1;
        	}else {
        		return true;
        	}
        }
        
        return false;
    }
}
```
### Time complexity: O(log(n))
#### Where n is length of max(row, col)
### Space complexity: O(1)