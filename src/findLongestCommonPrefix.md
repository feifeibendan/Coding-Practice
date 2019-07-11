#### Find the longest common prefix
Leetcode question #14</br>
Technique use: Binary Search

```
public String longestCommonPrefix(String[] strs) {
    if (strs.length == 0) return "";
    int min = Integer.MAX_VALUE;
    for (String s : strs) {
        min = Math.min(min, s.length());
    }
        
    int l = 0, r = min - 1;
        
    while (l <= r) {
        int mid = l + (r - l) / 2;
        if (containPrefix(strs, l, mid)) {
            l = mid + 1;
        } else {
            r = mid - 1;
        }
    }
    return strs[0].substring(0, l);
}
    
public boolean containPrefix(String[] strs, int start, int end) {
    String word = strs[0];
    for (int i = 1; i < strs.length; i++) {
        for (int j = start; j <= end; j++) {
            if (word.charAt(j) != strs[i].charAt(j)) {
                return false;
            }
        }
    }
    return true;
}
```