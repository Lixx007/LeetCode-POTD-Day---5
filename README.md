# 🚀 LeetCode POTD - Day 5

<table>
<tr>
<td align="left" width="400">
  <img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*VOQU8CuPG34Gsd1yJCadOQ.png" width="100%"/>
</td>
</tr>
</table>

---

## 🧙‍♂️ 3443. Maximum Manhattan Distance After K Changes

[Link to problem](https:https://leetcode.com/problems/divide-array-into-arrays-with-max-difference/)

---

## 🔥 Optimal Solution

```cpp
class Solution {
public:
    int maxDistance(string s, int k) {
        int maxMD = 0;

        int east = 0;
        int west = 0;
        int north = 0;
        int south = 0;

        for(int i = 0; i < s.length(); i++) {

            if(s[i] == 'E') east++;
            else if(s[i] == 'W') west++;
            else if(s[i] == 'N') north++;
            else if(s[i] == 'S') south++;

            int currMD = abs(east-west) + abs(north-south);

            int steps  = i+1;
            int wasted = steps - currMD;

            int extra = 0;
            if(wasted != 0) { //steps != currMD
                extra = min(2*k, wasted);
            }

            int finalCurrentMD = currMD + extra;

            maxMD = max(maxMD, finalCurrentMD);
        }

        return maxMD;
    }
};





