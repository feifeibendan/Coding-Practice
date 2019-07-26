#### Power of Three
Leetcode question #326</br>
Technique use: 

```
public boolean isPowerOfThree(int n) {
    if (n == 0) return false;
    while (n % 3 == 0) {
        n /= 3;
    }
    return n == 1;
}
```