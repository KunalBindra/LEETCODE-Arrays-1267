# LEETCODE-Arrays-1267
### **Breakdown of the Code**

1. **Input:**
   - `grid` is a 2D array where `grid[i][j] == 1` means there is a server at position `(i, j)`.

2. **Initialization:**
   - `n` is the number of rows in the grid.
   - `m` is the number of columns in the grid.
   - Two arrays `indexcolS` and `indexrowS` are used to store the count of servers in each column and row, respectively.

3. **First Pass (Counting Servers in Rows and Columns):**
   - Iterate over each cell of the grid:
     - If `grid[i][j] == 1`, increment the respective row count (`indexrowS[i]`) and column count (`indexcolS[j]`).

4. **Second Pass (Counting Communicable Servers):**
   - Iterate over each cell of the grid again:
     - If the cell contains a server (`grid[row][col] == 1`) and there are more than 1 servers in the same row (`indexrowS[row] > 1`) or more than 1 server in the same column (`indexcolS[col] > 1`), increment the `count`.

5. **Return the Result:**
   - The method returns the total count of servers that can communicate with others.

---

### **Example Dry Run**

#### Input:
```java
int[][] grid = {
    {1, 0},
    {1, 1}
};
```

#### Step 1: Count Servers in Rows and Columns
- `indexrowS = [1, 2]` (Row 0 has 1 server, Row 1 has 2 servers).
- `indexcolS = [2, 1]` (Column 0 has 2 servers, Column 1 has 1 server).

#### Step 2: Count Communicable Servers
- `(0, 0)` → `grid[0][0] == 1` and `indexcolS[0] > 1` → count = 1.
- `(0, 1)` → `grid[0][1] == 0` → not a server.
- `(1, 0)` → `grid[1][0] == 1` and `indexrowS[1] > 1` → count = 2.
- `(1, 1)` → `grid[1][1] == 1` and `indexrowS[1] > 1` → count = 3.

#### Output:
```java
3
```

---

### **Key Points**
- **Time Complexity:** \(O(n \times m)\)
  - First pass: \(O(n \times m)\)
  - Second pass: \(O(n \times m)\)
- **Space Complexity:** \(O(n + m)\)
  - Arrays `indexrowS` and `indexcolS`.
