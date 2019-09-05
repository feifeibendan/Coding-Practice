#### Palindromic Substrings
Leetcode question #647</br>
Technique use: 

```
Technique use: Brute force
class Solution {
    public int countSubstrings(String s) {
        if (s == null || s.length() == 0) return 0;
        
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            for (int j = i + 1; j <= s.length(); j++) {
                if (isPalindromic(s.substring(i, j))) {
                    count++;
                }    
            }
        }
        return count;
    }
    
    public boolean isPalindromic(String substring) {
        int start = 0, end = substring.length() - 1;
        while (start <= end) {
            if (substring.charAt(start) != substring.charAt(end)) {
                return false;
            }
            start++;
            end--;
        }
        return true;
    }
}
```

```
Technique use: around the center
class Solution {
    public int countSubstrings(String s) {
        if (s == null || s.length() == 0) return 0;
        
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            count += countSubstrings(s, i, i);
            count += countSubstrings(s, i, i + 1);
        }
        return count;
    }
    
    public int countSubstrings(String s, int i, int j) {
        int count = 0;
        while (i >= 0 && j < s.length() && s.charAt(i) == s.charAt(j)) {
            i--;
            j++;
            count++;
        }
        return count;
    }
}
```