# Evaluating an Email with Regex(Regular Expressions)

This tutorial will provide an in-depth exploration of regular expressions, often referred to as Regex. Our primary emphasis will be on using a regex pattern to validate input and verify whether a string conforms to the expected format of a valid email. Throughout the tutorial, we will use this email validation regex as a key example to illustrate the concepts and techniques discussed.

## Summary

Below is the single expression utilized to validate email inputs.
This tutorial will cover the fundamental components that constitute a regex, focusing on examples related to email regex patterns. The key elements of a regex include:

Anchors
Quantifiers
Grouping Constructs
Bracket Expressions
Character Classes
The OR Operator
Flags
and Character Escapes
In essence, regex serves as code segments acting as guardrails to ensure that user input aligns with the application's expectations, based on specific text pattern recognition defined within the regex. They can also be employed for text modification or manipulation purposes.

<br>

### ***REGEX EMAIL EXAMPLE***
```
 /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [About the Author](#about-the-author)

# Regex Components

<br>

## Anchors

**Anchors** are special characters that define the position of the regex. The are important if you have requirements on the placement of certain characters within a pattern. 
<br>
#### *Types of Anchors*
there are two main types of **Anchors**

**1. Start Anchor:** `^`

- This defines that the beginning of an input must match the start of the regex pattern. 

**2. End Anchor:** `$`

- This defines that the end of an input must match the end of the regex pattern. 

**Anchors** define the bounds in which the input should be compared to the regex. 
For example, the regex `^Bob$` would only allow the input of `Bob` and wouldn't allow the input of `Bobby` or `hi Bob` since neither pattern both starts and ends with `Bob`. Now, `^Bob` would allow `Bobby`, and `Bob$` would allow `hi Bob` to pass, but the other rex would not work for the alternate input. 

With respect to email validation, both the start and end **anchor** are necessary. As we know , the general email has a general text shape of `xxxxxxx@xxxx.xxx`. with the `@` and `.` characters having specific placement within that shape with the `@` symbol coming first, and the `.` last. Therefore, comparing the start and end of an email input is important. In our [regex email example](#regex-email-example) we can see our expression uses both the start `^([a-z0-9_\.-]+)` and end anchor `([a-z\.]{2,6})$` to limit the acceptable inputs by both the start and end.

<br>

## Quantifiers

**Quantifiers** are a number or numeric symbol used at the end of a character, [character class](#character-classes), or [bracket expression](#bracket-expressions) to define how many times that specified pattern should match. In the following examples we wil use `x` as a placeholder for a character .

- `x*` Equals the previous character or pattern 0 or more times. 
- `x+` Equals the previous character 1 or more times. 
- `x?` Equals the previous character 0 or 1 times.
- `x{n}` *note: `n` stands for number/integer in this example.* Equals the previous character exactly `n` times. 
- `x{n,m}` Equals the previous character between `n` and `m` times. 
*note: `m` must be greater than `n` and `n` must be an integer greater or equal to 0*

*note: adding a `?` to the end of any **qualifier** will make it non greedy and only return the first instance of an acceptance criteria.*



In our [regex email example](#regex-email-example) we can see our first grouping of character requirements `([a-z0-9_\.-]+)` has a `+` at the end which we know from our examples means that the input must match one or more instances of the specified requirements. we see the same **qualifier** at the end of the requirement set between the `@` and `.` `([\da-z\.-]+)`. Then, at the end of the regex `([a-z\.]{2,6})`, we see the `{2,6}` which we now know matches the set between 2 and 6 times based on this **qualifier**. 

<br>

## Grouping Constructs

**Grouping constructs** are are used to consolidate acceptable character criteria and organize or capture specific patterns. They are kept inside of parentheses `()`. 

In our [regex email example](#regex-email-example) we see `([a-z0-9_\.-]+)`,`([\da-z\.-]+)`, and `([a-z\.]{2,6})` which are all grouping constructs. We can infer the first group relates to the email name like `n00bsl43r`, the second to the email domain like `gmail` or `yahoo`, and the third to the top domain like `com`, or `net`. 

<br>

## Bracket Expressions

**Bracket Expressions** or *sub expressions* are represented by square brackets `[]` and specify a set of characters to match within an input. 

In our [regex email example](#regex-email-example) we can again see three examples `[a-z0-9_\.-]`, `[\da-z\.-]`, and `[a-z\.]` these are usually what our quantifiers are attached to if we have more than one character being evaluated for. 

<br>

## Character Classes

**Character classes** are shorthand expressions that are used to evaluate certain groupings of characters. Some common examples are: 
- `.`  The 'Charlie Day' AKA wild card allows any character
- `\s` For break or whitespace characters (space,tab,line breaks)
- `\d` Any number character (0-9)
- `\w` Any word associated characters(letters, numbers, and underscores)

*note: the capital letter version of these examples ` are the inverse.  So `\D` equals any non number character.*

In our [regex email example](#regex-email-example) we see that we have a `\d` which we know means any numeric character is being evaluated as acceptable in this expression. 

<br>

## The OR Operator

The **OR operator** depicted as `|` which is similar to the or operand in JavaScript `||` does exactly that. It lets you compare one pattern or another pattern to the input.

However we don't have any examples of this in our email example.

<br>

## Flags

**Flags** are like rule modifiers. the `i` **flag** makes the regex non case sensitive so both upper and lowercase can pass. the 'g' **flag** is called a 'global' **flag** and searches for all instances of the pattern instead of just the first matching input. 

there are no examples of **flags** in the email example. 

<br>

## Character Escapes

**Character escapes** are how you use certain characters that have been described by the regex code to mean something more than just the character as just the character that it is. For example, we know the `$` is an end anchor, so if we wanted to use `$` to check if an input contained a `$` we would have to *'escape'* it. We escape characters by adding a `\`. so to escape the `$` we would write `\$`. Now our regex will look for a literal `$` and not see it as an end anchor. 

In the regex email example provided, we utilize escaping backslashes followed by periods (\.) to specifically match periods instead of treating them as wildcard characters. This allows us to search for literal periods rather than their default wildcard representation.

### About the Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)

The author is weary and reluctant to write about themselves. Additionally, they have an aversion to writing and struggle with literacy, which has made the task of creating this tutorial quite challenging and less enjoyable. Please forgive any typos or grammatical errors that may be present.