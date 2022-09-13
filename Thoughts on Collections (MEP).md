# Collections

I created this list of operations on collections from the point of view of what business functions a person might want to perform.
I've also included some samples of what the syntax might look like. 
Do you think this is worth pursuing? :smiley:
Mike

## Operations on Collections
A collection can be sequenced on one or more attributes using ->sortedBy or ->sortedByDesc

Can return any data type including a collection.

General structure can be
`<collection name>[<filter expression>]-><operations>`  or  `<collection name>.<attribute name>[<filter expression>]-><operations>`
  
Business Question                                                 | Possible Implementation
----------------------------------------------------------------- | ---------------------------------------------------------------------------------------
Is there any person over 65?                                      | `{p in Person,age>65}->notEmpty`                   returns T or F
Are there any persons between 13 and 19?                          | `{p in Person,age in [13..19]}->notEmpty`          returns T or F
Are there more than 2 persons between 20 and 65?                  | `{p in Person,age in [20..65]}->size > 2`          returns T or F
How many persons between 20 and 65?                               | `n={p in Person,age in [20..65]}->size`            sets the value of n
Find males under 13                                               | `mu13={p in Person,age<13, gender='male'}`         creates a collection named mu13
Are all the people over 65 male?                                  | `{p in Person,age>65}.gender->allContain('male')`  returns T or F
Are there any males over 65 ?                                     | `{p in Person,age>65,gender='male'}->notEmpty`     returns T or F
Are there any non-males over 65?                                  | `{p in Person,age>65,gender<>'male'}->notEmpty`
What is the highest income for males over 65?                     | `highest={p in Person,age>65,gender='male'}.income->max`
Is the youngest person over 65 a male?                            | `{p in Person,age>65}->sortedBy(age)->first = 'male'`returns T or F
What is the sum of incomes for people over 65                     | `incomeSum={p in Person,age>65}.income->sum`        returns the sum of incomes
Is the lowest income for over 65s greater than zero?              | `{p in Person,age>65}.income->min >0`               returns T or F
What is the average age of the oldest 3 males between 21 and 45?  | `avgAge={p in Person,age in [20..65],gender='male'}->sortedBy(age)->first(3)->avg`
Which are the oldest 3 males between 21 and 45?                   | `oldest={p in Person,age in [20..65],gender='male'}->sortedBy(age)->first(3)` collection
What is the sum of the incomes for the oldest N males?            | `incomeSum={p in Person,gender='male'}->sortedByDesc(age)->first(N)->sum`
What state does the youngest person over 65 live in?              | `state={p in Person,age>65}.state->sortedBy(age)->first`
Find all the males over 65.                                       | `seniorMales={p in Person,age>65,gender='male'}` collection saved for further use
Then find their average income.                                   | `seniorMaleAvgIncome=seniorMales.income->avg`     result is a value
Is the highest income of the oldest 5 persons greater than 10000? | `{p in Person}.income->sortedBy(age)->first(5)->sortedBy(income)->first>10000`
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
->merge      |     `transportation=cars->merge(boats)->merge(planes)` or `transportation=cars+boats+planes`
.            |     `transportation=cars[seats>4,insured=True]->merge(boats[type='hovercraft',seaworthy=True])->merge(planes[age<5])` 
  
## Attribute specific operators:
   Operation|Example
  -|-
->max
->min
->avg
->allContain(<string>)|`Person[age>65].gender->allContain('male')` equivalent to `Person->forAll(age>65,gender='male')`
->uniqueCount(<string>)|`Person[age in 18..65].gender.uniqueCount`

## Filters (produce subsets of a collection)
[list of any valid expression involving attributes of the collection that evaluates to boolean]
  
  Person[age>65] just those instances where age >65
  Person is equivalent to Person[] and Person[*] meaning every instance of the ckass
  Person[n] any n arbitrary instances (can't think why we'd need this yet)
  
  Person[age>65,gender='male'] allows the filters to be applied in any order (perhaps even in parallel) and is equivalent to Person[age>65][gender='male'] which requires the age filter to be applied first and then the gender filter is applied to the results. Not sure if it makes a huge difference
