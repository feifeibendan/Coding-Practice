#### Longest Palindromic Substring
Leetcode question #5</br>
Technique use:

```
class Solution {
    String ans = "";
    public String longestPalindrome(String s) {
        if (s == null || s.length() == 0) return "";
        for (int i = 0; i < s.length(); i++) {
            palindrome(s, i, i);
            palindrome(s, i, i + 1);
        }
        return ans;
    }
    
    public void palindrome(String s, int i, int j) {
        while (i >= 0 && j < s.length() && s.charAt(i) == s.charAt(j)) {
            if (ans.length() < j - i + 1) {
                ans = s.substring(i, j + 1);
            }
            i--;
            j++;
        }
    }
}
```