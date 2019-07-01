---
layout: post
title: "LR Parser"
date: 2019-3-10
excerpt: "Just a note about what I've just learnt in case I forget"
tags: [parser,note]
comments: true
---

<script src="/assets/raphael-min.js"> </script>

<script src="/assets/flowchart.min.js"> </script>

# LR Parser

首先，LR Parser的实现需要一个Action Table和Goto Table。这两个表每个的行数都代表一个**状态**

示例：

假设有以下语法：

> (1) S -> AA
>
> (2) A -> aA
>
> (3) A -> b

<div id="diagram"></div>
<script>
  $.ajax({
      url: "/assets/LRParserIterationFlow.txt",
      success: function (data){
            var diagram = flowchart.parse(data);
            diagram.drawSVG('diagram');
      }
  });
  
</script>

```flow
st=>start: Start


create new node=>operation: Create a new Node

create an augmented rule=>operation: Create an augmented rule(S' in this example)

place a dot at the start=>subroutine: Place a dot at the start of the rule(the current rule means the item after the dot in this flow chart)

the current symbol is a rule=>condition: Is the current symbol a rule?

create a rule after=>operation: create a rule after(the current rule is the created rule's 'parent')

if the current rule is augmented=>condition: Is the current rule augmented?

set lookahead to $=>operation: Set lookahead to $(EOF)

create a list of items after=>operation: Create a list of items of items after the parent node's current symbol including the lookahead

find front token=>operation: Find the very front token of the first item of the list and set lookahead to it

finish and create=>operation: Finish the current node and create a subnode connected to each rule the current node has

shift the dot=>operation: copy every rules and shift each rule's dot once in each subnode

dulplicate in other=>condition: Is it dulplicate?

connect to the dulplicate one=>operation: connect to the dulplicate one


st->create new node
create new node->create an augmented rule
create an augmented rule->place a dot at the start
place a dot at the start->the current symbol is a rule
the current symbol is a rule(yes, left)->create a rule after
create a rule after(left)->place a dot at the start
the current symbol is a rule(no, right)->if the current rule is augmented
if the current rule is augmented(yes, right)->set lookahead to $
if the current rule is augmented(no)->create a list of items after
create a list of items after->find front token
set lookahead to $->finish and create
create a list of items after->finish and create
finish and create->shift the dot
shift the dot(right)->dulplicate in other
dulplicate in other(yes, left)->connect to the dulplicate one
dulplicate in other(no, right)->the current symbol is a rule
connect to the dulplicate one(right)->the current symbol is a rule
```

## Create the parse table

```flow
st=>start: Start from the root node
```

