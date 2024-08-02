---

# Island Perimeter

This project is part of the ALX Interview preparation series. The goal of this project is to calculate the perimeter of an island represented within a grid (2D matrix) where `1` represents land and `0` represents water.

## Problem Statement

You are given a grid where:
- `0` represents water.
- `1` represents land.
- Each cell is square, with a side length of 1.
- Cells are connected horizontally/vertically (not diagonally).
- The grid is completely surrounded by water.
- There is exactly one island (or nothing).
- The island doesn't have any lakes (water inside that isn't connected to the water surrounding the island).

Your task is to write a function `def island_perimeter(grid):` that returns the perimeter of the island.

## Example

```python
grid = [
    [0, 0, 0, 0, 0, 0],
    [0, 1, 0, 0, 0, 0],
    [0, 1, 0, 0, 0, 0],
    [0, 1, 1, 1, 0, 0],
    [0, 0, 0, 0, 0, 0]
]

print(island_perimeter(grid))  # Output: 12
```

## Requirements

- Allowed editors: `vi`, `vim`, `emacs`
- All your files will be interpreted/compiled on Ubuntu 20.04 LTS using python3 (version 3.8.5)
- All your files should end with a new line
- The first line of all your files should be exactly `#!/usr/bin/python3`
- A `README.md` file, at the root of the folder of the project, is mandatory
- Your code should use the PEP 8 style (version 2.8)
- You are not allowed to import any module
- All modules and functions must be documented
- All your files must be executable

## Approach

### Concepts Covered
- **2D Arrays (Matrices)**: Understanding how to navigate through adjacent cells (horizontally and vertically).
- **Conditional Logic**: Applying conditions to determine whether a cell contributes to the perimeter of the island.
- **Counting Techniques**: Developing a method to count the edges that contribute to the island’s perimeter.
- **Problem-Solving Strategies**: Breaking down the problem into smaller tasks.

### Algorithm
1. **Iterate through each cell** in the grid.
2. For each land cell (`1`), **check its four neighbors** (up, down, left, right).
3. **Increase the perimeter** for each side that is either out of bounds or is water (`0`).
4. **Return the total perimeter** after all cells have been checked.

### Function Definition

```python
def island_perimeter(grid):
    perimeter = 0
    rows = len(grid)
    cols = len(grid[0])
    
    for i in range(rows):
        for j in range(cols):
            if grid[i][j] == 1:
                if i == 0 or grid[i-1][j] == 0:  # Up
                    perimeter += 1
                if i == rows-1 or grid[i+1][j] == 0:  # Down
                    perimeter += 1
                if j == 0 or grid[i][j-1] == 0:  # Left
                    perimeter += 1
                if j == cols-1 or grid[i][j+1] == 0:  # Right
                    perimeter += 1
                    
    return perimeter
```

## Testing

You can test the function using the provided grid example or by creating additional test cases to validate different island shapes and sizes.

```python
if __name__ == "__main__":
    grid = [
        [0, 0, 0, 0],
        [0, 1, 1, 0],
        [0, 1, 1, 0],
        [0, 0, 0, 0]
    ]
    print(island_perimeter(grid))  # Expected output: 8
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


---
