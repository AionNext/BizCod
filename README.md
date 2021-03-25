# BizCod Programming Language


BizCod is a programming language designed to provides means to develop business applications in Rexi native platform. 

The language has been designed to provide a common development platform for both business users (SME) and profesional programmers. Therefore, The language operates at two levels of complexity and this provides a powerful communication means to integrate both group of developers in the process of application development. 

# Introduction

The porogramming foundation of the language has been based on the following concepts :
* [Data](#the-data)
* [Procedural Logic](#the-data)
* [Knowledge](#the-data)


The following chapters provide the detailed explanation of these concepts



# The data

A data element is a container that stores the information. This information can take different forms (or be of certain types). For example it can store text, number or date. The data elements can be grouped together to form a coherent unit of information. 
This unit is called a class of data and the data elements that form this unit are called properties. Therefore, a class is a collection (grouping) of data properties.

As mentioned previously, the data properties are typed to represent different types of data. The following table provides the basic data types (partial): 

| type                           | Description   |
|--------------------------------|------------------------------------------------------------------------|
| text                    | textual data to store the text such as 'John Roberts' 'commercial account' and so on                                          | 
| number                     | number to store numbers such as 100, 3000. The number can be either positive or negative                                        | 
| decimal                     | decimal data that are desiged to store decimal numbers such as 213213.45 , -24324.67                                          | 
| date                     | to store then date                                      | 
| logical                     | logical type that can be either true or false                                        | 

Note that this table provides a partial list of data types only. 

Let's take a look at the following description of the Accoun class. Usually, an account has 




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



____________________
2021 AionNEXT Corporation<br>
we build soft and you build app | <b>soft4app</b>
