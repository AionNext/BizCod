
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
