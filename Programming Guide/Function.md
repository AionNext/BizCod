# BizCod Function


What is a function and what purpose does it serve? While procedure processes the data as well, it is fundamentally different from function because it does not produce results. In BizCod programming paradigm, the objective of function is to produce results by processing the input data called `arguments`. The result is called a `returning value`. 

Function has the following properties

- name
- arguments
- returning type
- body

The following represents a formal function definition

```js
define function <name>([<args>]) [ ->  variable [Type] ] 

  [<body>]
```


where arguments, and body can be optional. 


## Functional abstraction

When the body is not provided, the function is called `abstract`. Similar to data models, functions are objects as well and therefore can be subjected to the inheritance mechanism. 

```js

  define
    function calculateMortgageAmortizationSchedule(Mortgage,MortgageScheme) -> MprtgageAmortizationSchedule
```

