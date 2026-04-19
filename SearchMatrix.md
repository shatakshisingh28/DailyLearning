# Given a 2D integer array mat[][] and a number x, find whether element x is present in the matrix or not.

## Examples:

Input: mat[][] = [[6, 23, 21],[4, 45, 32],[69, 11, 87]], x = 32

Output: true

Explanation: 32 is present in the matrix, so the output is 1.

``` java
class Solution {
    public boolean searchMatrix(int[][] mat, int x) {
        int n = mat.length;
        int m = mat[0].length;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (mat[i][j] == x) {
                    return true; // found
                }
            }
        }
        return false; // not found
    }
}
```
## Time Complexity: O(n * m)

## Auxiliary Space: O(1)
