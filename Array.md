# Array
### solved
- easy: 3
- medium: 0
- hard: 0

## Tricks
#### using a fake head to avoid edge cases (link list)

> Edge cases could be:
>
> 1. head is null
> 2. `head.val = val`, thus you should remove the head node
>
> If use regular method the head node wouldn't be processed,  you need to write more code to prevent edge case fail

``` java
public ListNode removeElements(ListNode head, int val) {
    ListNode dummy = new ListNode(0, head);
    ListNode cur = dummy;    
    while(cur.next != null) {
        if(cur.next.val == val) cur.next = cur.next.next;
        else 					cur = cur.next;
    }
    return dummy.next;
}
```


