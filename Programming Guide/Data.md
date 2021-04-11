

# BizCod Data



A data element (datum) is a container that holds (stores) a value. This value can take different form. This data form (or representation) is called a type or more specifically a data type. Furthermore, each data element has its associated name and type.

For example, data element can store text, number or date. 

## Primitive data types

As mentioned previously, the data properties are typed to represent different forms of data. To begin with and create a basic data type foundation, BizCod provides data types the are 'internally' defined. These internal types are called primitive types. The following table provides the basic primitive data types: 

| primitive data type                           | description   |
|--------------------------------|------------------------------------------------------------------------|
| ID                             |  this data type stores a unique ID number. It is usually used for identification purpose to identify objects that are globally unique                    |
| Text                    | textual data to store the text such as 'John Roberts' 'commercial account' and so on                                          | 
| Number                     | number to store numbers such as 100, 3000. The number can be either positive or negative                                        | 
| Decimal                     | decimal data that are desiged to store decimal numbers such as 213213.45 , -24324.67                                          | 
| Date                     | to store then date                                      | 
| Logical                     | logical type that can be either <b>true</b> or <b>false</b>                                        | 

Note that this table provides a partial list of data types only. 

## Facts

By definition, a data element stores a value and its value is always known regardless of what it is. In BizCod, it means that its `knowability factor` is always `KNOWN`. While this is always true for regular data elements, it is not always true for special BizCod data elements called `facts`. Facts are data elements but they might or might not hold a value. Its knowability factor is either `KNOWN` or `UNKNOWN`. There is a compelling reason behind this feature that applies specifically to Knowledge elements that we will explain later.
> Essentially, facts are data elements but they might (or might not) hold a value and its knowability factor might be programmatically changed between KNOWN and UNKNOWN. Their default knowability factor is UNKNOWN. Once the value is assigned to a fact it becomes known.
> 

In BizCod, facts are defined by the keyword `fact`.

```js
    fact creditScore Text
```

here, the fact **creditScore** is of type `Text` and its defaut value is `UNKNWOWN`.


## Data model

Data elements can be grouped together to form a coherent unit of information. This unit is called a class of data (or model) and the data elements that form this unit are called properties. Therefore, a class is a collection (grouping) of data properties. That class of data is a data type as well. Therefore, in addition to primitive data types, a user can define its own data types by defining classes of data (models)

Moving forward, let's provide a practical application of BizCod data model. We will use the Banking system to define the data model. 
Here we will define a Account class to hold the basic information about the account


```js
define model Account
    id ID,
    name Text,
    accountType Text    
;
```
In simple terms, this BzCod statement translates into :
> define a data model (class) Account with the following properties id, name and account. These properties are of different types (ID, Text and Text respectively) to represent  different forms of data.
> 
## Instantiation

The data model defines the data structure that serves as a bluprint to create a concrete data called instances. The instantiation is a process of creating a concrete instances of an abstract data model.

## Inheritance

In BizCod, data models can be 'composed' using already defined data. This is very useful when some data models share common properties. In order to alleviate the problem of redefining the same data segments number of times, BizCod provides a mechanism to inherit these already defined data models in other data structures. This mechanism is called inheritance where one data model inherits properties from another data model. This two data models are in subclass relationship where a data model that inherits properties from the parent class is called a subclass of that parent class. 

Let's illustrate this very simple concept by defining an account type **SavingsAccont** which is an account with additional property `interestRate`. Here we can define this account as follows

```js
define model InterestAccount
    id ID,
    name Text,
    accountType Text    
    interestRate Decimal
;
```

`Investment Account` shares three properties with already defined data model `Account`. This data model can be redefined using inheritance mechanism to inherit these 3 properties from `Account` data model . 

```js
define model InterestAccount is Account
    interestRate Decimal
;
```

In addition, BizCod supports multiple inreritance so it is possible that one data model inherits properties from many data models. Here is an example

```js
define model SavingsAccount is Account, InterestAccount
    calcPeriod Text
;
```

`SavingsAccount` inherits properties from `Account` and `InterestAccount` data models. Here is how this data models would look like fully defined

```js
define model SavingsAccount
    id ID,
    name Text,
    accountType Text,
    interestRate Decimal,    
    calcPeriod Text
;
```

In addition, inheritance mechanism provides a convenient way to redefine the already defined data models that might otherwise be known by other names.

```js
define model InterestBearingAccount is SavingsAccount
```

here, `InterestBearingAccount` is **the same as** `SavingsAccount` and can be used interchangeably.

## Multiple inheritance conflict

Multiple inheritance represents a powerful way to reuse the already defined data elemenst and relieves the programmer from mandate task of redefining the same data elements (properties) over and over. While being very powerful, multiple inheritance might lead to unresolved problems where the same data element (property) is redefined multiple times (at least twice) with different data types in the parent classes (models) . 

Consider these two definitions 

```js
define 
    model Account
        id ID,
        name Text,
        accountType Text    
        
    model InterestAccount
        id Number,
        name Text,
        accountType Text,    
        interestRate Decimal
;
```

When BizCod processes data model defintions that define inheritance it attempts to resolve the inheritance. What it means is that it applies multpiple inheritance consitency rules in order to resolve data model inheritance. When these rules fail, it generates an error and invalidates the entire program.

The followig definition would not be able to resolve because the property `id` is defined with different data types (ID in Account and Number in InterestAccount) in the parent classes:

```js
define model SavingsAccount is Account, InterestAccount
    calcPeriod Text
;
```

This definition is invalid and BizCod will not be able to resolve it.


# Methods

While data models define data structures and provide the information about the business objects, they alone do not provide any means to manipuate (process) its content. A method is simply a function that provides means to process the data model structures and are attached to the data model

```js

define 
    method Account::isCommercialAccount(type Text) -> boolean 
        if (Account.type = type) then
            return true
        end
        return false

```

Here, a method `isCommercialAccount` is defined on data model `Account` and accepts argument `type` (Text) and returns logical value.

Methods are simply [functions](Function.md) defined on the data model to process the data model content. here isa practical illustration of that concept:

```js
    define Account:init(name Text, ssn Text, )  
        
    
```


# Data domain

once the data models are defined they can be grouped into coherent set of data models called object domain. A domain is a collection of data models that provide another form of abstraction to operate at the data model groups and capture the dependencies between the data models. Here are the building block of data domains

| element                           | description   |
|--------------------------------|------------------------------------------------------------------------|
| models                        |  data models that belong to the data domain                    |
| arrows                    | the transformations (mapping) between the models                                          | 
| relations                     | the relations between the data models in the domain                                        | 
| associations                     | the associations between the data models in the domain                                        | 



```js
    define domain BankingDomain {
        Account, CommerciaAccount, InvestmentAccount, Branch
}
```


```js
    define arrow <name>(<args>):A->B     
        <body>
```


```js
    define association between A.asdasdasd and B.asdsadsadsad one-to-many
        asdsadsad, 
        asdasdsads, 
        asdsad, 
        asdsadsadsad, 
        asdasdsad Text
```

```js
    define diagram <name>(<args>) { asdcxasdsadsad, asdasdsa, asdsadsad, asdasdasdsa }
```

____________________
2022 AionNEXT Corporation<br>
we build soft and you build app | <b>soft4app</b>
