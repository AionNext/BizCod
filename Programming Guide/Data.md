

# BizCod Data

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




```js
define model Account
    id ID,
    name Text,
    accountType Text    
;
```
In simple terms, this BzCod statement translates into :
define a data model (class) Account that has id , name and account type properties. These properties are of different types (ID, Text and Text respectively) to represent different forms of data.

## Inheritance

In BizCod data models can be 'composed' using already defined data. This is very useful, when some data models sher common properties. In order to alleviate the problme of redefing the sam edata mode segment numbe rof times, BizCod provides a mechanis to inherit these alraedy define datas models in other data structure. This mechanism is called inheritance where one data model inherits properties from another inrehited data model. This two data models are in subclass relationship where the data model that inreits the property from the parent class is called subclass of that parent class. Let's illustartes this very simpel concept 

Let's define an accoun type **SavingsAccont** which is an account with additional property `interestRate`. Here we can this account

```js
define model InterestAccount
    id ID,
    name Text,
    accountType Text    
    interestRate Decimal
;
```

`Investmet Account` shares three properties with already define data model `Account`. This data model can be redfined using inheritance mechanism t inherits thes 3 properties from data modedl `Account`. 

```js
define model InterestAccount is Account
    interestRate Decimal
;
```

In addition, BizCod supports multiple inreritance so it is possible that one data model inreits properties form many data models. Here is an example

```js
define model SavingsAccount is Account, InterestAccount
    calcPeriod Text
;
```

`SavingsAccount` inherits properties from `Account` and `InterestAccount` data models. Here is howthis data models would look like fully defined

```js
define model InterestAccount
    id ID,
    name Text,
    accountType Text,
    interestRate Decimal,    
    calcPeriod Text
;
```

