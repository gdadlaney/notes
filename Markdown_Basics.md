# Markdown Basics
- To add a new line, type `\` or type 2 spaces before the newline

*italics* or _underscores_\
**bold** or __underscores__  
~~scratch~~\
`Ctrl+k, then v` to view markdown in VSC

## 3 ways to draw Horizontal Lines
---
***
___

## Lists
1. Item1
    1. Item1.1
2) Item2
    * Some other item

    Indented para

## 3 ways for unordered list
+ one
- two
* three


# Biggest
###### Smallest


> These are blockquotes.

> 2nd blockquote.

> Block quotes support line breaks.
> 
> This is like a code block, but for normal text.

> Overkill - Nesting in block quotes
> 1. req.params
> 2. req.query
> > hi
---


# Note: Order of symbols (lists and headers)
1. lists and block qoutes have the same top priority
> 1. > * Hello
2. Next comes headers
## 1) Doesn't work
1) > 2. > * ## Works

# Note: Indentation
1. Indentation in lists
    - Works well
- The other way around
    1) This works too
## Indentation immediately after headers
    1) Disaster, lists don't work
    - `code snippets` are not highlighted
## Don't indent immediately after headers
1) Lists work
- `code snippets` work
    - Nesting inside lists works

# Links
1. [I'm an inline-style link](www.google.com "optional title")
2. [using numbers for reference-style link definitions][1]  
    * [mozilla again][1]
3. \<a href> can be used too
> Note: for 2., there needs to be an empty line above the link definition

[1]: www.mozilla.org

# Links enable Jumps
1. ### Jump to [Biggest](#Biggest)
2. ### Jump to [Smallest](#Smallest)
3. ### Jump to [a Heading](#tith)
### <span id="tith"></span>This is the Heading

# Comments
Multiline look like this: 
\<!---
Comments
--->  
- Single line comments are not defined.
- Note the triple hypen.

> Note: Tabs and newlines work as they are in code sections, but not for usual text.  
> Solution 1: Enclose it in pre tags. \
> Solution 2: For newlines, use a \ or double space before the newline.

