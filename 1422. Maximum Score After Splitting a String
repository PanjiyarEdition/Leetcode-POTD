

# 📍Description ➡:-
<!-- Describe your first thoughts on how to solve this problem. -->
IMAGE HERE




# Code
```cpp [C++]
class Solution {
public:
    int maxScore(string inputStr) {
        int onesCount = 0;
        int zerosCount = 0;
        int bestScore = INT_MIN;

        for (int i = 0; i < inputStr.size() - 1; i++) {
            if (inputStr[i] == '1') {
                onesCount++;
            } else {
                zerosCount++;
            }
            
            bestScore = max(bestScore, zerosCount - onesCount);
        }
        
        if (inputStr[inputStr.size() - 1] == '1') {
            onesCount++;
        }
        
        return bestScore + onesCount;
    }
};
```



---

>    **Coded** By $$Panjiyar EDITION$$

               
