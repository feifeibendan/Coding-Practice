#### Find the longest Substring without repeated character
Leetcode question #2</br>
Techique use: sliding window
```
public int lengthOfLongestSubstring(String s) {
    int max = 0, tail = 0, head = 0;
    Map<Character, Integer> map = new HashMap<>();
    while (tail < s.length()) {
        char c = s.charAt(tail);
        if (map.containsKey(c)) {
            head = Math.max(head, map.get(c));
        }
        tail++;
        max = Math.max(max, tail - head);
        map.put(c, tail);
    }
    return max;
}
```