# BizCod

# BizDev Programming Guide

BizDev is a suite of products that enable the development of Enterprise Application Software Fabric (EAS/F) in Rexi environment.

It is Rexi based and can only run in Rexi environment. For more information about Rexi Operating System please refer to this publication.


```
define model Bank
    id ID,
    name Text fact,
    account (Account)* [1:n]
;
```

```html
<script src="//unpkg.com/graphre/dist/graphre.js"></script>
<script src="//unpkg.com/nomnoml/dist/nomnoml.js"></script>

<canvas id="target-canvas"></canvas>
<script>
    var canvas = document.getElementById('target-canvas');
    var source = '[nomnoml] is -> [awesome]';
    nomnoml.draw(canvas, source);
</script>
```

## Table of Contents
* [Introduction](#introduction)
* [Structure of BizCod](#structure-of-griddb)
* [Instruction set](#instruction-set)


