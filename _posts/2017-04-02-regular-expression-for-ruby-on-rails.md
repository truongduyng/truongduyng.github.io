---
layout: post
title: Regular Expression in Ruby
tag: ruby
---

In this post, I intend to write down some basic Regex knowledge, especially for Ruby.

## Syntax

A regular expression literal is a pattern between slashes or between arbitrary delimiters followed by %r as follows:

```ruby
  /pattern/
  /pattern/im    # option can be specified
  %r!/usr/local! # general delimited regular expression
```

## Basic patterns

Except for control characters, (+ ? . * ^ $ ( ) [ ] { } \| \\ ), all characters match themselves. You can escape a control character by preceding it with a backslash.

Following table lists the regular expression syntax that is available in Ruby.

| Patterns | Description |
| -------- | ----------- |
| ^ | Matches beginning of line.
| $ | Matches end of line.
| . | Matches any single character except newline. Using m option to allow it to match newline as well.
| [...] | Matches any single character in brackets.
| [^...] | Matches any single character not in brackets
| re* | Matches 0 or more occurrences of preceding expression.
| re+ | Matches 1 or more occurrence of preceding expression.
| re? | Matches 0 or 1 occurrence of preceding expression.
| re{n}  | Matches exactly n number of occurrences of preceding expression.
| re{n,} | Matches n or more occurrences of preceding expression.
| re{n, m} | Matches at least n and at most m occurrences of preceding expression.
| a\|b | Matches either a or b.
| (re) | Groups regular expressions and remembers matched text.
| (?imx) | Temporarily toggles on i, m, or x options within a regular expression. If in parentheses, only that area is affected.
| (?-imx) | Temporarily toggles off i, m, or x options within a regular expression. If in parentheses, only that area is affected.
| (?: re) | Groups regular expressions without remembering matched text.
| (?imx: re) | Temporarily toggles on i, m, or x options within parentheses.
| (?-imx: re) | Temporarily toggles off i, m, or x options within parentheses.
| (?#...) | Comment.
| (?= re) | Specifies position using a pattern. Doesn't have a range.
| (?! re) | Specifies position using pattern negation. Doesn't have a range.
| (?> re) | Matches independent pattern without backtracking.
| \w | Matches word characters.
| \W | Matches nonword characters.
| \s | Matches whitespace. Equivalent to [\t\n\r\f].
| \S | Matches nonwhitespace.
| \d | Matches digits. Equivalent to [0-9].
| \D | Matches nondigits.
| \A | Matches beginning of string.
| \Z | Matches end of string. If a newline exists, it matches just before newline.
| \z | Matches end of string.
| \G | Matches point where last match finished.
| \b | Matches word boundaries when outside brackets. Matches backspace (0x08) when inside brackets.
| \B | Matches nonword boundaries.
| \n, \t, etc. | Matches newlines, carriage returns, tabs, etc.
| \1...\9 | Matches nth grouped subexpression.
| \10 | Matches nth grouped subexpression if it matched already. Otherwise refers to the octal representation of a character code.

## Examples

| Examples | Description |
| ------- | --- |
| /[Rr]uby/| Match "Ruby" or "ruby" |
| /rub[ye]/| Match "ruby" or "rube" |
| /[aeiou]/| Match any one lowercase vowel |
| /[0-9]/| Match any digit; same as /[0123456789]/ |
| /[a-z]/| Match any lowercase ASCII letter |
| /[A-Z]/| Match any uppercase ASCII letter |
| /[a-zA-Z0-9]/| Match any of the above |
| /[^aeiou]/ | Match anything other than a lowercase vowel |
| /[^0-9]/ | Match anything other than a digit |

## Searching and replace in ruby

```ruby
"0123-123-123 is a phone number.".gsub(/[\D]/, "") # 0123123123
line1 = "Cats are smarter than dogs"
line2 = "Dogs also like meat"
line1 =~ /Cats(.*)/ # true
line2 =~ /Cats(.*)/ #false
```
References: [https://www.tutorialspoint.com/ruby/ruby_regular_expressions.htm](https://www.tutorialspoint.com/ruby/ruby_regular_expressions.htm)
