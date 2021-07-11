# Markdown and LaTeX introduction
*[Ashkan Mirzaee](https://ashki23.github.io/index.html)*

[Markdown](https://daringfireball.net/projects/markdown/) is a
text-to-HTML conversion tool for web writers. Markdown allows you to
write using an easy-to-read, easy-to-write plain text format, then
convert it to structurally valid XHTML (or HTML). A Markdown document
could contain chunks of embedded graphics, source codes and LaTex
formula. [LaTeX](https://www.latex-project.org//) is a high-quality
typesetting system; it includes features designed for the production of
technical and scientific documentation. A basic knowledge about Markdown
and LaTeX could let to create HTML documents such as weblogs or reports
very easily. This tutorial provides a quick reference to use Markdown
and LaTeX.

-----

# Markdown

The following provides a quick reference to the most commonly used
Markdown syntax.

## Headers

<h3>

H3

</h3>

#### H4

##### H5

###### H6

``` markdown
# Markdown
The following provides a quick reference to the most commonly used Markdown syntax.

## Headers
### H3
#### H4
##### H5
###### H6
```

## Emphasis

*Italic* and **Bold**

``` markdown
*Italic* and **Bold**
```

~~Scratched Text~~

``` markdown
~~Scratched Text~~
```

superscript<sup>2</sup>

``` markdown
superscript^2^
```

Markdown doesn’t support underline, but we can use <u>HTML Text</u>
instead. Also, <b>we</b> can <i>render</i> almost any
<span style="color:red;">HTML</span> code that we   <kbd>like</kbd>  
such as superscript<sup>2</sup>.

``` html
Markdown doesn't support underline, but we can use <u>HTML Text</u> instead. Also, <b>we</b> can <i>render</i> almost any <span style="color:red;">HTML</span> code that we &nbsp; <kbd>like</kbd> &nbsp; such as superscript<sup>2</sup>.
```

For manual line or page breaks, we can use following HTML and CSS codes:

  - Line breaks:

<!-- end list -->

``` html
<br />
```

  - Print breaks:

<!-- end list -->

``` css
<p style="page-break-after:always;"></p>
```

## Lists

  - Item 1
  - Item 2
      - Item 2a
      - Item 2b
          - Item 2b-1
          - Item 2b-2

<!-- end list -->

``` markdown
- Item 1
- Item 2
    - Item 2a (2 tabs)
    - Item 2b
        - Item 2b-1 (4 tabs)
        - Item 2b-2
```

1.  Item 1
2.  Item 2
3.  Item 3
      - Item 3a
      - Item 3b

<!-- end list -->

``` markdown
1. Item 1
2. Item 2
3. Item 3
    - Item 3a
    - Item 3b
```

## Links

[Github](http://www.github.com/)

``` markdown
[Github](http://www.github.com/)
```

## Images

<p align="center">

![logo](https://www.raspberrypi.org/app/uploads/2018/03/RPi-Logo-Reg-SCREEN-199x250.png
"Raspberry pi")

</p>

``` markdown
<p align="center">
![logo](https://www.raspberrypi.org/app/uploads/2018/03/RPi-Logo-Reg-SCREEN-199x250.png "Raspberry pi")
</p>
```

Note that here we used an HTML code to align center the image. Also, we
can use HTML to add more styles, for example:

``` html
<p align="center">
<img src="https://www.raspberrypi.org/app/uploads/2018/03/RPi-Logo-Reg-SCREEN-199x250.png" alt="Raspberry pi" style="width:20%; border:0;">
</p>
```

## Quotes

> Imagination is more important than knowledge.
> 
> Albert Einstein

``` markdown
> Imagination is more important than knowledge.
>
> Albert Einstein
```

## Hlines

Use three dashes `---` to draw an horizontal line like:

-----

``` markdown
---
```

## Tables

<div style="margin-bottom: 1rem; overflow-x: auto;">

| 1st Header |   2nd Header   | 3rd Header |
| :--------- | :------------: | ---------: |
| col 1 is   |  left-aligned  |          1 |
| col 2 is   | center-aligned |          2 |
| col 3 is   | right-aligned  |          3 |

</div>

``` markdown
1st Header|2nd Header|3rd Header
---|:---:|---: 
col 1 is|left-aligned|1
col 2 is|center-aligned|2
col 3 is|right-aligned|3
```

Note that we can use HTML styles to hide tables’ overflow by putting
them in a division like:

``` html
<div "margin-bottom: 1rem; overflow-x: auto;">
...
</div>
```

Also, we can use `overflow-x: scroll` to always scroll or `overflow-x:
hidden` to hide them compeletely.

## Code blocks

In Markdown, we can simply add plain code blocks to display (not
evaluating) by inserting triple back quote i.e. ` ``` `. For example:

``` r
norm = function(x) {
  sqrt(x%*%x)
}
norm(1:4)
```

``` markdown
` ``r
norm <- function(x) {
  sqrt(x%*%x)
}
norm(1:4)
` ``
```

For inline plain codes use single back quote before and after the code,
for example we defined `this codes here` in this way.

## YAML header

At the top of a Markdown document, we can insert the following meta data
such that:

``` markdown
---
title: "Page Title"
subtitle: "Page sub-title"
author: "Author name"
description: "This is a test"
institute: "MU"
date: "20/02/2020"
abstract: "YAML"
keywords: 
  - key1
  - key2
tags:
  - tag1
  - tag2
---
```

## Mathematical formula

We can use LaTeX to write mathematical equations in Markdown. To write
inline LaTeX formula use a single `$` before and after the equation and
use a double `$` to display equations.

-----

# LaTeX

A basic LaTeX knowledge let us to write mathematical equations in
Markdown. You can find a quick reference to the most commonly used LaTeX
syntax for Markdown in
[here](https://ashki23.github.io/markdown-latex.html#latex) and a more
extensive reference at [LaTeX
Wikibooks](https://en.wikibooks.org/wiki/LaTeX/Mathematics).

---

Copyright 2018-2021, [Ashkan Mirzaee](https://ashki23.github.io/index.html) | Content is available under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) | Sourcecode licensed under [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html)
