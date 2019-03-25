## [1023. Binary String With Substrings Representint 1 to N](https://leetcode.com/contest/weekly-contest-129/problems/binary-string-with-substrings-representing-1-to-n/)
1. Key observation: to contain all the 1 to N binary representations, the length of string S.length()>logN/2*N/2 => N<4*S.length();
2. Then we can check all the numbers under N.

```c++
class Solution {
public:
    bool queryString(string S, int N) {
        if (N > 1000)
            return false;

        for (int i = 1; i <= N; i++) {
            string str = "";
            int x = i;

            while (x != 0) {
                str += x % 2 + '0';
                x /= 2;
            }

            reverse(str.begin(), str.end());

            if (S.find(str) == string::npos)
                return false;
        }

        return true;
    }
};
```