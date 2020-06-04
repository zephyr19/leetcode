# Array
### solved
- easy: 8
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

#### Binary Search Pattern

> Used for:
>
> 1. Find the correct index for Val, whether the Val exists or not.
> 2. Find the boundary between two sides.

```java
public int binarySearch(int[] arr, int val) {
    int lo = 0, hi = arr.length - 1;
    while (lo <= hi) {
        int mi = lo + (hi - lo) / 2;  // prevent Interger overflow.
        if (val == mi) return mi;
        if (val > mi)  lo = mi + 1;
        else		   hi = mi - 1;
    }
    return lo;
}
```

#### appropriately use `i++`, `%`, `/`

>  Given two binary strings, return their sum (also a binary string).
>
> The input strings are both **non-empty** and contains only characters `1` or `0`.
>
> **Example 1:**
>
> ​	Input: a = "11", b = "1"
>
> ​	Output: "100"

```java
public String addBinary(String a, String b) {
    StringBuilder sb = new StringBuilder();
    int i = a.length() - 1, j = b.length() - 1, carry = 0;
    while (i >= 0 || j >= 0 || carry == 1) {
        int sum = carry;
        if (i >= 0) sum += a.charAt(i--) - '0';
        if (j >= 0) sum += b.charAt(j--) - '0';
        sb.append(sum % 2);
        carry = sum / 2;
    }
    return sb.reverse().toString();
}
```

#### `ArrayList` vs `LinkedList`

Prefer to use `ArrayList`: consume less memory, and perform well

when you need to add element to front, do as follows:

```java
for (int i = 0; i < n; i++) {
    list.add(val);
}
Collections.reverse(list);
```
