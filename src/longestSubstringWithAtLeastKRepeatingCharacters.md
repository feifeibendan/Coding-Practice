#### 395 Longest Substring with At Least K Repeating Characters
Leetcode question #395</br>
Technique use: Recursion
```
public int longestSubstring(String s, int k) {
    if (s == null || s.length() == 0) return 0;
        
    int[] a = new int[26];
    for (int i = 0; i < s.length(); i++) {
        char c = s.charAt(i);
        a[c - 'a'] += 1;
    }
        
    boolean valid = true;
    for (int i = 0; i < s.length(); i++) {
        char c = s.charAt(i);
        if (a[c - 'a'] < k) {
            valid = false;
        }
    }
    if (valid) return s.length();
        
    int tail = 0, pos = 0, max = 0;
    while (tail < s.length()) {
        char c = s.charAt(tail);
        if (a[c - 'a'] < k) {
            max = Math.max(max, longestSubstring(s.substring(pos, tail), k));
            pos = tail + 1;
        }
        tail++;
    }
    max = Math.max(max, longestSubstring(s.substring(pos), k));
    return max;
}
```