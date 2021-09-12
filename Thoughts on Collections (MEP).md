# Collections

I created this list of operations on collections from the point of view of what business functions a person might want to perform.
I've also included some samples of what the syntax might look like. 
Do you think this is worth pursuing? 
Mike

## Operations on Collections
A collection can be sequenced on one or more attributes using ->sortedBy or ->sortedByDesc

Can return any data type including a collection.

General structure can be
`<collection name>[<filter expression>]-><operations>`  or  `<collection name>.<attribute name>[<filter expression>]-><operations>`
  
Business Question                                                 | Possible Implementation
----------------------------------------------------------------- | ---------------------------------------------------------------------------------------
Is there any person over 65?                                      | `person[age>65]->notEmpty`
Are there any persons between 13 and 19?                          | `person[age in 13..19]->notEmpty`
Are there more than 2 persons between 20 and 65?                  | `person[age in 20..65]->size > 2`
How many persons between 20 and 65?                               | `n=person[age in 20..65]->size`
Find males under 13                                               | `malesUnder13=person[age <13, gender='male']`
Are all the people over 65 male?                                  | `person.gender[age>65]->allContain('male')`
Are there any males over 65 ?                                     | `person[age>65,gender='male']->notEmpty`
Are there any non-males over 65?                                  | `person[age>65,gender<>'male']->notEmpty`
What is the highest income for males over 65?                     | `highest=person.income[age>65,gender='male']->max`
Is the youngest person over 65 a male?                            | `person.gender[age>65]->sortedBy(age)->first = 'male'`
What is the sum of incomes for people over 65                     | `incomeSum=person.income[age>65]->sum`
Is the lowest income for over 65s greater than zero?              | `person.income[age>65]->min >0`
What is the average age of the oldest 3 males between 21 and 45?  | `avgAge=person[age in 21..45, gender='male']->sortedBy(age)->first(3) ->avg`
Which are the oldest 3 males between 21 and 45?                   | `oldest=person[age in 21..45, gender='male']->sortedBy(age)->first(3)`
What is the sum of the incomes for the oldest N males?            | `incomeSum=person.income[gender='male']->sortedByDesc(age)->first(N)->sum`
What state does the youngest person over 65 live in?              | `state=person.state[age>65]->sortedBy(age)->first`
Find all the males over 65.                                       | `seniorMales=person[gender=’male’,age>65]` result is a collection saved for further use
 Then find their average income.                                  | `seniorMaleAvgIncome=seniorMales.income->avg`     result is a value
Is the highest income of the youngest 5 males greater than 10000? | `person.income[gender='male']->sortedBy(age)->first(5)->sortedByDesc(income)->first > 10000`
Is person with the lowest income over parm.x a parm.gender        | `person.gender[income > parm.x] ->sortedBy(income)->first = parm.gender`
Is there a male over 65?                                          | `person[age>65]->exists(gender='male')`
or alternatively                                                  | `person->exists(gender='male',age>65)`
.                                                                 |
Find the sum of the two lowest book prices                        | `lowest_two=Books->sortedBy(price)->at(1).price + Books->sortedBy(price)->at(2).price`
or                                                                | `lowest_two=Books->sortedBy(price)->first(2).price->sum`
or                                                                | `lowest_two=Books->subSequence(1,2).price->sum`

Person->iterate(<any expression>)
Eg Person->iterate(Person.


## Basic Collection Operators
size, iterator(), add() or +=, remove() or -=, clear

## Single Collection operators
  Operation|Example
  -|-
->exists|
->forall|
->isEmpty|
->notEmpty|
->size|
->sortedBy|
->sortedByDesc|
## Sequenced Collection operators
  Collection must be sorted eg `sortedCollection=collection->sortedBy(age)`
  
  Operation|Example
  -|-
->at(n)|
->next|
->first(n)|
->last(n)|
->subSequence(i,j)|

## Multiple Collection operators (collections of same type)
  Assume A={red,green,blue} and B={red,yellow,blue}
  
  Operation|Example|Result
  -|-|-
->union              | `C=A->union(B)`         |C={red,green,yellow,blue}
->intersection       | `C=A->intersection(B)`  |C={red,blue}
->difference         | `C=A->diff(B)`          |C={green.yellow}

## Multiple Collection operators (collections of different type but implementing a common interface)
 Operation|Example
  -|-
->merge      |     `transportation=cars->merge(boats)->merge(planes)`

## Attribute specific operators:
   Operation|Example
  -|-
->max
->min
->avg
->allContain(<string>)
->uniqueCount(<string>)

## Filters (produce subsets of a collection)
[list of any valid expression involving attributes of the collection that evaluates to boolean]
