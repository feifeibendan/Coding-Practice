#### Happy Number
Leetcode question #202</br>
Technique use: Recursion

```
class Solution {
    Set<Integer> set = new HashSet<>();
    public boolean isHappy(int n) {
        if (n == 0) return false;
        if (n == 1) return true;
        int sum = 0;
        while (n != 0) {
            int pop = n % 10;
            sum += pop * pop;
            n /= 10;
        }
        if (!set.add(sum)) {
            return false;
        }
        return isHappy(sum);
    }
}
```