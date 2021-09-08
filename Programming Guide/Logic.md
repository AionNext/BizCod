# BizCod Procedural Logic


The objective of BizCod procedural logic is to provide a means to process the data. Once the data are defined, they can be processed in order to produce information or to generate other types of data.

From conceptual standpoint, procedural logic is a set of instructions that the programmer can use (group) to process the data. Since these instructions perform different functions, they are of different types. Here are the basic types:
- assignment instruction
- class instantiation instruction
- procedure invocation instructions

and the following statements 
- conditional statement
- evaluation statement
- switch statement
- while statement


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

These two forms are equivalent.

## The deterministic factor

While the assignments of values to data elements are always deterministic, the assignment of facts might not always be. Facts might or might not have values at the time of the assignement. Therefore what will happen when we assign a fact to a data element when this fact does not have avalue (is `UNKNOWN`)? The problem is further compounded because a data element always has value. What will be a result of this assignment? 

BizCod implements a special value called `nil` to handle this situation. Consider the following assignment 

```js
  application.creditScore = score.creditScore
```

where `score.creditScore` is a fact. 

If the value of `score.creditScore` is `750` the value of `application.screditScore` will be `750` after this assignement.

If the value of `score.creditScore` is `UNKNOWN` the value of `application.screditScore` will be `nil' after this assignment .

The value `nil` cannot be explicitly assigned to either a data element or a fact.

> add explanation of assigning fact to a fact

>MEP: is it possible to test if a a variable has the value `nil`?
>
>MEP: What happens later if a variable with a value `nil` is used in some other expression?

## nil vs null

What is different between these two special values? The difference is fundamental. 

BizCod uses `nil` is an illegitimate value to handle facts assignments to data elements when the facts are `UNKNOWN`. Since data elements must always have value. 
On the other hand, `null` is a legitimate value that can be assigned to either data element or fact. It is a value like any other value.

>MEP so a regular data element can be x or nil or null (but cannot be UNKNOWN)? 
>
>MEP: Whereas a fact can be x or null or UNKNOWN (but cannot be nil)? Or is null excluded from facts?
>
# Class instantiation instruction

In a computer system, any time a new context is created based on some model, it is said that the model has been instantiated. In practice, this instance usually has a data structure in common with other instances, but the values stored in the instances are separate. Changing the values in one instance will then not interfere with the values of some other instance.

An instance is a specific realization of any object. An object may be varied in a number of ways. Each realized variation of that object is an instance. The creation of a realized instance is called instantiation.

Instantiation instruction creates an instance of a class of data. Since class is just a template for data creation it does not hold any value; it is not a container.  To create  a particular instance, BizCod provides `set instance` instruction. Here is an example:


```js
 set account to instance of Account

```

or, alternatively

```js
 account = Account::create

```

This instruction creates an instance of class `Account` and sets the value of variable `account` to this instance.

>MEP: The variable `account` may be an attribute of a class or a local variable in a function or procedure.



# Procedures

A procedure is a collection of instructions that are grouped into a coherent unit. This group of instructions (procedure) can be called and run. Usually, the procedure defines:
- input arguments
- output arguments
- procedure body

# Procedure invocation (call) instruction

A procedure call instruction is simnply invocation a define dprocedure with the respective argument list if defined. 

```js
  <procedure-name>(<list-of-arguments>)
```

Here is a simple example of a procedure call (invocation) 


```js
  calculateInterestRate()
```

or with the arguments


```js
  assessRisk(income, creditScore, outstandingDebt)
```



# Statements 



# Conditional statement

The purpose of conditional statement is to provide means to process a block of instructions based on certain conditions. If these conditions are met the block will be executed. If they are not met the block will not be executed. Optionally, conditional instruction can define the block of instructions that will be executed if the conditions are not met. 
Here is a general format of conditional instruction



```js
  if <condition> then
     <block>
  else 
     <block>
  end 

```

You use logical operations to conditionally execute your intended actions. This is the ‘then’ part of the if statement that specifies what should be done when the ‘if’ property is true.
Here, you can use properties such as ‘pass value to trigger’, ‘next loop’, ‘comment’ and so on.
Meanwhile, ‘else’ outlines what the computer should do when the ‘if’ property is false

Here is an example a simple conditional statement that performs an action if the condition evaluates to `true`

```js

 if (customerProfile.income => 200000) then
   customerProfile.status = 'GOLD' 
 end
 ```
 
 This statement will set the `status` of `customerProfile` to `GOLD` if the income is at least 200000.  
 In the folowing example, If statement will set the status to `REGULAR` if the income is less than 200000.
 
```js

 if (customerProfile.income => 200000) then
   customerProfile.status = 'GOLD' 
 else 
   customerProfile.status = 'REGULAR' 
 end
 ```



# Evaluate statement

Use the evaluate statement to execute one or many code blocks depending on a logical condition. Evaluate statement is an extension of IF statement and provides better way to test for various conditions in one statement instead of compounding many if conditions. 


```js
evaluate 
  <condition>
     <block>
     break;
    
  <condition>
     <block>
     break;
    
  .....
  
  <condition>
    <block>
    break;  
end
```

To illustrate this mechanism, let's set up a credit score depending on the credit rating


```js
evaluate 
  (credit.rating between 580, 669 )
     credit.score = 'Fair'
     break;
    
   (credit.rating between 670, 739 )
     credit.score = 'Good'
     break;
     
   (credit.rating between 740, 799 )
     credit.score = 'Very Good'
     break;
    
   (credit.rating between 800, 855 )
     credit.score = 'Exceptional'
     break; 
end
```
>MEP: What happens if the conditions should overlap? Is it considered an error or could both actions be performed
>
>MEP: I'm thinking here of a situation where, instead of setting an attribute to a single value, we might add various values to a total.
>
>MEP: What happens if none of the conditions applies? Should there be an `other`category
>
>MEP: Suppose the first evaluate said `between 580, 668)` instead of `between 580, 669`. So the 699 case is missing.
>
>MEP: Will there be any mechanism to identify and add any missing conditions?
>
>MEP: Also what about the option to compress when several actions are the same?

# Switch statement
Use the switch statement to select one of many code blocks to be executed.


```js
switch(expression) {
  case x:
    // code block
    break
  case y:
    // code block
    break
  default:
    // code block
}
```

This is how it works:

- switch expression is evaluated once
- value of the expression is compared with the values of each case
- if there is a match, the associated block of code is executed
- if there is no match, the default code block is executed.

When BizCod reaches a break keyword, it breaks out of the switch block.
This will stop the execution inside the switch block.
It is not necessary to break the last case in a switch block. The block breaks (ends) there anyway.

In this example, switch statement translates day name from English to French. 

```js

 switch (day)
 
    case 'Monday':
      jour = 'Lundi'
      break
      
    case 'Tuesday':
      jour = 'Mardi'
      break
      
    case 'Wednesday':
      jour = 'Mercredi'
      break
      
    case 'Thursday':
      jour = 'Jeudi'
      break
      
    case 'Friday':
      jour = 'Vendredi'
      break
      
    case 'Sunday':
      jour = 'Dimanche'
      break
 
 end 
```
>MEP: Can the case values also be ranges or must they be discrete values? Eg Saturday or Sunday jour = 'le Weekend'
>
>MEP: If the expression evaluates to true or false are the case values automatically constrained?
>
>MEP: What happens if the expression is a `fact` and could have a value of UNKNOWN
>
>MEP: Can `expression` be a function call?
>
>MEP: Is the value case sensitive? And if so is there a way to easily handle mismatched cases that would otherwise be correct?

# Repetition statement

Repetition is a special kind of conditional statement. The purpose of repetition is to execute a block of code in a loop as long as the condition remains satisfied (or met, or true)
The `while` statement creates a loop that executes a specified statement until the test condition evaluates to false. The condition is evaluated before executing the statement.


```js
  while  <condition> 
     <block>
```

In the following example, the code in the loop will run, over and over again, as long as a variable (i) is less than 10:

```js
while (i < 10) {
  text += "The number is " + i;
  i++;
}
```

>MEP: If you had a 1:N association (Eg `Customer->Account`) is there a repetition mechanism that would iterate over the collection of Accounts? 
>
>MEP: Maybe this is handled somewhere else?
>
>MEP: How might it look if you had `Customer->Account->Transaction`
____________________
2021 AionNEXT Corporation<br>
we build soft and you build app | <b>soft4app</b>
