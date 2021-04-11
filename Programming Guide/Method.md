# BizCod Methods

```js

define 
    method Account::isCommercialAccount(type Text) -> boolean 
        if (Account.type = type) then
            return true
        end
        return false

```

Here, a method `isCommercialAccount` is defined on data model `Account` and accepts argument `type` (Text) and returns logical value.

Methods are simply [functions](Function.md) defined on the data model to process the data model content. here is a practical illustration of that concept:

```js
    define Account:init(name Text, ssn Text, )  
        
    
```
