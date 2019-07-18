#### Count number of primes
Leetcode question #204</br>
Technique use: Sieve of eratosthenes
```
public int countPrimes(int n) {
    if (n < 2) return 0;
        
    boolean[] primes = new boolean[n];
    for (int i = 2; i < n; i++) {
        primes[i] = true;
    }
        
    for (int i = 2; i*i < n; i++) {//formula p*p, p*p + p, p*p + 2P ex: 2*2, 2*2 + 2, 2*2 + 4
        if (primes[i] == true) {
            for (int j = i*i; j < n; j+=i) {
                primes[j] = false;
            }
        }
    }
        
    int ans = 0;
    for (int i = 2; i < n; i++) {
        if (primes[i] == true) ans++;
    }
    return ans;
}
```