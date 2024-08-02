To solve the “Island Perimeter” problem, you’ll need to create a function `island_perimeter(grid)` that calculates the perimeter of an island represented in a 2D grid.

### Breakdown of the Problem

1. **Understanding the Grid**:
   - The grid is a list of lists (a 2D array) where `0` represents water and `1` represents land.
   - The grid is surrounded by water, and the island does not contain any lakes.

2. **Perimeter Calculation**:
   - Each land cell (`1`) contributes to the island's perimeter.
   - A land cell can contribute up to 4 edges to the perimeter (top, bottom, left, and right).
   - If a land cell is adjacent to another land cell, the shared edge does not contribute to the perimeter.

### Step-by-Step Approach

1. **Initialize Perimeter**:
   - Start with a perimeter count of 0.

2. **Iterate Through the Grid**:
   - Use nested loops to go through each cell in the grid.

3. **Check Each Cell**:
   - For each cell that contains land (`1`), check its four possible neighbors (up, down, left, right).
   - If a neighboring cell is out of bounds (which means water) or is water (`0`), increase the perimeter by 1 for that edge.

4. **Return the Total Perimeter**:
   - After iterating through all the cells, the total perimeter will be the sum of all the edges contributing to the perimeter.


### Conclusion

This approach efficiently calculates the perimeter by iterating through each cell and checking its neighbors. The time complexity is O(n), where n is the total number of cells in the grid, making it suitable for large grids up to the maximum allowed size (100x100).



---


Sure, let's break down the concepts with examples, full explanations, and expected outputs for each part of the "Island Perimeter" task.

### 1. **2D Arrays (Matrices)**

#### **Accessing and Iterating Over Elements in a 2D Array**

**Example:**
```python
grid = [
    [0, 1, 0],
    [1, 1, 1],
    [0, 1, 0]
]

# Iterate over each row and column to print the elements
for i in range(len(grid)):
    for j in range(len(grid[i])):
        print(f"Element at row {i}, column {j} is: {grid[i][j]}")
```

**Explanation:**
- We have a 3x3 grid represented as a list of lists.
- `len(grid)` gives us the number of rows, and `len(grid[i])` gives us the number of columns for each row.
- The nested loops allow us to access each element in the 2D array.

**Output:**
```
Element at row 0, column 0 is: 0
Element at row 0, column 1 is: 1
Element at row 0, column 2 is: 0
Element at row 1, column 0 is: 1
Element at row 1, column 1 is: 1
Element at row 1, column 2 is: 1
Element at row 2, column 0 is: 0
Element at row 2, column 1 is: 1
Element at row 2, column 2 is: 0
```

### 2. **Conditional Logic**

#### **Determining Whether a Cell Contributes to the Perimeter**

**Example:**
```python
grid = [
    [0, 1, 0],
    [1, 1, 1],
    [0, 1, 0]
]

i, j = 1, 1  # Selecting the cell at row 1, column 1

# Check if cell is on the grid and if it's a land cell
if grid[i][j] == 1:
    perimeter = 0
    # Check the four sides (up, down, left, right)
    if i == 0 or grid[i-1][j] == 0:  # Up
        perimeter += 1
    if i == len(grid) - 1 or grid[i+1][j] == 0:  # Down
        perimeter += 1
    if j == 0 or grid[i][j-1] == 0:  # Left
        perimeter += 1
    if j == len(grid[i]) - 1 or grid[i][j+1] == 0:  # Right
        perimeter += 1
    
    print(f"Perimeter contribution from cell ({i}, {j}): {perimeter}")
```

**Explanation:**
- We are checking if the selected cell at `(1, 1)` contributes to the perimeter.
- The checks include:
  - **Up**: Whether it's the first row or the cell above is water.
  - **Down**: Whether it's the last row or the cell below is water.
  - **Left**: Whether it's the first column or the cell to the left is water.
  - **Right**: Whether it's the last column or the cell to the right is water.

**Output:**
```
Perimeter contribution from cell (1, 1): 0
```

### 3. **Counting Techniques**

#### **Counting the Total Perimeter**

**Example:**
```python
grid = [
    [0, 0, 0, 0],
    [0, 1, 1, 0],
    [0, 1, 1, 0],
    [0, 0, 0, 0]
]

def island_perimeter(grid):
    perimeter = 0
    rows = len(grid)
    cols = len(grid[0])
    
    for i in range(rows):
        for j in range(cols):
            if grid[i][j] == 1:
                # Check each side of the cell
                if i == 0 or grid[i-1][j] == 0:  # Up
                    perimeter += 1
                if i == rows-1 or grid[i+1][j] == 0:  # Down
                    perimeter += 1
                if j == 0 or grid[i][j-1] == 0:  # Left
                    perimeter += 1
                if j == cols-1 or grid[i][j+1] == 0:  # Right
                    perimeter += 1
    return perimeter

print(island_perimeter(grid))
```

**Explanation:**
- This function iterates through each cell of the grid and calculates the perimeter by checking the four neighboring sides of each land cell.
- If a side is water or out of bounds, it adds to the perimeter.

**Output:**
```
8
```

### 4. **Problem-Solving Strategies**

#### **Breaking Down the Problem**

**Steps:**
1. **Identify Land Cells**: Go through each cell in the grid.
2. **Check Neighbors**: For each land cell, check if it is bordered by water or the edge of the grid.
3. **Calculate Contribution**: Each side that is water or out of bounds adds 1 to the perimeter.

**Example:**
Using the same function as above, with another grid:

```python
grid = [
    [1, 1, 1, 0],
    [1, 0, 0, 0],
    [1, 1, 1, 0],
    [0, 0, 0, 0]
]

print(island_perimeter(grid))  # New grid
```

**Explanation:**
- The function is re-used, showing how it handles a different grid configuration.

**Output:**
```
12
```

### 5. **Python Programming Techniques**

#### **Nested Loops and Conditional Statements**

**Example:**
```python
grid = [
    [1, 1, 1, 0],
    [1, 0, 0, 0],
    [1, 1, 1, 0]
]

for i in range(len(grid)):
    for j in range(len(grid[i])):
        if grid[i][j] == 1:
            print(f"Land cell found at ({i}, {j})")
```

**Explanation:**
- Nested loops are used to iterate through each cell of the grid.
- Conditional statements (`if`) are used to check if a cell contains land.

**Output:**
```
Land cell found at (0, 0)
Land cell found at (0, 1)
Land cell found at (0, 2)
Land cell found at (1, 0)
Land cell found at (2, 0)
Land cell found at (2, 1)
Land cell found at (2, 2)
```

### Summary

By understanding and applying these concepts, you can systematically approach the island perimeter problem, ensuring that each land cell’s contribution to the perimeter is accurately calculated. This combination of 2D array manipulation, conditional logic, and counting strategies forms the basis for solving this and similar grid-based problems.
