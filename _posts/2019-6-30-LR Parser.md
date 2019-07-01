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

<script src="https://qiufeng54321.github.io/assets/js/jquery-1.12.0.min.js"></script>
<script src="https://qiufeng54321.github.io/assets/js/jquery.dlmenu.min.js"></script>

<script src="https://qiufeng54321.github.io/assets/js/jquery.goup.min.js"></script>

<script src="https://qiufeng54321.github.io/assets/js/jquery.magnific-popup.min.js"></script>

<script src="https://qiufeng54321.github.io/assets/js/jquery.fitvid.min.js"></script>



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
            diagram.drawSVG('diagram', {
                              'maxWidth': 45,
                              'maxHeight': 25
            });
      }
  });</script>

## Create the parse table

```flow
st=>start: Start from the root node
```

