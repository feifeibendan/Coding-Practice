#### Reverse vowel of string
Leetcode question #345</br>
Technique use: two pointer

```
public String reverseVowels(String s) {
    List<Character> vowel = Arrays.asList('a','e','i','o','u', 'A', 'E', 'I', 'O', 'U');
    int start = 0, end = s.length() - 1;
    char[] reverse = new char[s.length()];
    while (start <= end) {
        char l = s.charAt(start);
        char r = s.charAt(end);
        if (vowel.contains(l) && vowel.contains(r)) {
            reverse[start] = r;
            reverse[end] = l;
            start++;
            end--;
            continue;
        }
        if (!vowel.contains(l)) {
            reverse[start] = l;
            start++;
        }
        if (!vowel.contains(r)) {
            reverse[end] = r;
            end--;
        }
    }
    return new String(reverse);
}
```