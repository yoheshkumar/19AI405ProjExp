# Implement a Sudoku Solver From Scratch
## Steps to solve the Sudoku Puzzle in Python
<ol>
  <li>In this method for solving the sudoku puzzle, first, we assign the size of the 2D matrix to a variable M (M*M).</li>
 <li>Then we assign the utility function (puzzle) to print the grid.</li>
<li>Later it will assign num to the row and col.</li>
<li>If we find the same num in the same row or same column or in the specific 3*3 matrix, ‘false’ will be returned.</li>
<li>Then we will check if we have reached the 8th row and 9th column and return true for stopping further backtracking.</li>
<li>Next, we will check if the column value becomes 9 then we move to the next row and column.</li>
<li>Further now we see if the current position of the grid has a value greater than 0, then we iterate for the next column.</li>
<li>After checking if it is a safe place, we move to the next column and then assign the num in the current (row, col) position of the grid. Later we check for the next possibility with the next column.</li>
<li>As our assumption was wrong, we discard the assigned num and then we go for the next assumption with a different num value</li>
</ol>
<h2>PROGRAM :</h2>

```python
DEVELOPED BY :YOHESH KUMAR R.M
REGISTER NO : 212222240118
```

```python
M = 9
def puzzle(a):
  for i in range(M):
      for j in range(M):
          print(a[i][j],end = " ")
      print()
def solve(grid, row, col, num):
  for x in range(9):
      if grid[row][x] == num:
          return False
           
  for x in range(9):
      if grid[x][col] == num:
          return False


  startRow = row - row % 3
  startCol = col - col % 3
  for i in range(3):
      for j in range(3):
          if grid[i + startRow][j + startCol] == num:
              return False
  return True

def Suduko(grid, row, col):

  if (row == M - 1 and col == M):
      return True
  if col == M:
      row += 1
      col = 0
  if grid[row][col] > 0:
      return Suduko(grid, row, col + 1)
  for num in range(1, M + 1, 1): 
   
      if solve(grid, row, col, num):
       
          grid[row][col] = num
          if Suduko(grid, row, col + 1):
              return True
      grid[row][col] = 0
  return False

'''0 means the cells where no value is assigned'''
grid =  [[2, 5, 0, 0, 3, 0, 9, 0, 1],
        [0, 1, 0, 0, 0, 4, 0, 0, 0],
        [4, 0, 7, 0, 0, 0, 2, 0, 8],
        [0, 0, 5, 2, 0, 0, 0, 0, 0],
        [0, 0, 0, 0, 9, 8, 1, 0, 0],
        [0, 4, 0, 0, 0, 3, 0, 0, 0],
        [0, 0, 0, 3, 6, 0, 0, 7, 2],
        [0, 7, 0, 0, 0, 0, 0, 0, 3],
        [9, 0, 3, 0, 0, 0, 6, 0, 4]]

if (Suduko(grid, 0, 0)):
  puzzle(grid)
else:
  print("Solution does not exist:")
```

<h2>OUTPUT :</h2>

![image](https://github.com/yoheshkumar/19AI405ProjExp/assets/119393568/9b995c4d-734f-418c-acb9-6cf1840d40b4)


<h2>RESULT :</h2>
Thus, a Sudoku solver using the backtracking algorithm is implemented for the given Sudoku puzzle.
