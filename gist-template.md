# Regex Tutorial

Regex, or regular expressions, are patterns used to search and return matches from with a given string. Regex are used throughout programming including JavaScript code. Regex can be constructed in one of two ways in JavaScript, by use of regular expression literal or calling the constructor function RegExp. While regex come in many different "flavors" between programming languages, they can always be used to save both time and effort.

## Summary

The regex which I will explain is the pattern used to match an email address, /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/. I will attempt to break down each component of the regex to better understand how exactly the pattern is able to return an email address. Also, I will look at commonly used regex components which are not included in the email address search pattern, but which will still increase understanding of how regex can be used.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)

## Regex Components

### Anchors

Anchors do not match any character, they instead match the position before and after the characters and in doing so "anchor" the match at a given position. The caret anchor, ^, matches the beginning of the string, the position before the first character that is. Whereas the dollar sign, $, matches the point after the last character in a string. Together the two represent the start and end of the string and act as its' anchors. The email address pattern features the caret anchoring the beginning of the pattern and the dollar sign anchoring the end.

### Quantifiers

A metacharacter which modifies the previous character in the regex which determines how many of those characters you want to match in a row. Frequently used quantifiers are the exact count {n}, the range {n,m}, the question mark which means zero or one and is equal to {0,1}, the asterisk which means zero or more and is the same as {0,}, and the plus sign which means one or more. The email pattern makes use of both the plus sign quantifier and the range quantifier. Both plus signs are included to match any number of characters that may be present in the username and the domain name. The range {2,6} being used to match .com, .org, or .info. Any of which may be present at the end of the domain name.

### OR Operator

The logical OR is represented by |. The operator will search for matches to the characters or expressions on either the left or the right of the OR operator. If one was to search, p|P, it would yield any use of either the upper or lower case of the letter p. The OR operator is not used in the email address pattern, but is still both commonly used and useful.

### Character Classes

By use of an opening and closing square bracket, [...], we can tell the regex engine to match specific characters amongst many. For the email address pattern, character classes are used on three different occasions. In the first character class, we will match any lower class letter from a-z, any digit 0-9, underscore, a period denoted by \., and the slash. In the second character class \d matches any digit, any lower case latter from a-z, a period, and a slash. In the final character class the pattern will match any lower cass letter from a-z and a period.

### Flags

Flags can be thought of as parameters for a regex search engine which will modify its behavior. In JavaScript there are a total of six different flags eahc being denoted by the use of a single lowercase letter. For a regex created literally, the flag would come after the second slash /regex/flag. One such example is the ignore casing flag, i, which makes the regex search case insensitive. Another, the global, g, makes the regex search for all occurences. No flags however are used in the email search pattern.

### Grouping and Capturing

The act of enclosing a pattern within a set of parentheses (...) is referred to as a capturing group. Within the email search pattern, three capturing groups are used. The first set of parentheses contains the username, the second the domain name, and the third contains the top-level domain.

### Greedy and Lazy Match

Greedy and lazy matches refer to the sometimes unexpected way in which quantifiers can work. The combination of the dot, which denotes any character except line breaks, with the plus sign, +, which denotes one or more, will return every character in a string until a line break. The regex engine looks for a match at every position in the string, so if the search `.+` were tried, once the first backtick were found the engine would begin looking for a match for the rest of the pattern with .+ being next. The .+ would return every position in the string then until it ended, the engine would then have to backtrack when it came to the next part of the pattern, the second backtick. Lazy matches on the other hand combine a quantifier with the question mark,?, which is itself a quantifier. When +? is used in combination, the engine will increase the number of repetitions only if the rest of the pattern can't match a particular position.

### Boundaries

Acting like an anchor, the word boundary, \b, is generally used to search for whole words, though it can also be used with digits. The regex \bHello\b would return Hello from the string "Hello World!", however if the regex \bHell\b were to be used the search would yield nothing. Within the email pattern, boundaries are not used by the pattern.

## Author

My name is John Armstrong but everyone calls me Jack. Regular expressions are still new to me, but I hope to get better acquainted with them as I continue coding.
GitHub Profile: https://github.com/jackarms
