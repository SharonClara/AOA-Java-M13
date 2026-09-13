# EX 3B Rat in Maze- Backtracking 
## AIM:
To write a Java program to for given constraints.
here is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1). The ball can go through the empty spaces by rolling up, down, left or right, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.

Given the m x n maze, the ball's start position and the destination, where start = [startrow, startcol] and destination = [destinationrow, destinationcol], return true if the ball can stop at the destination, otherwise return false.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />
Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
Output: true
Explanation: One possible way is : left -> down -> left -> down -> right -> down -> right.


## Algorithm

1.Initialize a visited matrix to track which positions have already been explored.

2.Start DFS from the start position; if the position has already been visited, return false.

3.If the current position is the destination, return true.

4.Mark the current cell as visited.

5.For each of the four directions (up, down, left, right), roll the ball continuously in that direction until it hits a wall or boundary.

6.After the ball stops, recursively apply DFS from this new stopping position; if any path returns true, then a valid path exists. If all fail, return false.
## Program:

Program to implement Reverse a String
## Developed by: SHARON CLARA A
## Register Number: 212224040310 
```
import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        
        int m = sc.nextInt();
        int n = sc.nextInt();

        int[][] maze = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maze[i][j] = sc.nextInt();
            }
        }

       
        int[] start = new int[]{sc.nextInt(), sc.nextInt()};

       
        int[] destination = new int[]{sc.nextInt(), sc.nextInt()};

        Solution sol = new Solution();
        boolean result = sol.hasPath(maze, start, destination);

        System.out.println(result);
    }
}

class Solution {

    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length;
        int n = maze[0].length;
        boolean[][] visit = new boolean[m][n];

        return dfs(m, n, maze, start, destination, visit);
    }

    public boolean dfs(int m, int n, int[][] maze, int[] curr, int[] destination, boolean[][] visit) {
        if (visit[curr[0]][curr[1]]) return false;
        if (curr[0] == destination[0] && curr[1] == destination[1]) return true;

        visit[curr[0]][curr[1]] = true;

        int[][] dirs = {{1,0}, {-1,0}, {0,1}, {0,-1}};
        for (int[] dir : dirs) {
            int x = curr[0];
            int y = curr[1];

            while (x + dir[0] >= 0 && x + dir[0] < m && y + dir[1] >= 0 && y + dir[1] < n && maze[x + dir[0]][y + dir[1]] == 0) {
                x += dir[0];
                y += dir[1];
            }
            if (dfs(m, n, maze, new int[]{x, y}, destination, visit))
                return true;
        }

        return false;
    }
}


```

## Output:

<img width="378" height="543" alt="650877937-3e861203-4b73-48eb-a33d-559e972bab99" src="https://github.com/user-attachments/assets/4350c62a-ea49-4b09-96b6-4b23ef6ce8c2" />



## Result:
The program successfully implemented and the expected output is verified.
