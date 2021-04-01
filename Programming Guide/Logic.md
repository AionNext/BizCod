# BizCod Procedural Logic


The objective of BizCod procedural logic is to provide means to process the data. Once the data are defined, they can be processed in order to produce information or to generate other types of data.

From conceptual standpoint, procedural logic is a set of instructions that the programmer can use (group) to process the data. Since these instructions perform different functions, they are of different types. Here are the basi types:
- assignment instructions
- conditional instructions
- procedure invocation instructions

# Assignment instruction

Assignment instruction assigns value to a variable or property. There are two forms that can be used, being either:
- set - using form **set** `property` **to** `value`, or
- direct assignment

here are examples of these two forms

```js
set interestRate to 0.12

```

or, alternatively

```js
 interestRate = 0.12

```

these two forms are equivalent.


# Instanciation instruction

Instanciation instruction creates an instance of a class of data. Since class is just a template for data creation it does not hold any value; it is not a container.  To create  a particular instance, BizCod provides `set instance` instruction. Here is an exampple:


```js
 set account to instance of Account

```


# Procedures

A procedure is a collection of instructions that are gropuped togther into a coherent unit. This group of instructions (procedure) can be called and run. Usually, the procedure defines:
- input arguments
- output arguments
- procedure body





