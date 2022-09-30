# Numbers

## 2. Add Two Numbers

Basic decimal addition.

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
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
    head := &ListNode{}
    current := head
    carry := 0
    for carry > 0 || l1 != nil || l2 != nil {
        if l1 != nil {
            carry += l1.Val
            l1 = l1.Next
        }
        if l2 != nil {
            carry += l2.Val
            l2 = l2.Next
        }
        current.Next = &ListNode{
            Val: carry % 10,
        }
        carry /= 10
        current = current.Next
    }
    return head.Next
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
    pub fn add_two_numbers(l1: Option<Box<ListNode>>, l2: Option<Box<ListNode>>) -> Option<Box<ListNode>> {
        let mut l1 = l1.clone();
        let mut l2 = l2.clone();
        let mut head = Box::new(ListNode::new(0));
        let mut carry = 0;
        let mut current = &mut head;
        
        while carry > 0 || l1.is_some() || l2.is_some() {
            if let Some(node) = l1 {
                carry += node.val;
                l1 = node.next;
            }
            if let Some(node) = l2 {
                carry += node.val;
                l2 = node.next;
            }
            current.next = Some(Box::new(ListNode::new(carry % 10)));
            carry /= 10;
            current = current.next.as_mut().unwrap();
        }
        return head.next;
    }
}
```
{% endtab %}
{% endtabs %}