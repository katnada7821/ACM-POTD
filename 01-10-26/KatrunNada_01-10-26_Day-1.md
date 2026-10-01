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
top-first row containing a *
bottom-last row containing a *
left-leftmost column containing a *
right-rightmost column containing a *
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

# Problem 2

## Problem Description
In this problem you are to calculate the sum of all integers from 1 to n, but you should take all powers of two with minus in the sum.
For example, for n = 4 the sum is equal to  - 1 - 2 + 3 - 4 =  - 4, because 1, 2 and 4 are 20, 21 and 22 respectively.
## Approach-
1.Calculate sum by using formula 
2. Subtract every power of 2
normal sum = 1 + 2 + 3 + 4 = 10
minus = 1  10 - 1 = 9
minus = 2  9 - 2 = 7
minus = 4  7 - 4 = 3
this gives 3, but the required answer is -4.
so here came the intution of solution To change +1 into -1, we need to subtract 2 × 1.
therefore, sum -= 2 * minus;
## Complexity-
Time: O(log n) (We're doubling minus every time, so it takes about log₂(n) iterations)
Space: O(1)
## Code-
```cpp
#include <iostream>
using namespace std;
int main(){
    int t;
    cin>>t;
    while(t--){
        long long n;
        cin>>n;
        long long sum=n*(n+1)/2;
        long long minus=1;
        while(minus<=n){
            sum-=2*minus;
            minus*=2;
        }
        cout<<sum<<'\n';
    }
    return 0;
}
```
## Accepted Submission
![Accepted Submission](598A_Accepted.png)






