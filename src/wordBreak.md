#### Word Break
Leetcode question #139</br>

Solution 1. Technique use: recusion

```
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        int size = s.length();
        if (size == 0) return true;
        
        for (int i = 1; i <= size; i++) {
            if (wordDict.contains(s.substring(0, i)) && wordBreak(s.substring(i, size), wordDict)) {
                return true;
            }
        }
        return false;
    }
}
```
Time is O(2^n) and exceed the time limit

Solution 2. Technique use: DP

```
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        boolean[] isWordBreak = new boolean[s.length() + 1]; //add 1 because array of zero
        isWordBreak[0] = true; //empty string should all be in the wordDict
        
        for (int i = 0; i < s.length() + 1; i++) {
            for (int j = 0; j < i; j++) {
                if (!isWordBreak[j]) continue;
                if (wordDict.contains(s.substring(j, i))) {
                    isWordBreak[i] = true;
                    break;
                }
            }
        }
        return isWordBreak[s.length()];
    }
}
```
Time complexity is O(n^2). The space complexity is O(n)
```
/**
String s = "leetcode";
the outer loop
""
"l"
"le"
"lee"
"leet"
"leetc"
"leetco"
"leetcod"
"leetcode"

the inner loop
""
"l", ""
"le", "e", ""
"lee", "ee", "e", ""
"leet", "eet", "et", "t", ""
"leetc", "eetc", "etc", "tc", "c", ""
"leetco", "eetco", "etco", "tco", "co", "o", ""
"leetcod", "eetcod", "etcod", "tcod", "cod", "od", "d", ""
"leetcode", "eetcode", "etcode", "tcode", "code", "ode", "de", "d", ""
**/
```