
# Data Domain

once the data models are defined they can be grouped into coherent set of data models called object domain. A domain is a collection of data models that provide another form of abstraction to operate at the data model groups and capture the dependencies between the data models. In relational databases, data domain is referred to as data schema.
Here are the building block of data domains

| element                           | description   |
|--------------------------------|------------------------------------------------------------------------|
| models                        |  data models that belong to the data domain                    |
| arrows                    | the transformations (mapping) between the models                                          | 
| relations                     | the relations between the data models in the domain                                        | 
| associations                     | the associations between the data models in the domain                                        | 


## Domain definition

You define a domain by listing the model definitions that are part of this domain. Here is a an example of a domain `BankingDomain` that contains 4 data models

```js
    define domain BankingDomain {
        Account, CommerciaAccount, InvestmentAccount, Branch
}
```

## Arrow definition

Arrow functions operate on a set of class instances (objects). Just like the regular functions operate on a set of objects, arrows take set of objects as arguments. In addition, arrows can accept parameters as well. Here is a general notation of an arrow. 

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
