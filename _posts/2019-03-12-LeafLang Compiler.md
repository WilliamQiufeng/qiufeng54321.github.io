---
layout: post
title: "LeafLang Compiler"
date: 2019-3-12
excerpt: "LeafLang Compiler docs and how it does."
tags: [project,language,compiler]
comments: true
typora-root-url: ../../qiufeng54321.github.io
---

# LeafLang Compiler

LeafLang compiler is currently under ***development***.**Anything** may change .

## Output Structure

**Note**:This is a standard and the code is yet to be completed.

For *Example* the source code:

##### Code:

```
function sth:(args){
    println("hi");
};
var somevar=1024;
class AClass{
    function _init:(x,y){
        x=1;
        y=2;
    };
    function dosth{
        println("yayay");
    };
};
```



The compiler will translate the source file into like this:

```
root
\_ .conpl
\_ sth.func
\_ somevar.var
\_ AClass
\___ _init.func
\___ dosth.func
```

***And Then***,It zips the root file to make a leaflang executable file.(Yeah it is just a zip archive)

## ByteCode

Every code starts with an **Operation Code** and then the optional arguments.

First,each type of id's length:

| Type of ID | Length |
| ---------- | ------ |
| uid        | 2      |
| cid        | 2      |
| bid        | 2      |
| num        | 4      |



### Constant Pool

*Operation Code*:0x01

*Follows by*:

+ Arguments count:expressed as a num
+ {Arguments count} constant pool elements

#### Constant Pool Element

Structure:

*Tag*+Value

##### Num

*Tag*:\x00

*Value*:**type** num

##### String

*Tag*:\x01

*Value*:

+ **type** num count of string
+ utf-8 string

### OpCodes

See docs in `OpCodes.py`.

## Example

```
var a=10;
var b=11;
a=b;
```

![Result](/assets/LeafLangCompilerPreview1.jpeg)

