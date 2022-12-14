#  Computer Science for JavaScripte: Regex-Tutorial

### Summery

Regular expressions are a way to describe patterns in a string data. They form a small language of its own, which is a part of many programming languages like Javascript, Perl, Python, Php, and Java.There are two ways to create a regular expression in Javascript. It can be either created with RegExp constructor, or by using forward slashes ( / ) to enclose the pattern.
A character class are matches any one of the enclosed characters. You can specify a range of characters by using a hyphen, but if the hyphen appears as the first or last character enclosed in the square brackets, it is taken as a literal hyphen to be included in the character class as a normal character.RegEx is really good at matching patterns and extracting values from found patterns. Matching URL,find output/input data,email,password,username. For email use- /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

# Regex Components

### Anchors

"^" is used for matching the beginning of input. If the multiline flag is set to true, also matches immediately after a line break character. For example, /^A/ does not match the "A" in "an A", but does match the first "A" in "An A".
For email 
These are special sequences which match an empty substring:
^ matches at the beginning of the target string
$ matches at the end of the target string
\b matches on a word boundary, i.e., the previous or subsequent character is not a word character
### Quantifiers

? may also be used as Qualifier. Eg x(?=y)can be used Matches "x" only if "x" is followed by "y". For example, /Jack(?=Sprat)/ matches "Jack" only if it is followed by "Sprat"./Jack(?=Sprat|Frost)/ matches "Jack" only if it is followed by "Sprat" or "Frost". However, neither "Sprat" nor "Frost" is part of the match results.
(?<=y)x is used to Matches "x" only if "x" is preceded by "y". For example, /(?<=Jack)Sprat/ matches "Sprat" only if it is preceded by "Jack". /(?<=Jack|Tom)Sprat/ matches "Sprat" only if it is preceded by "Jack" or "Tom". However, neither "Jack" nor "Tom" is part of the match results.

### Grouping Constructs

We can use (?<Name>x) Matches "x" and stores it on the groups property of the returned matches under the name specified by <Name>. The angle brackets (< and >) are required for group name. To extract the United States area code from a phone number, we could use /\((?<area>\d\d\d)\)/. The resulting number would appear under matches.groups.area.
  
  ### Bracket Expressions
  
  Brackets indicate a set of characters to match. Any individual character between the brackets will match, and you can also use a hyphen to define a set.
  
e.g to find three bracket expressions: [0-9], [a-z], and [_.-].[0-9] denotes any number between 0 and 9. [a-z] denotes any lowercase leter from a to z. If you wanted to also include uppercase letters, you would need to use [a-zA-Z]. Lastly, [.-] denotes the special characters that can be used: underscore (), backwards slash (/), period (.), and dash (-).

  
  ### Character Classes
  A character class can define a set of characters that can occur in input strings to fullfill a match. The bracket expressions mentioned previously are examples of this.
  e.g 1)[abcd] is the same as [a-d]. They match the "b" in "brisket", and the "a" or the "c" in "arch", but not the "-" (hyphen) in "non-profit".
  2)"." Matches any single character except line terminators: \n, \r, \u2028 or \u2029. For example, /.y/ matches "my" and "ay", but not "yes", in "yes make my day".
Inside a character class, the dot loses its special meaning and matches a literal dot.
  3)"\" For characters that are usually treated literally, indicates that the next character is special and not to be interpreted literally. For example, /b/ matches the character "b". By placing a backslash in front of "b", that is by using /\b/, the character becomes special to mean match a word boundary.
For characters that are usually treated specially, indicates that the next character is not special and should be interpreted literally. For example, "*" is a special character that means 0 or more occurrences of the preceding character should be matched; for example, /a*/ means match 0 or more "a"s. To match * literally, precede it with a backslash; for example, /a\*/ matches "a*".
  
### Character Escapes
  1) Escaping Using Backslash - We know that the backslash character is an escape character in Java String literals as well. Therefore, we need to double the backslash character when using it to precede any character (including the \ character itself).
  
  @Test
public void givenRegexWithDotEsc_whenMatchingStr_thenNotMatching() {
    String strInput = "foof";
    String strRegex = "foo\\.";

    assertEquals(false, strInput.matches(strRegex));
}
  
  2) Escaping Using \Q & \E
   we can use \Q and \E to escape the special character. \Q indicates that all characters up to \E needs to be escaped and \E means we need to end the escaping that was started with \Q.
  
  Here, the escaping is done by placing the pipe character between \Q and \E:
  @Test
public void givenRegexWithPipeEscaped_whenSplitStr_thenSplits() {
    String strInput = "foo|bar|hello|world";
    String strRegex = "\\Q|\\E";
    
    assertEquals(4, strInput.split(strRegex).length);
}
  
  
  ## Sources
  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Cheatsheet
  https://www.rexegg.com/regex-quickstart.html#morequants
  
  ## Author
  
 This is Sheetal Jawale pursuing her current career from QA to full-stack engineer.IT profession for the last 8 years by performing various roles.
 Here is my GitHub URL- https://github.com/sheetaljwl795/ 

  
  


