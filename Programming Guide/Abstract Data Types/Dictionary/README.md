# Dictionary

A dictionary is a general-purpose data structure for storing a group of objects. A dictionary has a set of keys and each key has a single associated value. When presented with a key, the dictionary will return the associated value. In other words, a dictionary is simply a set of key/value pairs.

Here is a formal definition of dictionary in BizCod 

```js
    define dictionary <dictionary-name>
```

Dictionaries support the following operations:

- retrieve a value (depending on language, attempting to retrieve a missing key may give a default value or throw an exception)
- insert or update a value (typically, if the key does not exist in the dictionary, the key-value pair is inserted; if the key already exists, its corresponding value is overwritten with the new one)
- remove a key-value pair
- test for existence of a key
- iteration over dictionary key/value pairs
