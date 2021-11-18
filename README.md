# Regex Tutorial

This document is to explain how the regex works. blabla.....

## Summary

In this toturial, I am going to explain how the regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` work. blablabla...

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
1. what does the component do? 
The characters ^ and $ are both considered to be anchors.

The ^ anchor signifies a string that begins with the characters that follow it. This could be in one of two formats:

An exact string match, such as ^The, where the strings "The" or "The person" match, but "the" and "the person" do not. This is because a regex is case-sensitive.

A range of possible matches, displayed using bracket expressions. We'll discuss this in the next section.

The $ anchor signifies a string that ends with the characters that precede it. Just as with the ^ character, it can be preceded by an exact string or a range of possible matches.

2. In your example, how does the anchor work?
In regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, it defines the string to be start with `([a-z0-9_\.-]+)` and end with `([a-z\.]{2,6})`. We will talk about what the start and ending pattern means in the later section.

### Quantifiers
1. What does the component do

Quantifiers set the limits of the string that your regex matches (or an individual section of the string). They frequently include the minimum and maximum number of characters that your regex is looking for.

Quantifiers are inherently greedy, meaning they match as many occurrences of particular patterns as possible. They include the following:

*—Matches the pattern zero or more times

+—Matches the pattern one or more times

?—Matches the pattern zero or one time

{}—Curly brackets can provide three different ways to set limits for a match:

{ n }—Matches the pattern exactly n number of times

{ n, }—Matches the pattern at least n number of times

{ n, x }—Matches the pattern from a minimum of n number of times to a maximum of x number of times

Each of these quantifiers can be made lazy by adding the ? symbol after it, meaning it will match as few occurrences as possible.
3. How it work in your example
In my example, {2,6} is the quantifier. It means the string's ending pattern should be a character of a-z or dot with length of 2-6 characters.
For example ab => will work
abc => work, 
abc. => work,
aabbcc => work, 
aabbccd => not work(>6 characters)

### Grouping Constructs
what is component do?
The primary way you group a section of a regex is by using parentheses (()). Each section within parentheses is known as a subexpression.

how it work in your regex?
In regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, there are three grouping constructs. `([a-z0-9_\.-]+)`, `([\da-z\.-]+)` and `([a-z\.]{2,6})`
It means we need to translate the regex pattern within the group. In this case, it divde the regex into three components, for exmaple, the first one `([a-z0-9_\.-]+)`, it means any number of characters that is a-z, 0-9 plus special characters . - _ 

### Bracket Expressions
1. what is the component
Anything inside a set of square brackets ([]) represents a range of characters that we want to match. These patterns are known as bracket expressions, but they are also known as a positive character group, because they outline the characters we want to include. We can write these expressions to include all of the characters we want to match. For example, [abc] will look for a string that includes a or b or c, regardless of the length of the string. So all of the following examples would match: "aaa", "bin" "court", "abracadabra", and "bca".

You'll more commonly see a hyphen (-) used between alphanumeric characters (letters and numbers only) to represent a range of those possible characters. This means that [a-c] and [abc] will look for the exact same thing.

2. how it works in your regex
In `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, we have three bracket expression. For example, `[a-z0-9_\.-]`, it means character should match the pattern that is a-z, 0-9 plus special characters . - _ 
### Character Classes
What is the component
A character class in a regex defines a set of characters, any one of which can occur in an input string to fulfill a match. We've actually already discussed some character classes. The bracket expressions outlined previously, including positive and negative character groups, are considered character classes.

Here are some of the other common character classes:

.—Matches any character except the newline character (\n)

\d—Matches any Arabic numeral digit. This class is equivalent to the bracket expression [0-9].

\w—Matches any alphanumeric character from the basic Latin alphabet, including the underscore (_). This class is equivalent to the bracket expression [A-Za-z0-9_].

\s—Matches a single whitespace character, including tabs and line breaks

Each of the last three character classes can be changed to perform an inverse match by capitalizing the letter character. For example, \D matches a non-digit character.

How it works in your regex
In the exmaple `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, `\d` is the character classes. It means the character should be 0-9
### The OR Operator
What is the component
Using the OR operator (|), the expression [abc] could be written as (a|b|c). 

How it works in your example 
In my example,  `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, there is no OR characters.
### Flags
We started this tutorial by explaining that as a literal, a regex must be wrapped in slash characters. The one exception to this rule is with the component known as flags. Flags are placed at the end of a regex, after the second slash, and they define additional functionality or limits for the regex. There are six optional flags that can be used, either separately or together and in any order, but these are the three you're most likely to encounter:

g—Global search: the regex should be tested against all possible matches in a string.

i—Case-insensitive search: case should be ignored while attempting a match in a string

m—Multi-line search: a multi-line input string should be treated as multiple lines
In my example,  `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, there is no flags.

### Character Escapes
The backslash (\) in a regex escapes a character that otherwise would be interpreted literally. For example, the open curly brace ({) is used to begin a quantifier, but adding a backslash before the open curly brace (\{) means that the regex should look for the open curly brace character instead of beginning to define a quantifier. This is common when looking for strings with special characters that are the same as a particular component of a regex.

It's important to note that all special characters, including the backslash (\), lose their special significance inside bracket expressions.
In my example,  `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, `\.` is the character escapes. The reason it should be used is that we want to clarify it is a dot rather than a matching character.
## Author
A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
