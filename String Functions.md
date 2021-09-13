# String Functions

Function|Example
-|-
 +|`'THE' + ' '  + 'CAT'` returns  'THE CAT' concatenate two strings
 <|`'CAT' < 'CAR' ` returns true compare two strings
 <=|
 <>|
 '>'|
 '>='|
 .alphabet|`'THE CAT SAT ON THE MAT'.alphabet` returns ' ACEHMNOST'
 .characterAt(i)|`'THE CAT SAT ON THE MAT'.characterAt(6)` returns A
 .charsIn(validset)|`'THE CAT SAT ON THE MAT'.charsIn(' ACEHMNOST')` returns true
 .concat(string)|`'THE CAT SAT'.concat(' ON THE MAT')` returns 'THE CAT SAT ON THE MAT'
 .contains(string)|`'THE CAT SAT ON THE MAT'.contains('THE')` returns 2
 .                |`'THe CAT SAT ON THE MAT'.contains('THE')` returns 1
 .                |`'THE CaT SAT oN THE MaT'.toUpper.contains('Mat'.toUpper)` returns 1
 .                |`'THE CaT SAT oN THE MaT'.toUpper.contains('Man'.toUpper)` returns 0
 .containsBlanks  |`' THE CAT SAT ON THE MAT '.containsBlanks` returns 7
 .containsSpecialChars|`' THE CAT SAT ON THE !@%% MAT '.containsSpecialChars` returns 4
 .endsWith(string)|`' THE CAT SAT ON THE MAT'.endsWith('AT')` returns true
 .equals(string)|`'THE CAT SAT ON THE MAT'.equals('THe CAT SAT ON THE MAT')` returns false
 .equalsIgnoreCase(string)|`'THE CAT SAT ON THE MAT'.equalsIgnoreCase('THe CAT SAT ON THE MAT')` returns true
 .in string1..string2|`'CAR'.in 'CA'...'CATEGORY'` returns true
 .indexOf(substring)|`'THE CAT SAT ON THE MAT'.index of('THE')` returns 1
 .isInteger|`'42'.isInteger` returns true
 .isDecimal|`'3.14'.isDecimal` returns true
 .isDateTime|`'12/1/2017 12:00:00 AM'.isDateTime` returns true
 .distance(string)|`'https://www.wellsfargo.com/'.distance('https://www.wellsforgo.com/')` returns 1. Number of edits to convert. Used in fraud detection. Uses Levenstein
 .toProtein|`'GUUCACUUAACACCCGAGAAAUGA'.toProtein` returns Val-His-Leu-Thr-Pro-**Glu**-Lys-. the protein(s) coded by a string containing only A,C,U,G
 .         |`'GUUCACUUAACACCCGUGAAAUGA'.toProtein` returns Val-His-Leu-Thr-Pro-**Val**-Lys-. Sickle Cell - Mutation -  GAG is replaced by GUG in the sickle cell
 .regexMatches(regex)|returns true if the string matches the regular expression
 .regexReplace(regex,string)|anything that matches regex is replaced with string. 
 .replace(stringToBeReplaced,replacementString|`'THE CAT SAT ON THE MAT'.replace('THE','A')` returns 'A CAT SAT ON A MAT'
 .size|`'THE CAT SAT ON THE MAT'.size` returns 22
 .soundex|`'Robert'.soundex = 'Rupert'.soundex'` returns true. Numeric value representing the phonetic sound of the string. 'R163' in this example
 .metaphone|`'mississipi'.metaphone='mosasupy'.metaphone` returns  true  since both produce 'MSSP'. 
 .startsWith(string)|`'THE CAT SAT ON THE MAT'.startsWith('THE C')` returns true
 .toDateTime|`'12/1/2017 12:00:00 AM'.toDateTime` returns null if the string cannot be converted; otherwise returns the datetime
 .toDecimal|`'3.1415'.toDecimal` returns 3.1415. returns null if the string cannot be converted; otherwise returns the decimal value
 .toInteger|`'42'.toInteger` returns 42. returns null if the string cannot be converted; otherwise returns the integer value
 .toLower|`'THE CAT SAT ON THE MAT'.toLower` returns 'the cat sat on the mat'
 .toUpper|`'the cat sat on the mat'.toUpper` returns 'THE CAT SAT ON THE MAT'
 .trimSpaces|`'    THE CAT SAT ON THE MAT     '.trimSpaces` returns 'THE CAT SAT ON THE MAT' 

Note: Any string literal in the examples may be replaced with any expression that evaluates to a string. Even a complex one involving collections.
For example `person.gender[age>65]->sortedBy(age)->first.equalsIgnoreCase('male')`
