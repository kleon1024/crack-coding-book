# Linked List

Linked List is a list of uncontigous memory blocks.

## Singly Linked List

Singly linked list has a pointer *next* pointing to the successor of the current node in the linked list.

```graphviz
digraph G {
graph [fontname=helvetica]
node [shape=box penwidth=2 fontname=helvetica]
edge [penwidth=1.5 arrowhead=vee fontname=helvetica]
rankdir=LR

A->B->C->null [label=next]
null [shape=plaintext]
}
```

### Traversion

We can traverse through the linked list using a pointer.

```graphviz
digraph G {
graph [fontname=helvetica]
node [shape=box penwidth=2 fontname=helvetica]
edge [penwidth=1.5 arrowhead=vee fontname=helvetica]
rankdir=LR

head -> A [constraint=false]
A -> B -> C -> null [label=next]
null [shape=plaintext]
}
```

### Reversion

We can use three pointer to reverse the order of the linked list.

```go
cur, pre := head, nil
for cur.Next != nil {
	cur, cur.Next, pre = cur.Next, pre, cur
}

```

Before

```graphviz
digraph G {
graph [fontname=helvetica]
node [shape=box penwidth=2 fontname=helvetica]
edge [penwidth=1.5 arrowhead=vee fontname=helvetica]
rankdir=LR

cur->A [constraint=false color=palegreen3]
pre->null2 [constraint=false color=indianred3]
cur [color=palegreen3]
pre [color=indianred3]

null2 [label=null shape=plaintext]
pre->cur [style=invis]
null2 -> A [style=invis]
B -> C -> null [label=next]
A->B [color=deepskyblue3]
A [color=deepskyblue3]
null [shape=plaintext]
}
```

After

```graphviz
digraph G {
graph [fontname=helvetica]
node [shape=box penwidth=2 fontname=helvetica]
edge [penwidth=1.5 arrowhead=vee fontname=helvetica]
rankdir=LR

null1->null2 [constraint=false style=invis]
cur->B [constraint=false color=palegreen3]
pre->A [constraint=false color=indianred3]
null1->pre->cur [style=invis]

null2 -> A [dir=back color=deepskyblue3]
A [color=deepskyblue3]
B -> C -> null [label=next]
A -> B [style=invis]

pre [color=indianred3]
cur [color=palegreen3]

null1 [style=invis]

null [label=null shape=plaintext];
null2 [label=null shape=plaintext];
}
```

### Nth node from the end

To find the Nth node from the tail of the linked list, we can use two pointers.
First move the faster pointer N steps and then move both pointers until the faster pointer reach the end of the linked list.
This can save us one time of full traversion.


```go
slow, fast := head, head
for i := 0; i < N; i++ {
	fast = fast.Next
}
for fast.Next != nil {
	fast = fast.Next
	slow = slow.Next
}
```

## Doubly Linked List

Doubly linked list has another pointer *prev* pointing to the predecessor of the current node as well.

```graphviz
digraph G {
forcelabels=true;
graph [fontname=helvetica]
node [shape=box penwidth=2 fontname=helvetica]
edge [penwidth=1.5 arrowhead=vee fontname=helvetica]
rankdir=LR

tmph -> head -> tmp -> tail -> tmpt [style=invis]
tmph [style=invis]
tmp [style=invis]
tmpt [style=invis]
head -> A [constraint=false]
tail -> C [constraint=false]
tmph -> nullh [constraint=false style=invis]
tmpt -> nullt [constraint=false style=invis]


nullh -> A -> B -> C -> nullt [label=next constraint=false]
nullh -> A -> B -> C -> nullt [style=invis]
nullh -> A -> B -> C -> nullt [label=prev dir=back arrowtail=vee constraint=false]
nullh [label=null shape=plaintext]
nullt [label=null shape=plaintext]
}
```

## Circular Linked List

The head and tail of a circular linked list are linked together.

```graphviz
digraph G {
forcelabels=true;
graph [fontname=helvetica]
node [shape=box penwidth=2 fontname=helvetica]
edge [penwidth=1.5 arrowhead=vee fontname=helvetica]
rankdir=LR

A -> B -> C -> D 
D -> A [constraint=false]
}
```