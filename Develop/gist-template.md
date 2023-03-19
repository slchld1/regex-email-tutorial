# Regex tutorial 101

This is a Regex(Regular Expression) tutorial that will be guiding you on what they are, what the purpose of a regex are, and how to use them. A regular expression is a sequence of characters that defines a search pattern in text. Such as, finding a certain capital letter, or finding all text values that include the word "er". Regex is a great tool to pull information from a large amount of source.

## Summary

Now the question comes down to how we will be using regex in an actual problematic situation. In this tutorial we will be using the example of matching an Email using regex. The regex format for validating an email is the following givin code:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

At first glance, it does look like a bunch of special characters and numbers squished inside two slashes, but thats exactly what it is and we will break them down step-by-step.
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

To start a regex, the pattern must be wrapped around the slash characters `/`
This indicates the start of the pattern and the end of the pattern, whatever characters that are located inside the slash is the pattern that we are searching for.

### Anchors

The characters that start the following pattern and end the following pattern are considered anchors.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

In the example of the email format of the regex above we can identify that the symbols `^` and `$` are our anchors.

The `^` anchor indicates a string begins with the following. 

### Quantifiers

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
