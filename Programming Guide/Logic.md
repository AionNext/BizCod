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


# Class instanciation instruction

Instanciation instruction creates an instance of a class of data. Since class is just a template for data creation it does not hold any value; it is not a container.  To create  a particular instance, BizCod provides `set instance` instruction. Here is an example:


```js
 set account to instance of Account

```

this instruction creates an instance of class `Account` and set the value of variable `account` to this instance



# Conditional instruction

The purpose of conditional instruction is to provide means to process a block of instructions based on certain conditions. If these conditions are met the block will be executed. If they are niot met the block will not be executed. Optionally, conditional instruction can define the block of instructions that will be executed if the conditions arte not met. 
Here is a general format of conditional instruction



```c
  if <condition then
     <block>
  else 
     <block>
  end 

```


# Procedures

A procedure is a collection of instructions that are gropuped togther into a coherent unit. This group of instructions (procedure) can be called and run. Usually, the procedure defines:
- input arguments
- output arguments
- procedure body





____________________
2021 AionNEXT Corporation<br>
we build soft and you build app | <b>soft4app</b>
