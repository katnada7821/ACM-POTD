# Day-1-[14A-Letter]
## Problem Description

We are given a grid with n rows and m columns. Some cells contain * (shaded), and the rest contain .
We need to find the smallest rectangle that contains all the * cells and print that rectangle.
The rectangle's sides must stay aligned with the rows and columns.
Any . inside that rectangle is totally fine.
We can cut away all rows above/below and columns left/right that contain no required *.

## Approach-
We scan the whole grid and find the first/last row and first/last column where a * appears.
We keep four boundaries:
top → first row containing a *
bottom → last row containing a *
left → leftmost column containing a *
right → rightmost column containing a *
After finding these four boundaries, we simply print the part of the grid between them.

## Complexity-
Time: O(n × m)-we check every cell once.
Space: O(n × m)-we store the grid.

## Code-
```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>

using namespace std;

int main() {
    int n, m;
    cin >> n >> m;
    vector<string> grid(n);
    for (int i = 0; i < n; i++) {
        cin >> grid[i];
    }
    int top = n;
    int bottom = -1;
    int left = m;
    int right = -1;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            if (grid[i][j] == '*') {
                top = min(top, i);
                bottom = max(bottom, i);
                left = min(left, j);
                right = max(right, j);
            }
        }
    }
    for (int i = top; i <= bottom; i++) {
        for (int j = left; j <= right; j++) {
            cout << grid[i][j];
        }
        cout << '\n';
    }
    return 0;
}
```
## Accepted Submission
![Accepted Submission](14A_Accepted.png)

