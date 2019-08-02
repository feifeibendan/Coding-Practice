#### 4Sum II
Leetcode question #454</br>
Technique use: 

```
public int fourSumCount(int[] A, int[] B, int[] C, int[] D) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < A.length; i++) {
        for (int j = 0; j < B.length; j++) {
            int val = A[i] + B[j];
            map.put(val, map.getOrDefault(val, 0) + 1);
        }
    }
        
    int count = 0;
    for (int i = 0; i < C.length; i++) {
        for (int j = 0; j < D.length; j++) {
            int val = C[i] + D[j];
            if (map.containsKey(0 - val)) {
                count += map.get(0 - val);
            }
        }
    }
    return count;
}
```