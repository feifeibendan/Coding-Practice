#### Valid Perfect Square
Leetcode question #367</br>
Technique use: Binary search

```
public boolean isPerfectSquare(int num) {
    if (num == 0) return false;
    if (num == 1) return true;
    long l = 1, r = num / 2;
    while (l <= r) {
        long mid = l + (r - l) / 2;
        long sqrt = mid * mid;
        if (sqrt == num) {
            return true;
        } else if (sqrt < num) {
            l = mid + 1;
        } else {
            r = mid - 1;
        }
    }
    return false;
}
```