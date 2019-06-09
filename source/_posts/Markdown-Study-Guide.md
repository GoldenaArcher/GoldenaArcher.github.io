---
title: Markdown Study Guide
date: 2019-06-07 01:10:01
categories: [GitHub/Markdown]
tags: [Markdown, GitHub]
---
<img src="https://i.loli.net/2019/06/09/5cfcb6625228618408.png" width=400>

Since markdown was introduced by one of my instructors, I have been using markdown for quite a while, and also used it for taking class notes as well. However, I have not yet fully discovered the potential of markdown, until recently I read that css and html languages can also be used directly in markdown. 

<!-- more -->

Here is the sample code that I read:

<p style="text-align:center;color:#1e819e;font-size:1.3em;font-weight:bold;">
Change the size, color and align of font
</p>
And this is the result that I saw:

<img src="https://i.loli.net/2019/06/09/5cfcb66336c4495588.png" width="400">

This blew my mind, and I decided to spend more time on studying markdown. Later, the idea of learning and being more organized turned to be the motivation for the post.

***

# Basic Syntax

## Basic Text Formatting

### Italic

`<i>`

```markdown
*italic* or _italic_
```
Output:

*italic* or _italic_

***

### bold

`<b>`

```markdown
**bold** or __bold__
```
Output:

**bold** or __bold__

***

### Italic and Bold

`<b>` and `<i>` of course

```markdown
___italic and bold___ or ***italic and bold***
```
Output:

___italic and bold___ or ***italic and bold***

***

### Strikethrough

`<del>`


```markdown
~~strikethrough~~
```
Output:

~~strikethrough~~

***

### Carriage Return

`<br>` for line break, and `<p>` for paragraph.

```markdown
A carriage return
makes a line break.

Two carriage returns make a new paragraph.
```
A carriage return
makes a line break.

Two carriage returns make a new paragraph.

***

### Other Basic Syntax

#### Strong

`<Strong>` - this is <strong>important</strong>

***

#### Emphasis

`<em>` - this is <em>emphasized</em>

***

#### Mark

`<mark>` - this is <mark>marked</mark>

***

#### Small

`<small>` - this is <small>small</small>

***

#### inserted

`<ins>` - this is <ins>inserted</ins>

***

#### Subscript

`<sub>` - this is <sub>subscript</sub>

***

#### Superscript

`<sup>` - this is <sup>superscript</sup>

***

### Horizontal Rules

Which is the divider used between sections, consists of three or more *'s or -'s on a single line.

```
---
***
--------------------
******************
```

---

### Backslash Escapes

Used for special characters so that they can be displayed normally.

Markdown provides backslashes for the following characters:

>```
>\   backslash
>`   backtick
>*   asterisk
>_   underscore
>{}  curly braces
>[]  square brackets
>()  parentheses
>#   hash mark
>+   plus sign
>-   minus sign (hyphen)
>.   dot
>!   exclamation mark
>```

```
\. \* \\
```

Output:

\. \* \\ 

## Headers

### Setex

Used for `<h1>` and `<h2>` tags.

“Underlined” using **equal signs (=)** as `<h1>` and **dashes (-)** as `<h2>` in any number

```markdown
This is an H1
==============
This is an H2
--------------
```

Output:

<img src="https://i.loli.net/2019/06/09/5cfcb662cfb9094585.png" width="400">

***

### Atax

HTML tags are `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, and `<h6>`, use 1-6 hash character to correspond desired `<h1>` - `<h6>`

```html
# This is an H1
## This is an H2
### This is an H3
#### This is an H4
##### This is an H5
###### This is an H6
```

Output:

<img src="https://i.loli.net/2019/06/09/5cfcb662dd70842980.png" width="200" align="middle">

***

## Links

`<a>`

Most links will be automatically turned into links, to be more explicit, use `<>` surround the link.

```markdown
<https://www.amazon.com/>
<some@example.com>
```

Output:

<https://www.amazon.com/>

<some@example.com>

***

### Inline

The format for inline like is: `[text](https://abc.com "Title")`, if `Title` is neglected, then there is no `Title` attributes for the link, which means when mouse is hovered over the text, there will be no title displayed for the link. 

```markdown
[Google](https://www.google.com/ "Google")
[Google](https://www.google.com/)
```

Output:

[Google](https://www.google.com/ "Google") and [Google](https://www.google.com/)

***

Also, when referring to a local resource on the same server, relative path can be used.

```markdown
[Hello World](/2019/06/05/hello-world/)
```

Output:

[Hello World](/2019/06/05/hello-world/)

Also, the markdown images on the top of the page is inserted by using relative path.

***

### Reference

The format for reference is: `[text]: URL "title"` for defining source, and use `[text][reference]`to link text and reference. This is useful when links are used for multiple times in some content.

```markdown
[1]: https://en.wikipedia.org/wiki/Main_Page "wikipedia main page"
[wikipedia main page]: https://en.wikipedia.org/wiki/Main_Page "wikipedia main page"
This is [wikipedia main page][1].
This is [wikipedia mainpage][] as well.
```

Output:

[1]: https://en.wikipedia.org/wiki/Main_Page "wikipedia main page"
[wikipedia main page]: https://en.wikipedia.org/wiki/Main_Page "wikipedia main page"
This is [wikipedia main page][1].<br/>
This is [wikipedia main page][] as well.

***

### Anchor Reference

Similar to reference, but anchor reference is used to link in-text anchor point. I have read in some [stackoverrflow comments](<https://stackoverflow.com/questions/6695439/how-to-link-to-a-named-anchor-in-multimarkdown/6706594>) which stated that header will generate anchor point by default. I tried on this post, nothing really worked, but perhaps works in other place.

Basically, anchor reference used html `<a>` tag to create an anchor point which is accessible as long as the linkage is in the same page.

```
set an anchor link
<a name="anchor">anchor</a>
...as long as they are in the same page...
[text](#anchor)

TO CREATE AN ANCHOR IN HEADING
[create an anchor](#anchors-in-this-page)
```

***

## Images

Similar to links, just have `!` in front of link.

### Inline

`<img src="">`

Syntax: `![images](https://link.com "alt")`

```
![flower](https://i.loli.net/2019/06/09/5cfcb663304de29730.jpg "flower")
```

Output:

![flower](https://i.loli.net/2019/06/09/5cfcb663304de29730.jpg)

### Reference

```
![flower][flower]
[flower]:https://i.loli.net/2019/06/09/5cfcb663304de29730.jpg "flower"
```

Output:

![flower][flower]

[flower]:https://i.loli.net/2019/06/09/5cfcb663304de29730.jpg "flower"

---

### Attached Link

I'm not planning to attach images here, so, just add context here as a reference.

`[[img src=attached-image.jpg alt=image]]`

# List

## Unordered List

use *, -, + to create an unordered list, `<ul>`

```
- unordered list 1
	- nested unordered list 1.1
+ unordered list 2
* unordered list 3
```

Output:

- unordered list 1
  - nested unordered list 1.1
    - nested unordered list 1.1.1
      - etc

- unordered list 2

- unordered list 3

***

## Ordered List

Similar to unordered list, but use 1 instead. 

I feel like in this case, perhaps using html is a clearer way of creating an ordered list.

```
1. point A
	1. point A.a
	2. point A.b
2. point B
```

1. point A
   1.  point A.a
   2.  point A.b
2. point B

It is possible to trigger an ordered list by accident:

```
1986. What a great season.
```

Output:

1986. What a great season.

In this case, a __backslash_escape(\\)__ can be used to resolve the issue:

```
1986\. What a great season.
```

Output:

1986\. What a great season.

***

## Definition List

Seemed not supported by GitHub page... But seemed fun to play around, so I decided to add the item here.

This is the markdown syntax:

```
First Term
: This is the definition of the first term.

Second Term
: This is one definition of the second term.
: This is another definition of the second term.
```

This is the corresponding html syntax:

```
<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>
```

Output from html syntax:


<dl>
  <dt>First Term</dt>
  <dd>This is the definition of the first term.</dd>
  <dt>Second Term</dt>
  <dd>This is one definition of the second term. </dd>
  <dd>This is another definition of the second term.</dd>
</dl>
***

## Check List

Looks  like to-do list.

```
- [ ] not checked
- [ ] not checked
- [x] checked
```

Output:

- [ ] not checked
- [ ] not checked
- [x] checked

---

# Indent

## Blockquote

Just put __>__ in front of the paragraph or text.

```
A list item with block quote
> Blockquote
> with indentation
```

Output:

A list item with block quote
> Blockquote
> with indentation

Can also only put in front of the paragraph.

```
A list item with block quote
> Blockquote
with indentation
```

Output:

A list item with block quote
> Blockquote
> with indentation

## Nested Blockquote

Like reference of reference.

```
 > A blockquote
 >> Nested blockquote
 >>> Another nested blockquote
```

 > A blockquote
 > > Nested blockquote
 > >
 > > > Another nested blockquote

## Code Block

For some reason, it does not work same when I read in other place:

> To put a code block within a list item, the code block needs to be indented twice — **8 spaces** or **two tabs**

It only works in this particular format:

```
* List 1

      printf()
```

Outcome:

* List 1

      printf()

Perhaps just easier to use code blocks directly.

---

# Code Blocks

`<pre>` in html. 

I found in different places they said that 

> Indent every line of the block by at least **4 spaces** or **1 tab**.

But this part is true:

> Within a code block, **ampersands (&)** and angle **brackets (< and >)** are automatically converted into HTML entities.

```html
<div class="footer" style="text-align: center">
    &copy; 2004 Foo Corporation
</div>
```

Outcome:

<div class="footer" style="text-align: center">
    &copy; 2004 Foo Corporation
</div>

## Fenced Code Blocks

`<code>`

I found this works way better than indentation directly.

`~`and <code>`</code> works the same way.

```
This is a normal paragraph:
\`\`\`
    This is a code block.
\`\`\`
```

Outcome:

This is a normal paragraph:

```
This is a code block.
```

---

### Syntax Highlighting

This is the way I like to do it, adding the language after \`\`\`.

```
\`\`\`Java
System.out.println("hello world");
\`\`\`
```

Outcome:

```java
System.out.println("hello world");
```

---

## Inline Code

Just use \` between inline code

```
Use `System.out.println();` to print in Java
```

Outcome:

Use `System.out.println();` to print in Java

---

# Tables

`<table>`

Column separator is __pipe (|)__; the header is separated by **dashes(-)**; the **colon(:)** is used for alignment.

```
name | id | score 
- | - | -
A | 1 | A
B | 2 | A+
```

Outcome:

| name | id   | score |
| ---- | ---- | ----- |
| A    | 1    | A     |
| B    | 2    | A+    |

---

Whether outer pipe exists or not, there is no effect:

```
| name | id | score |
| - | - | - |
| A | 1 | A |
| B | 2 | A+ |
```

Outcome:

| name | id   | score |
| ---- | ---- | ----- |
| A    | 1    | A     |
| B    | 2    | A+    |

---

Also, this example shows how to align the table:

```
name | id | score 
:--- | :---: | ---:
A | 1 | A
B | 2 | A+
```

Outcome:

| name |  id  | score |
| :--- | :--: | ----: |
| A    |  1   |     A |
| B    |  2   |    A+ |

---

# Not GitHub-flavored Functions

I found these not working on the git page, but might be worth it to dig deeper.

## Footnotes

```
Markdown[^1]

```

---

## TOC

`[toc]`

---

## Flowchart

Have not yet studied.

---

## Video and Audio Insertion

---

## LateX

---

