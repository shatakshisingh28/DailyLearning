# Chessboard Cell Color

## Problem Statement

Given the coordinates of a cell on a chessboard in the form of a string `s` (for example, `"a1"`, `"b2"`), determine whether the cell is **Black** or **White**.

The chessboard follows the standard coloring pattern where adjacent cells have opposite colors.

---

## Input Format

- A single string `s` representing the cell coordinates.

## Output Format

- Print `"Black"` if the cell is black.
- Print `"White"` if the cell is white.

---

## Constraints

```text
|s| = 2
```

---

## Example 1

### Input

```text
b2
```

### Output

```text
Black
```

### Explanation

Cell `b2` is a black square on the chessboard.

---

## Example 2

### Input

```text
a1
```

### Output

```text
Black
```

### Explanation

Cell `a1` is the bottom-left corner and is black.

---

## Chessboard Representation

```text
      a     b     c     d     e     f     g     h
   +-----+-----+-----+-----+-----+-----+-----+-----+
8  |  W  |  B  |  W  |  B  |  W  |  B  |  W  |  B  |
   +-----+-----+-----+-----+-----+-----+-----+-----+
7  |  B  |  W  |  B  |  W  |  B  |  W  |  B  |  W  |
   +-----+-----+-----+-----+-----+-----+-----+-----+
6  |  W  |  B  |  W  |  B  |  W  |  B  |  W  |  B  |
   +-----+-----+-----+-----+-----+-----+-----+-----+
5  |  B  |  W  |  B  |  W  |  B  |  W  |  B  |  W  |
   +-----+-----+-----+-----+-----+-----+-----+-----+
4  |  W  |  B  |  W  |  B  |  W  |  B  |  W  |  B  |
   +-----+-----+-----+-----+-----+-----+-----+-----+
3  |  B  |  W  |  B  |  W  |  B  |  W  |  B  |  W  |
   +-----+-----+-----+-----+-----+-----+-----+-----+
2  |  W  |  B  |  W  |  B  |  W  |  B  |  W  |  B  |
   +-----+-----+-----+-----+-----+-----+-----+-----+
1  |  B  |  W  |  B  |  W  |  B  |  W  |  B  |  W  |
   +-----+-----+-----+-----+-----+-----+-----+-----+
```

---

## Observation

Assign numerical values to columns:

```text
a=1, b=2, c=3, d=4, e=5, f=6, g=7, h=8
```

Then:

- If `(column + row)` is **even**, the cell is **Black**.
- If `(column + row)` is **odd**, the cell is **White**.

### Examples

| Cell | Column | Row | Sum | Color |
|--------|--------|-----|-----|--------|
| a1 | 1 | 1 | 2 | Black |
| a2 | 1 | 2 | 3 | White |
| b1 | 2 | 1 | 3 | White |
| b2 | 2 | 2 | 4 | Black |

---

## Approach

1. Convert the column character (`a`–`h`) into a number (`1`–`8`).
2. Extract the row number.
3. Calculate:

```text
column + row
```

4. If the sum is even, return `"Black"`.
5. Otherwise, return `"White"`.

---

## Java Solution

```java
import java.util.Scanner;

public class Main {

    public static String determineColor(String s) {

        int col = s.charAt(0) - 'a' + 1;
        int row = s.charAt(1) - '0';

        if ((col + row) % 2 == 0) {
            return "Black";
        } else {
            return "White";
        }
    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        String s = scanner.nextLine().trim();

        System.out.println(determineColor(s));
    }
}
```

---

## Dry Run

### Input

```text
b2
```

### Step 1

```text
Column = 'b'
col = 'b' - 'a' + 1
    = 2
```

### Step 2

```text
Row = '2'
row = 2
```

### Step 3

```text
col + row = 2 + 2 = 4
```

### Step 4

```text
4 % 2 = 0
```

Even ⇒ **Black**

### Output

```text
Black
```

---

## Complexity Analysis

### Time Complexity

```text
O(1)
```

Only a few arithmetic operations are performed.

### Space Complexity

```text
O(1)
```

No extra data structures are used.

---

## Key Insight

A chessboard follows an alternating color pattern. By converting the column letter to a number and checking the parity of:

```text
column + row
```

we can instantly determine the color of any cell.
