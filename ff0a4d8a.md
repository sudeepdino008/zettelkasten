---
date: 2020-11-13T13:53
---

# Regex
#### resource
[regexr](https://regexr.com/)

## Character classes

## Anchors 
```
^ - match at beginning of input text
$ - match at end of input text
\b - match at word boundary
\B - don't match at word boundary

```

## escape characters

### control escape characters
```
in the form \cZ
Where it can range from \cA to \cZ
\cI is tab
```

## Groups and back references
reference: [Capture Group Numbering & Naming: The Gory Details](https://www.rexegg.com/regex-capture.html)

```
capturing group
(ABC)

named capturing group
(?<name>ABC)
referencing a named capturing group
\k<name>

non capturing group (doesn't create a capture group)
(?:ABC)


numeric reference
\1

```

## lookaround

The extra patterns (`ABC`) are not matched
```
positive lookahead
(?=ABC)

1pt 2px 3em 4px

to match '3', you can do \d(?=em)


negative lookahead
(?!ABC)

to match everything apart from em numerals - \d(?!em)

positive lookbehind
(?<=ABC)

to match those 'em' which follow a number
(?<=\d)em

negative lookbehind
(?<!ABC)
```

## Quantifiers

```
plus +
star *
quantifier {1,3}
optional ?

lazy ?
makes preceding quantifier lazy, causing it to match as few characters as possible. By default, they are greedy, and will match as many characters as possible

alternation |

example: 
b123b
bee3oob
bllpppb

match "pure" boundaries of b i.e. b123b and bllpppb

\bb([0-9]+|[A-Za-z]+)b\b

```


## Regex substitutions
Most common way is to use capture (named/unnamed) groups  

```
substitute the substring matched by group number - $number
substitute the substring matched by named group - ${name}

```
