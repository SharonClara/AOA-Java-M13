# EX 3D Sudoku solver - Backtracking.
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm

1.Scan the grid from left to right, top to bottom to find an empty cell (value 0).

2.If no empty cell is found, the Sudoku is solved — return true.

3.For the empty cell, try placing digits 1 through 9 one by one.

4.For each digit, check if it is safe to place using: Row check, Column check, 3×3 subgrid check

5.If a digit is safe, place it temporarily and recursively try to solve the rest of the board.

6.If recursion fails, remove the digit (backtrack) and try the next number and if all digits fail, return false.

## Program:

Program to implement Reverse a String
## Developed by: SHARON CLARA A
## Register Number: 212224040310 

```

import java.util.Scanner;

public class SudokuSolver {

    
    static boolean isSafe(int[][] board, int row, int col, int num) {
        
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        
        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    
  static boolean solveSudoku(int[][] board, int row, int col) {
        
        if(row == 8 && col==9)
            return true;
        if(col==9){
            row++;
            col=0;
            
        }
        if (board[row][col] !=0)
           return solveSudoku(board,row,col+1);
        for (int num=1;num<=9;num++){
            if(isSafe(board,row,col,num)){
                board[row][col]=num;
                if (solveSudoku(board,row,col+1))
                    return true;
                board [row][col]=0;
            }
        }
        return false;
}

    
    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

      

        for (int i = 0; i < 9; i++) {
           
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }



        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}

```
## Output:


<img width="654" height="589" alt="650878444-876589f9-a794-486b-ad2b-efe1290aa30c" src="https://github.com/user-attachments/assets/938f54b7-b71b-4b9d-b723-e953d49c3bbd" />

## Result:
The program successfully implemented and the expected output is verified.
