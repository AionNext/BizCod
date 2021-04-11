# BizCod Methods

Data model defines a data structure in terms of properties. However, the properties alone do not provide any means of processing the content of the data model. Methods are simply functions that are defined on a data model for the purpose of processing the data model content. A data model can have unlimited number of methods defined (or attached to it). Methods provide very practical and convenient ways to define functionalities proper to the data model they are defined on.

Her is a formal definition of a method.

```js

define 
    method <data-model>::<method-name>([<args>]) [ -> variable Type] 
        <method-body>

```

Here, a method `isCommercialAccount` is defined on data model `Account` and accepts argument `type` (Text) and returns logical value.

Methods are simply [functions](Function.md) defined on the data model to process the data model content. here is a practical illustration of that concept:

```js
    define Account:init(name Text, ssn Text, )  
        
    
```
