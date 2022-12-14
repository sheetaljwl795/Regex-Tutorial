#  Computer Science for JavaScripte: Regex-Tutorial

### Summery

Regular expressions are a way to describe patterns in a string data. They form a small language of its own, which is a part of many programming languages like Javascript, Perl, Python, Php, and Java.There are two ways to create a regular expression in Javascript. It can be either created with RegExp constructor, or by using forward slashes ( / ) to enclose the pattern.
A character class are matches any one of the enclosed characters. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character enclosed in the square brackets, it is taken as a literal hyphen to be included in the character class as a normal character.RegEx is really good at matching patterns and extracting values from found patterns. Matching URL,find output/input data,email,password,username.
For email use- /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

# Table Content
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping-Constructs](#grouping-constructs)
- [OR Operator](#or-operator)
- [Bracket-Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Back-references](#back-references)
- [Greedy-and-Lazy-Match](#greedy-and-lazy-match)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

# Regex Components

### Anchors

"^" is used for matching the beginning of input. If the multiline flag is set to true, also matches immediately after a line break character. For example, /^A/ does not match the "A" in "an A", but does match the first "A" in "An A".
For email -These are special sequences which match an empty substring:
^ matches at the beginning of the target string
$ matches at the end of the target string
\b matches on a word boundary, i.e., the previous or subsequent character is not a word character

### Quantifiers

Quantifiers indicate numbers of characters or expressions to match. 
For eg ([a-z0-9_\.-]+) It will match ny string that contains a-z, 0-9, _, ., or -. The quantifier + means that it has to contain at least one of this in order to have a match.? may also be used as Qualifier. Eg x(?=y)can be used Matches "x" only if "x" is followed by "y". For example, /Jack(?=Sprat)/ matches "Jack" only if it is followed by "Sprat"./Jack(?=Sprat|Frost)/ matches "Jack" only if it is followed by "Sprat" or "Frost". However, neither "Sprat" nor "Frost" is part of the match results.


### Grouping Constructs

Groups use the ( ) symbols (like alternations, but the | symbol is not needed). They are useful for creating blocks of patterns, so you can apply repetitions or other modifiers to them as a whole. In the pattern ([a-x]{3}[0-9])+, the + metacharacter is applied to the whole group.
For email it will try to find all the groups 1)([a-z0-9_\.-]+) 2)([\da-z\.-]+) 3)([a-z\.]{2,6})

### Or Operator

* `|` Acts like a boolean OR. Matches the expression before or after the |.
It can operate within a group, or on a whole expression. The patterns will be tested in order. Just as in java will match either set of characters. It will look for this OR that.

 
  ### Bracket Expressions
  
  Brackets indicate a set of characters to match. Any individual character between the brackets will match, and you can also use a hyphen to define a set.For email /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
  
e.g to find three bracket expressions: [0-9], [a-z], and [_.-].[0-9] denotes any number between 0 and 9. [a-z] denotes any lowercase leter from a to z. If you wanted to also include uppercase letters, you would need to use [a-zA-Z]. Lastly, [.-] denotes the special characters that can be used: underscore (), backwards slash (/), period (.), and dash (-).

  
  ### Character Classes
  A character class can define a set of characters that can occur in input strings to fullfill a match. The bracket expressions mentioned previously are examples of this.
  e.g 1)[abcd] is the same as [a-d]. They match the "b" in "brisket", and the "a" or the "c" in "arch", but not the "-" (hyphen) in "non-profit".
  2)"." Matches any single character except line terminators: \n, \r, \u2028 or \u2029. For example, /.y/ matches "my" and "ay", but not "yes", in "yes make my day".
Inside a character class, the dot loses its special meaning and matches a literal dot.
  3)"\" For characters that are usually treated literally, indicates that the next character is special and not to be interpreted literally. For example, /b/ matches the character "b". By placing a backslash in front of "b", that is by using /\b/, the character becomes special to mean match a word boundary.
For characters that are usually treated specially, indicates that the next character is not special and should be interpreted literally. For example, "*" is a special character that means 0 or more occurrences of the preceding character should be matched; for example, /a*/ means match 0 or more "a"s. To match * literally, precede it with a backslash; for example, /a\*/ matches "a*".
### Flags
Regular expressions may have flags that affect the search.Expression flags change how the expression is interpreted.

* `i` Ignores case
* `g` Global search retain the index of the last match, allowing subsequent searches to start from the end of the previous match. Without the global flag, subsequent searches will return the same match.
* `m` Multiline flag When the multiline flag is enabled, beginning and end anchors (^ and $) will match the start and end of a line, instead of the start and end of the whole string.
* `u` Unicode
* `y` The expression will only match from its lastIndex position and ignores the global (g) flag if set. Because each search in RegExr is discrete, this flag has no further impact on the displayed results.
* `s` Dot (.) will match any character, including newline.


### Back-references

Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag.

For Example: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ This regex contains only one pair of parentheses, which capture the string matched by [a-z][0-9]*. This is the opening HTML tag. The backreference \1 references the first capturing group. \1 matches the exact same text that was matched by the first capturing group. The / before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match.

### Greedy and Lazy Match

* 'Greedy' means matching the longest possible string.
    A Greedy quantifier tells the engine to match as many instances of its quantified token or subpattern as possible. This behavior is called greedy.

* 'Lazy' means matching the shortest possible string.
    A lazy quantifier tells the engine to match as few of the quantified tokens as needed. As you'll see in the table below, a regular quantifier is made lazy by appending a ? question mark to it.

### Look-ahead and Look-behind

(?=ABC) is a postive lookahead and it matches a group after the main expression without including it in the result.

(?!ABC) is a negitive lookahead and it specifies a group that can not match after the main expression (if it matches, the result is discarded)

(?<=ABC>) is a postive lookbehind and matches a group before the main expression without including it in the result.

(?<!ABC) is a negitive lookbehind and Specifies a group that can not match before the main expression (if it matches, the result is discarded).
 
  
  ## Sources
  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Cheatsheet
  https://www.rexegg.com/regex-quickstart.html#morequants
  
  ## Author
  
 This is Sheetal Jawale pursuing her current career from QA to full-stack engineer.IT profession for the last 8 years by performing various roles.
 Here is my GitHub URL- https://github.com/sheetaljwl795/ 

  
  


