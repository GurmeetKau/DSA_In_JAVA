Minimum Falling Path Sum II - LeetCode
code :
class Solution {
    public int minFallingPathSum(int[][] grid) {
       int n = grid.length;
      int[][] dp = new int[n][n];
      for(int col = 0; col<n; col++)
      {
        dp[0][col]=grid[0][col];
      }
      for(int row = 1;row<n;row++)
      {
        for(int col = 0;col<n;col++)
        {
           int minValue = Integer.MAX_VALUE;
           for(int prevRowCol = 0;prevRowCol<n;prevRowCol++)
           {
              if(prevRowCol!=col){
                minValue = Math.min(minValue, dp[row-1][prevRowCol]);
              }
           }
           dp[row][col] = grid[row][col]+minValue;
      }
      }
      int result = Integer.MAX_VALUE;
      for(int col = 0;col<n;col++)
      {
        result = Math.min(result,dp[n-1][col]);
      }
      return result;
    }
}
