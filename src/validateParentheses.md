#### Validate Parentheses
Leetcode question #20</br>
Technique use: Stack and HashMap

```
class Solution {

    Map<Character, Character> map;
    
    public Solution() {
        this.map = new HashMap<>();
        this.map.put(')', '(');
        this.map.put(']', '[');
        this.map.put('}', '{');
    }
    
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (map.containsKey(c)) {
                char pop = stack.isEmpty() ? '#' : stack.pop();
                if (map.get(c) != pop) return false;
            } else {
                stack.push(c);
            }
        }
        return stack.isEmpty();
    }
}
```