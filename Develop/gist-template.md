# Regex Tutorial - Matching an Email
The goal of this tutorial is to help someone both understand what regex is and also understand how they can use regex to match an email address.  The tutorial will be using language related to Javascript and Node but regex can be used in multiple languages and applications.  In this tutorial we will be using `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` as our example string.

## Summary
Regular expression, or more commonly know as regex, is a sequence of letters, numbers, and characters that define a logical pattern and can be used to compare against a string to determine whether or not the string matches the logical pattern.  If that sounds confusing then the plain english way to explain regex is that it allows you to check if a string has been written correctly by the user.  Examples of this would be email addresses, phone numbers, social security numbers, and url's.  These all have certain characters that are required to be valid inputs and regex can validate whether this is true or not.

## Table of Contents
* [Anchors](#anchors)
* [Quantifiers](#quantifiers)
* [OR Operator](#or-operator)
* [Character Classes](#character-classes)
* [Flags](#flags)
* [Grouping and Capturing](#grouping-and-capturing)
* [Bracket Expressions](#bracket-expressions)
* [Greedy and Lazy Match](#greedy-and-lazy-match)
* [Boundaries](#boundaries)
* [Back-references](#back-references)
* [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
### Anchors
Anchors are used to match a position before of after characters.  For example, in our string the `^` anchor is used to indicate the beginning of the text we are trying to match.  The `$` anchor is used to indicate the end of the text.

### Quantifiers
A quantifier tells the regex engine how many instances of a certain character, group, or character class must be in the user's input in order for the match to be returned as true.  In our example the quantifiers used are `+` and `{2, 6}`.  The `+`quantifier in our example means the regex engine will be looking for at least one of the expressions enclosed in the `[]` that precedes the `+` symbol.  The other quantifier, `{2, 6}`, means there should be between two and six instances of the character or character class preceding it which is `[a-z/.]`.

### OR Operator
Alternation which is more commonly known as the OR operator lets the user match either of two patterns by using the `|` symbol.  More than two patterns can be matched by using multiple `|` symbols between the patterns.  This is actually not used in our example but it is a good regex term to remember.  For example, if you are trying to match a hex value and use the the following regex `/^#?([a-f0-9]{6}|[a-f0-9]{3})$/`, "true" would be returned if the input matched either `[a-f0-9]{6}` OR `[a-f0-9]{3}`.

### Character Classes
A character class is a notation that matches a specific character or symbol from a certain character set.  In our example the character class is `/d` and it is located here `[\da-z\.-]`.  This looks for the match of a single digit.  If the character class was `/s` it would look for a match of whitespace and if the character class was `/w` it would look for a match that is is a word character.

### Flags
Flags are settings in regex that will change or modify the regex engine's searching behavior.  In our example we don't have any flags but we'll still list a few to show how they can be used. `/i` makes the search not case sensitive.  `/g` looks for all matches instead of just the first match.  `/s` enables "dotall" which allows a `.`to match a newline character.  `/y` enables "sticky" mode which will search at the exact position in the text.

### Grouping and Capturing
In regex you can group and capture a string by using `()` where any text between the `()` will be considered a group and put into an array.  This is done a few times in our example `([a-z0-9_\.-]+)`, `([\da-z\.-]+)`, and `([a-z\.]{2,6})`.  This allows us to get a partial match as a separate item in the resulting array and also allows ust to put a quantifier after that parentheses to apply the match to everything in the parentheses.

### Bracket Expressions
Brackets indicate a group of symbols or characters that we are trying to match.  The characters are enclosed in `[]` and the engine will return true if any of the listed characters within the `[]` are matched.  In our example the first bracket expression is `[a-z0-9_\.-]` which means we are trying to match any letter a thru z, any number 0 thru 9, or any character `_`, `-`, or `.`.

### Greedy and Lazy Match
Greedy and Lazy searches will try and match the longest and shortest possible match with a greedy search trying to match the longest and a lazy search trying to match the shortest.  In our example we have two greedy searches, `+` and `{}`, which are located `([a-z0-9_\.-]+)`, `([\da-z\.-]+)`, and `([a-z\.]{2,6})`.  They are greedy because all three try and expand the match as far as they can go.

### Boundaries
The word boundary is signified with a `/b` and is a kind of anchor like a `^` or `$` that will test the position in a string.  There are three different positions that qualify as word boundaries and they are as follows: 1) At the start of a string if the first character is a word character 2) After the last character in a string if the last character is a word character 3) Between two characters in a string if one is a word character and the other is not.  In our example there are no word boundaries.

### Back-references
A back reference in regex identifies a previously matched group and looks for exactly that same text again.  For example, in the search `([abc])/1`, `/1` is the back reference, and it will match the same text that was matched by the first capturing group.

### Look-ahead and Look-behind
Look-ahead and look-behind, which are together referred to as lookaround, will find matches for a pattern that are followed or preceded by a different specific pattern.  We don't have any example of this search in our example but here's one so we can understand it better.  The search `X(?=Y)` means that the engine should look for X, but only if it is followed by Y.

## Author
Thanks so much for reading through the tutorial and I hope you found it helpful.  My name is Nate Schroeder and I'm currently attending the full stack bootcamp through UT Austin.  If you would like to visit more of my work please visit [https://github.com/n8dogg59](https://github.com/n8dogg59).