# RegEx for Matching and Email

A regular expression - or RegEx - "is a sequence of characters that defines a search pattern for text" (The Coding Train - 2.1: Introduction to Regular Expressions) and is used to find instances of non-specific character strings. One such RegEx is matching an email.

## Summary

A regex for matching an email ensures that the charcters entered by a user follow the format of a valid email address. I will explain the different components of this regex and how it is used.
This is an example of a regex for matching an email:
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

All regex's are wrapped in "/" characters because it is a literal. Each regex is composed of various components that will be explained below.

### Anchors

To begin a regex you must use a "^" character. This lets the expression know that any string match will begin with the specific characters or range that follows the "^". To end a regex you must use a "$" character so the expression knows that the string to match must end with that specific character or range. In the case of the code below, everything inside the code must match.
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` This has a "^" right after the first slash and a "$" right before the end slash, so it is including everything.

### Quantifiers

Quantifiers are limiters for the string the regex will match. A minimum and a maximum are set so that it verfies a match to at least the minimum amount of characters and can stop when it reaches the maximum. A few examples of quantifiers are:
* which matches zero or more times
+ which matches one or more times
? which matches zero or one time
{} which contain information that either tell the expression to match a specific number of times {n}, at least a specific number of times {n,}, or within a specified range of times {n, x}

### OR Operator

The or operator is used to let the expression know that any of the characters within a group (surrounded by parentheses) can be matched, not necessarily all of them. For example if we wanted to find the match of (gym), then the text would have to have the letters g, y, and m. If we instead use (g|y|m) then any of the following would match: g; y; m; gy; ym; gm; gym; ymg; myg; etc...

### Character Classes

Character classes are shortened codes that represent a certain grouing of characters. 
. which matches any character except the newline character
\d which matches any numeral
\D which matches any non-digit character
\w which matches any capital or lowercase letter, numeral, and underscore
\s which matches a whitespace character (including tabs and line breaks)

### Flags

Flags are added at the end of a regex (after the final "/") to impose an additional function or to set a limit. The six flags can be used in any order and can be combined. They are as follows:
d which gives an index location for the piece of a string that matches
g which instructs to search all possible matches in the text
i which instructs to ignore case of letters
m which instructs that a new line will have a new match, not to treat it as just one
s which instructs that the "." should include the newline character (which as described above in character classes, it doesn't)
u which provides various Unicode-related features
y which sets the specific index of which to attempt to match


### Grouping and Capturing

Characters within parentheses are treated as different groups. In the matching an email code we have been using you can see that everything within the first set of parentheses are treated as one group that must exist before the "@", and that the next set of characters must be between the "@" and the ".", etc...
Capturing is a way to treat multiple characters as a single unit.

### Bracket Expressions

Bracket expressions are used to represent a range of characters. Inside the bracket you can have multiple chracters and the regex will look for a match to any of them. If you put a hyphen between any two letters or any two numbers the regex will include all letters or numbers in between as well. 
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
In the code above, the first character(s) can be any letter from a-z, any number from 0-9, an underscore, a backslash, a period, and/or a hyphen. The "+" lets the expression know that it can be more than one. After the "@" the next character(s) can contain any number (/d is the same as [0-9] - as we learned in the character classes section above), any letter a-z, and/or a period and/or a hyphen. Again the "+" lets the expression know it can be more than one. Then there will be a period, and following that will be any letter a-z and/or a period. The {2,6} is one of the quantifiers described above.

### Greedy and Lazy Match

In the quantifiers section above we saw how a curly brace quanitifer can set a range for the amount of times for an expression to match. By default the regex will try to match as many occurences of the pattern as possible, but adding a "?" after the quantifier will make it go from "greedy" to "lazy." In these cases the expression will instead match as few occurences as possible.

### Boundaries

The boundaries that we spoke about at the beginning `(the "^" and the "$")` let the regex know where to begin and end matching, but what if you want to use those as characters? To include these in the string you must use the escape syntax - which is preceeding the chracter with a backslash. In our example code for matching an email we can include the "$" character in our string by writing it this way:
`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` - notice in the first grouping of characters we have \$ included to allow that chracter to be included without ending the regex (making it a literal and not a special).

### Back-references

Back-references are stored matches of the running of the regex. These are used for manipulating the string.

### Look-ahead and Look-behind

Different conditions of look-ahead and look-behind will be used for different purposes. For example a positive look-ahead will return a match, but only if it is followed by a specific chracter or group of characters, whereas a negative look-ahead will return a match only if it is NOT followed by that specified character or group of characters.
Look-behinds work in much the same way as look-aheads, but instead of being concerned with the characters that follow the match, they are concerned with the characters the precede it. Positive for when the match must be preceded by that specific chracter or group of characters, and negative for when the match must not be preceded by that specific chracter or group of characters.

## Author

Jackson Impellizeri is a student at Columbia University learning to become a full-stack software engineer. He is eager to learn as much as he can and excel in a new field. To view his public repositories and projects please visit https://github.com/Jaxpi.
