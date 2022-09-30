# Reserve List

## Reverse Linked List

🟢[lc206](https://leetcode.com/problems/reverse-linked-list/)

{% tabs %}
{% tab title="Go" %}
```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    var pre *ListNode
    cur := head
    for cur != nil {
        pre, cur, cur.Next = cur, cur.Next, pre
    }
    return pre
}
```
{% endtab %}
{% tab title="Rust" %}
```rust
// Definition for singly-linked list.
// #[derive(PartialEq, Eq, Clone, Debug)]
// pub struct ListNode {
//   pub val: i32,
//   pub next: Option<Box<ListNode>>
// }
// 
// impl ListNode {
//   #[inline]
//   fn new(val: i32) -> Self {
//     ListNode {
//       next: None,
//       val
//     }
//   }
// }
impl Solution {
    pub fn reverse_list(head: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
        let (mut pre, mut cur) = (None, head);
        
        while let Some(mut node) = cur {
            cur = node.next;
            node.next = pre;
            pre = Some(node);
        }
        pre
    }
}
```
{% endtab %}
{% endtabs %}

## Reverse Linked List II

🟡[lc92](https://leetcode.com/problems/reverse-linked-list-ii/)

## Reverse Nodes in k-Group

🔴[lc25](https://leetcode.com/problems/reverse-nodes-in-k-group/)

## Reverse Nodes in Even Length Groups

🟡[lc2074](https://leetcode.com/problems/reverse-nodes-in-even-length-groups/)