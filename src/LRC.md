#### LRU Cache
Leetcode question #146</br>
Technique use: Doubly LinkListed and HashMap

```
class LRUCache {

    int size = 0;
    Map<Integer, Node> map;
    Node head, tail;
    
    public LRUCache(int capacity) {
        this.size = capacity;
        this.map = new HashMap<>();
        this.head = new Node(0, 0);
        this.tail = new Node(0, 0);
        this.head.next = tail;
        this.tail.pre = head;
    }
    
    public int get(int key) {
        Node node = this.map.get(key);
        if (node == null) return -1;
        remove(node);
        add(node);
        return node.val;
    }
    
    public void put(int key, int value) {
        if (this.map.containsKey(key)) {
            Node node = this.map.get(key);
            node.val= value;
            remove(node);
            add(node);
        } else {
            Node node = new Node(key, value);
            add(node);
            this.map.put(key, node);
            
            if (this.map.size() > this.size) {
                this.map.remove(tail.pre.key); //remove from map first before remore node
                remove(tail.pre);
            }
        }
    }
    
    public void add(Node node) {
        //extra caution here, order does matter
        node.next = head.next;
        node.pre = head;
        head.next.pre = node;
        head.next = node;
    }
    
    public void remove(Node node) {
        node.pre.next = node.next;
        node.next.pre = node.pre;
    }
}

class Node {
    Node pre;
    Node next;
    int key;
    int val;
    
    public Node(int key, int val) {
        this.key = key;
        this.val = val;
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```