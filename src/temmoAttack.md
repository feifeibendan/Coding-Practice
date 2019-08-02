#### Temmo Attack
Leetcode question #495</br>
Technique use: 

```
public int findPoisonedDuration(int[] timeSeries, int duration) {
    if (timeSeries.length == 0 || duration == 0) return 0;
    int damage = 0;
        
    for (int i = 0; i < timeSeries.length - 1; i++) {
        damage += duration;
        if (timeSeries[i] + duration > timeSeries[i + 1]) {
            damage -= (timeSeries[i] + duration - timeSeries[i + 1]);
        }
    }
    damage += duration;
    return damage;
}
```