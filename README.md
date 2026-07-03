# Backtrack
Leetcode-79

class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans= new ArrayList();
            backtrack(0,nums,new ArrayList<>(),ans);
            return ans;
        }
        private void backtrack(int ind,int[]nums,ArrayList<Integer>path,
        List<List<Integer>>ans){
            if(ind==nums.length){
                ans.add(new ArrayList<>(path));
                return;
            }
            path.add(nums[ind]);
            backtrack(ind+1,nums,path,ans);
            path.remove(path.size()-1);
            backtrack(ind+1,nums,path,ans);
        }
    }




#N-Queen1 -Leetcode -51

import java.util.*;

class Solution {
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> ans = new ArrayList<>();

        char[][] board = new char[n][n];
        for (int i = 0; i < n; i++) {
            Arrays.fill(board[i], '.');
        }

        backtrack(0, board, ans);
        return ans;
    }

    private void backtrack(int row, char[][] board, List<List<String>> ans) {
        int n = board.length;

        if (row == n) {
            ans.add(construct(board));
            return;
        }

        for (int col = 0; col < n; col++) {
            if (isSafe(board, row, col)) {
                board[row][col] = 'Q';

                backtrack(row + 1, board, ans);

                board[row][col] = '.';
            }
        }
    }

    private boolean isSafe(char[][] board, int row, int col) {
        int n = board.length;

        // Check same column
        for (int i = 0; i < row; i++) {
            if (board[i][col] == 'Q')
                return false;
        }

        // Check upper-left diagonal
        for (int i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--) {
            if (board[i][j] == 'Q')
                return false;
        }

        // Check upper-right diagonal
        for (int i = row - 1, j = col + 1; i >= 0 && j < n; i--, j++) {
            if (board[i][j] == 'Q')
                return false;
        }

        return true;
    }

    private List<String> construct(char[][] board) {
        List<String> res = new ArrayList<>();

        for (char[] row : board) {
            res.add(new String(row));
        }

        return res;
    }
}




#Noueen -2 Leetcode-52

import java.util.*;

class Solution {
    private int count = 0;

    public int totalNQueens(int n) {
        char[][] board = new char[n][n];

        for (int i = 0; i < n; i++) {
            Arrays.fill(board[i], '.');
        }

        backtrack(board, 0);
        return count;
    }

    private void backtrack(char[][] board, int row) {
        int n = board.length;

        if (row == n) {
            count++;
            return;
        }

        for (int col = 0; col < n; col++) {
            if (isSafe(board, row, col)) {
                board[row][col] = 'Q';

                backtrack(board, row + 1);

                board[row][col] = '.';
            }
        }
    }

    private boolean isSafe(char[][] board, int row, int col) {
        int n = board.length;

        // Check column
        for (int i = 0; i < row; i++) {
            if (board[i][col] == 'Q')
                return false;
        }

        // Check upper-left diagonal
        for (int i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--) {
            if (board[i][j] == 'Q')
                return false;
        }

        // Check upper-right diagonal
        for (int i = row - 1, j = col + 1; i >= 0 && j < n; i--, j++) {
            if (board[i][j] == 'Q')
                return false;
        }

        return true;
    }
}
