# BizCod Knowledge 

BizCod programming language provides a powerful mechanism to capture and represent business knowledge. This representation comes in the form of Knowledge Base. Just like the data is captured in the data bases so is the knowledge captured in the knowledge base.



## Rules

Rule is a fundamental element of knowledge base. Rule processes the data and produce side-effects. Side efects are the results of rules applicationa to the data. 
Here is a formal definition of a rule

```js
  define 
    rule <rule-name"(<args>) 
      condition
        <logical-condition>
        
      action
        <instructions-block>
      
```
Let's ullistrates this concept using the following example of asseinga customer's status. Heer we will capture the business knowledge about customers status using rules 

```js

  define
    rule customerStatus(customer Customer) 
      condition
        customer.income > 200000
      action
        customer.status = 'EXCLUSIVE'  
```

This rules captures business knowledge about the customer's status. 

## Knowledge Base


```js
  define 
    rule asdasdsad(asdsad, asdsadsad, asdsadsa,asdasdas) 
      condition
        asdasd.asdsad > asdasdsad.asdsad or sadsadsad. asdasd = "123123123asdas" 
        
      action
        asdsadsad.asdasdsa = 12321.23432
      
```

```js
  define 
    ruleset asdasdasdsad
      facts 
        asdsad, asdsadsad, asdsad, asdasdsad
      rules 
        asdsadsad(asdsad, asdsad, asdsad)
        aSDSADSADSAD(ASDSAD,ASDSADASD)
      
```

```js

  define 
    knowledge-base FraudDetectionRules
      facts 
        asdasdsad Asadsad,  
        asdsadasda Hasdsadsad, 
        asdasdsad Adsafdsfdsfdsf
        
      rules 
      
        asdsadasdsad(asdasdsad, asdsadasda, asdasdsad
        
```

When knowedge bases are indedependent and they can be excuted at the same time because their excutions are not dependent on each other. BizCod privides means to execute them in parallel


```js

  define knowledge-base 
    ParallelKB (data1 Data1, data2 Data2, data3 Data3, data4 Data4) 
        kb1(data1, data2, data3) 
        kb2(data3, data4)
        kb4(data1, data2, data3, data4       
        
```


