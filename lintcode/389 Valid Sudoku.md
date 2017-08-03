## [389 Valid Sudoku](http://www.lintcode.com/en/problem/valid-sudoku/#)

##### Description

The Sudoku board could be partially filled, where empty cells are filled with the character `.`.

##### ** Notice

A valid Sudoku board (partially filled) is not necessarily solvable. Only the filled cells need to be validated.

**Example**

The following partially filed sudoku is valid.

![valid-sudoku](/Users/zhangjiachen/Downloads/valid-sudoku.png)

##### Solution

判断每一行每一列每一个小正方形有没有重复数字，有的话返回false，没有则返回true。

```java
class Solution {
    /**
      * @param board: the board
        @return: wether the Sudoku is valid
      */
    public boolean isValidSudoku(char[][] board) {
        for(int i = 0; i < 9; i++){
            HashSet<Character> row = new HashSet<Character>();
            HashSet<Character> col = new HashSet<Character>();
            HashSet<Character> squ = new HashSet<Character>();
            for(int j = 0; j < 9; j++){
                if(board[i][j] != '.' && !row.add(board[i][j])){
                    return false;
                }
                if(board[j][i] != '.' && !col.add(board[j][i])){
                    return false;
                }
                int squ_row = 3*(i/3);
                int squ_col = 3*(i%3);
                if(board[squ_row + j/3][squ_col + j % 3] != '.' && !squ.add(board[squ_row + j/3][squ_col + j % 3])){
                    return false;
                }
            }
        }
        return true;
    }
};
```



