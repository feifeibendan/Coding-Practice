#### Long Pressed Name
Leetcode question #925</br>
Technique use:

```
class Solution {
    public boolean isLongPressedName(String name, String typed) {
        int i = 0, j = 0;
        boolean back = false;
        while (j < typed.length()) {
            if (i >= name.length() && j < typed.length())
                i--;
            if (name.charAt(i) == typed.charAt(j)) {
                i++;
                j++;
                back = false;
            } else if (i >= 0 && name.charAt(i) != typed.charAt(j)) {
                i--;
                if (back || i < 0) return false;
                back = true;
            }
        }
        return i == name.length();
    }
}
```