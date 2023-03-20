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

The `^` anchor indicates a string beginning with the following. 
In an email expression, we can identify that `([a-z0-9_\.-]+)` is shown followed by the `^` anchor. 

This is indicating that the input value must start with any characters `a-z` and can follow with any numbers `0-9`.

Now onto the ending anchor `$` the expression is `.([a-z.]{2,6})$`
We know that all emails end with a .com or .org, etc. therefore, we know this expression is verifying that exact string. 
The `a-z` indicating any characters between a-z and {2,6} is a quantifier indicating that the length of the character is between 2 to 6 characters.

### Quantifiers

As mentioned in the above topic, quantifiers set the limits of the string that matches your regex. It typically includes the minimum and the maximum number of characters in the expression.

Quantifiers could be defined in many different patterns such as,
- `*`
- `+`
- `?`
- `{}`
We will only be covering the `{}` curly brackets in this tutorial.
Curly brackets provide multiple ways to set its limits.
`{ n }` - if declared with one number it matches the exact number of times,
`{ n , }` - if declared with a comma, it matches at least the number of times,

`{ a, b}` - if declared with two numbers `a` will indicate the minimum and `b` will indicate the maximum.

The `{2,6}` in the email expression `.([a-z.]{2,6})$` is within a parentheses which is defining that it is only affecting what is within the parentheses. Therefore, whatever that came after the `.` is affected by the minimum and maximum requirement length of characters.

### OR Operator

An OR operator is an indicator that splits characters which allows that the character could match one or the other. 
For example,
`a|b|c`  
in this expression, the matching character could be a, b, or c. Unfortunately, our email format expression does not contain an OR operators, but keep in mind that this operator is a great example to limit our matches to a much detailed amount, such as changing our expression to match only `.com` or `.org`. 

### Character Classes

Character Classes define set of characters that fulfil a match. This is very similar to bracket expressions, but you can consider them as sort of a shortcut. Some common character classes are 
- `.` - Matches any characters except the new line characters `\n`
- `\d` - Matches any Arabic numeral digits(equivalent to the bracket expression)
- `\w` - Matches any Alphanumerical characters from basic Latin alphabets including underscore `_`. The bracket expression is `[A-Za-z0-9_]`
- `\s` - Matches any single white space characters, including tab spaces and line breaks.

One neat fact about character classes are that once they are written in a capitalized letter such as `\D` or `\W` it inverses the matches, which means the match will be looking for the opposite factor.

### Flags

Flags are optional components placed after a regex expression to further strict a search. Our email expression does not use a flag but here are some common examples of a flag,
- `g` - A global search that tests against all possible matches in the string.
- `i` - A case-insensitive search which ignores case-sensitivity while it tests for a match.
- `m` - A multi-line search where the input string is treated as multi-lines.

These flags would be more commonly used in a document or a string containing a large pool of information, rather than an email.

### Grouping and Capturing

Grouping and Capturing allows us to focus on specific portions of the expressions. In the email expression below, we ues parentheses to do our grouping. 

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

We can observe that `([a-z0-9_\.-]+)`, `([\da-z\.-]+)`, `([a-z\.]{2,6})` are all in different groupings.
This lets us simplify the expression into just 3 separate part of an expression.

### Bracket Expressions

Brackets represent range. Whatever is declared inside a bracket `[]` describes the range of characters or numbers we want to match.
`[a-z0-9_\.-]` given this example, the range of characters inside the bracket are `a-z`, `0-9`, `_\.-`.

When broken down, the characters we are matching is `a-z`, any numbers between `0-9` and any special characters from `_\.-`. These numbers and characters and special characters could be in any order desired.

### Greedy and Lazy Match

Greedy Match is referring to matching in the longest group as possible, and a Lazy Match is referring to matching in the smallest group as possible. 
These matches are used with quantifiers, and the biggest difference between these to matches would be that a Greedy Match will continue searching for a match until condition is not satisfied, and a Lazy Match will stop the search once condition is satisfied.

A Greedy Match often use single quantifiers such as, `*`, `+`, `?`, `{n}`, `{n,}`, `{n,n}`.
A Lazy Match is often followed up with a `?` in its quantifiers such as `*?`, `+?`, `??`, `{n}?`, `{n,}?`, `{n,n}?`.

### Boundaries

Boundaries is an advance regex category where the meta-character `\b` acts as an anchor just as a `^` or `$`
The meta-character `\b` simply indicates and allows a search for a whole word. For example,

`\bEmail\b` will indicate a whole word search for `Email`.

### Back-references

Back-reference match is matching the same text previously matched by a capturing group. 
By adding a `\1` at the end of the expression captures one group, and whatever is placed within the expression previously, will be repeated for a search.

For example, 

`([a-c])x\1x\1`

will capture `axaxa` or `bxbxb` or `cxcxc`.

### Look-ahead and Look-behind

Look-ahead method is defined in positive and a negative method. A positive look-ahead defines a pattern that is followed by something else and a negative look-ahead defines a pattern that is not followed by something.

Look-behind method is also defined in a positive and a negative method. Look-behind method works backwards to the look-away method, so simply a positive look-behind method defines a pattern that is behind something else and negative look-behind defines a pattern that is not behind something else.

## Author

Name: Minjae Cho

GitHub: <a href=https://github.com/slchld1 target=_blank>https://github.com/slchld1</a>
