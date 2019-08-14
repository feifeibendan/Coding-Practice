#### Arrange Coin
Leetcode question #441</br>
Technique use: binary search

```
class Solution {
    public int arrangeCoins(int n) {
        if (n == 0) return 0;
        long l = 1, r = n;
        while (l <= r) {
            long mid = l + (r - l) / 2;
            long coin = mid * (mid + 1) / 2;
            if (coin == n) {
                return (int)mid;
            } else if (coin < n) {
                l = mid + 1;
            } else {
                r = mid - 1;
            }
        }
        return (int)(l - 1);
    }
}
```