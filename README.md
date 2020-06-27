


# Cheat Sheet

`.test()`  takes the regex, applies it to a string, and returns a boolean.  
`.replace()`  replaces a substring with another substring and returns the modified string.`.match()`  extracts the actual matches you found in the return array.



## Match literal strings

`/test/`  searches for a literal match of the string.
```
const str = 'test';  
const reg = /test/;  
reg.test(str); // return true
```
## OR (`|`) in literal strings

Search for multiple patterns using the OR operator  `|`.
```
const str = 'second';  
const reg = /first|second/;  
reg.test(str); // return true
```
## Ignore case (`i`)

Use  `i`  to search ignore-case.
```
const str = 'firstClass';  
const reg = /firstclass/i;  
reg.test(str); // return true
```
## Use global (`g`)

Use  `g`  to search or extract a pattern more than once.
```
const str = 'test test';  
const reg = /test/g;  
str.match(reg); // return ['test', 'test']
```
## Match anything with wildcard period (wildcard, dot, period)

The wildcard character  `.`  will match any one character.
```
const str = 'The string is strong';  
const reg = /str./;  
str.match(reg); // return ['stri']
```
## Match a single character with multiple possibilities [ ]

Search for a literal pattern with some flexibility with character classes by using  `/[abei]/`.
```
const str = 'The tree is strong';  
const reg = /t[hr]e/gi;  
str.match(reg); // ['The', 'tre']
```
## Match letters of the alphabet

Search for an alphabet literal pattern by using  `[a-z]`.
```
const str = 'The';  
const reg = /[a-z]+/;  
str.match(reg); // ['he']
```
## Match single characters not specified

Use  `[^ae]`  for sets of characters that you do not want to match.
```
const str = 'Test';  
const reg = /[^ae]/;  
reg.test(str); // true
```
## Match characters that occur one or more times

Use  `**+**`  to match characters that occur at least once and may be repeated.
```
const str = 'the text, the apple';  
const reg = /the+/g;  
str.match(reg); // ['the', 'the']
```
## Match characters that occur zero or more times

The asterisk  `*`  matches characters that occur zero or more times.
```
const str = 'greedy';  
const reg = /e*/;  
reg.test(str); // true
```
## Match beginning string patterns

The caret  `**^**`  is used to search for patterns at the beginning of strings.
```
const str = 'Test';  
const reg = /^A/i;  
reg.test(str); // false
```
## Match ending string patterns (`$`)

Use  `$`  to search for patterns at the end of strings.
```
const str = 'test-id-sDb4r';  
const reg = /-\w{5}$/;  
const result = str.replace(reg, ''); // 'test-id'
```
## Match all letters and numbers

Use  `\w`  as shorthand for character classes that are equal to  `/[A-Za-z0–9_]/`. Include the underscore (`_`) character.
```
const str = 'sDb4r';  
const reg = /\w/;  
reg.test(str); // true
```
## Match everything but letters and numbers

`\W`  search is the opposite of alphanumerics and is equal to  `/[^A-Za-z0–9_]/`.
```
const str = 'sDb4r?';  
const reg = /\W/;  
str.match(reg); // ['?']
```
## Match all numbers /d

`/d` is used to look for digit characters and is equal to  `/[0–9]/`.
```
const str = 'sDb4r?';  
const reg = /\d/;  
str.match(reg); // ['4']
```
## Match all non-numbers

`/D`  is used to look for non-digit characters and is equal to  `/[^0-9]/`.
```
const str = 'sDb4r?';  
const reg = /\D/g;  
str.match(reg); //['s', 'D', 'b', 'r', '?']
```
## Match whitespace  `\s`

Search for whitespace using  `\s`. This pattern not only matches whitespace but also carriage return, tab, form feed, and new line characters. It’s similar to  `\r\t\f\n\v`.

```
const str = 'test string';  
const reg = /\s/;  
str.replace(reg, ' new '); // 'test new string'
```
## Match non-whitespace characters  `\S`

Search for non-whitespace using  `\S`. This pattern will not match whitespace, carriage return, tab, form feed, and new line characters. It’s similar to  `^ \r\t\f\n\v`.

```
const str = 'test string';  
const reg = /test\S/;  
reg.test(str); // false
```
## Find characters with lazy matching (`?`)

`?`  finds the smallest possible part of the string that satisfies the regex pattern.

```
const str = '<h1>Title</h1>';  
const reg = /<.*?>/;  
str.match(reg); // ['<h1>']
```
## Specify the upper and lower number of matches

You can specify the lower and upper number of patterns with quantity specifiers. Quantity specifiers are used with curly brackets: ({ }). You put two numbers between the curly brackets for the lower and upper number of patterns.

```
const str = 'google';  
const str1 = 'gooogle';  
const str2 = 'gogle';  
const reg = /go{2,3}gle/;  
reg.test(str); // true  
reg.test(str2); // false   
reg.test(str1); // true
```
## Specify only the lower number of matches

To specify the lower number of patterns, keep the first number followed by a comma.
```
const str = 'google';  
const str1 = 'gogle';  
const str2 = 'goooogle';  
const reg = /go{2,}gle/;  
reg.test(str); // true   
reg.test(str1); // false  
reg.test(str2); // false
```
## Specify the exact number of matches

To specify a certain number of patterns, just have that one number between the curly brackets.
```
const str = 'heel';  
const str1 = 'heeeeel';  
const reg = /he{2}l/  
reg.test(str); // true  
reg.test(str1); // false
```
## Check for all or none

Sometimes the patterns you want to search for may have parts that may or may not exist.
```
const str = 'favourite';  
const str1 = 'favorite';  
const str2 = 'faver';  
const reg = /favou?/;  
reg.test(str); // true  
reg.test(str1); // true  
reg.test(str2); // false
```
## Positive (`?=…`) and negative (`?!…`) lookahead

_Lookaheads_  are patterns that tell JavaScript to look ahead in your string to check for patterns further along.
```
const str = 'abs123';Positive   
const reg = /(?=\w{2,6})/  
reg.test(str); // trueNegative  
const reg1 = /(?=[a-z]{3})(?!\d{3})/  
reg1.test(str); // true
```

## Adding more Soon!

[Credit to](https://medium.com/better-programming/javascript-regular-expressions-cheatsheet-b55b0d6886e3)
