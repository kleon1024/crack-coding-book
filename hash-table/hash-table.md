# Hash Table

Hash table is a data structure using a small amount of space to store the values which in a large space. The access time is constant.

```graphviz
digraph G {
label="Hash function x % 2"
graph [fontname=helvetica]
node [shape=box penwidth=2 fontname=helvetica]
edge [penwidth=1.5 arrowhead=vee fontname=helvetica]
rankdir=LR
ranksep=2

h [shape=none margin=0 label=<
<TABLE border="0" cellspacing="1" cellborder="2">
<TR><TD port="0" width="100" height="30" fixedsize="true">0</TD>0</TR>
<TR><TD port="1" width="100" height="30" fixedsize="true">1</TD>1</TR>
<TR><TD port="2" width="100" height="30" fixedsize="true">2</TD>2</TR>
<TR><TD port="3" width="100" height="30" fixedsize="true">3</TD>3</TR>
<TR><TD port="4" width="100" height="30" fixedsize="true">4</TD>4</TR>
<TR><TD port="5" width="100" height="30" fixedsize="true">5</TD>5</TR>
<TR><TD port="6" width="100" height="30" fixedsize="true">6</TD>6</TR>
<TR><TD port="7" width="100" height="30" fixedsize="true">7</TD>7</TR>
</TABLE>
>]

l [shape=none margin=0 label=<
<TABLE border="0" cellspacing="1" cellborder="2">
<TR><TD port="0" width="100" height="30" fixedsize="true">0</TD>0</TR>
<TR><TD port="1" width="100" height="30" fixedsize="true">1</TD>1</TR>
</TABLE>
>]

h:0->l:0
h:1->l:1
h:2->l:0
h:3->l:1
h:4->l:0
h:5->l:1
h:6->l:0
h:7->l:1
}
```

## Hash Function

## Hash Confliction

## Progressive Migration

## Consistant Hashing
