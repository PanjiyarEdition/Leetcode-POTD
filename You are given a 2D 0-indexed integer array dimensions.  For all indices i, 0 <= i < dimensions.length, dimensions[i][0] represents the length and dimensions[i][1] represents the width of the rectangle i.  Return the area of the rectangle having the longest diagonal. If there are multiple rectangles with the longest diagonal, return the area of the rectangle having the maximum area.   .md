# 📍Description ➡:-
<!-- Describe your first thoughts on how to solve this problem. -->
You are given a 2D 0-indexed integer array dimensions.

For all indices i, 0 <= i < dimensions.length, dimensions[i][0] represents the length and dimensions[i][1] represents the width of the rectangle i.

Return the area of the rectangle having the longest diagonal. If there are multiple rectangles with the longest diagonal, return the area of the rectangle having the maximum area.

 

# 📝Code ⬇:-


# Java
```java []

class Solution {
    public int areaOfMaxDiagonal(int[][] dimensions) {
        int n = dimensions.length;
        int maxArea = 0, maxDiag = 0;

        for (int i = 0; i < n; i++) {
            int l = dimensions[i][0];
            int w = dimensions[i][1];
            int currDiag = l * l + w * w;

            if (currDiag > maxDiag || (currDiag == maxDiag && l * w > maxArea)) {
                maxDiag = currDiag;
                maxArea = l * w;
            }
        }
        return maxArea;
    }
}

```

# C++
``` cpp []
class Solution {
public:
    int areaOfMaxDiagonal(vector<vector<int>>& dimensions) {
        int maxArea = 0, maxDiag = 0;

        for (int i = 0; i < dimensions.size(); i++) {
            int l = dimensions[i][0];
            int w = dimensions[i][1];
            int currDiag = l * l + w * w;

            if (currDiag > maxDiag || (currDiag == maxDiag && l * w > maxArea)) {
                maxDiag = currDiag;
                maxArea = l * w;
            }
        }
        return maxArea;
    }
};
```

# Python
``` python []
class Solution:
    def areaOfMaxDiagonal(self, dimensions: list[list[int]]) -> int:
        max_area, max_diag = 0, 0

        for l, w in dimensions:
            curr_diag = l * l + w * w
            if curr_diag > max_diag or (curr_diag == max_diag and l * w > max_area):
                max_diag = curr_diag
                max_area = l * w

        return max_area    
```

---

>    **Coded** By $$Panjiyar EDITION 🖋  $$

               
