#### 206 Reverse Linked List
Leetcode question #206</br>
Technique use: 
```
public ListNode reverseList(ListNode head) {
    if (head == null) return null;
    ListNode pre = null;
    while (head != null) {
        ListNode tail = new ListNode(head.val);
        tail.next = pre;
        pre = tail;
        head = head.next;
    }
    return pre;
}
```