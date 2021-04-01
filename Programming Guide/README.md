# BizCod Programming Language


BizCod is a programming language designed to provides means to develop business applications in Rexi native platform. 

The language has been designed to provide a common development platform for both business users (SME) and profesional programmers. Therefore, The language operates at two levels of complexity and this provides a powerful communication means to integrate both group of developers in the process of application development. 

# Introduction

The porogramming foundation of the language has been based on the following concepts :
* [Data](Data.md)
* [Procedural Logic](Logic.md)
* [Knowledge](#the-data)
* [User Interface](#the-data)


The following chapters provide the detailed explanation of these concepts



# The data

A data element is a container that stores the information. This information can take different forms (or be of certain types). For example it can store text, number or date. The data elements can be grouped together to form a coherent unit of information. 
This unit is called a class of data and the data elements that form this unit are called properties. Therefore, a class is a collection (grouping) of data properties.

As mentioned previously, the data properties are typed to represent different forms of data. To begin with and create a basic data type foundation, BizCod provides the types the are 'internally' defined. These internal types are called primitive types. The following table provides the basic primitive data types: 

| primitive data type                           | description   |
|--------------------------------|------------------------------------------------------------------------|
| ID                             |  this data type stores a unique ID number. It is usually used for identification purpose to identify objects that are globally unique                    |
| Text                    | textual data to store the text such as 'John Roberts' 'commercial account' and so on                                          | 
| Number                     | number to store numbers such as 100, 3000. The number can be either positive or negative                                        | 
| Decimal                     | decimal data that are desiged to store decimal numbers such as 213213.45 , -24324.67                                          | 
| Date                     | to store then date                                      | 
| Logical                     | logical type that can be either <b>true</b> or <b>false</b>                                        | 

Note that this table provides a partial list of data types only. 

Moving forward, let's provide a practical application of BizCod data model. We will use the Banking system to define the data model. 
Here we will define a Account class to hold the basic information about the account




```
define model Account
    id ID,
    name Text,
    accountType Text    
;
```
In simple terms, this BzCod statement translates into :
define a data model (class) Account that has id , name and account type properties. These properties are of different types (ID, Text and Text respectively) to represent different forms of data.

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
