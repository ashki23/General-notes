
# R Markdown and LaTeX
*[Ashkan Mirzaee](https://ashki23.github.io/index.html) - December 2018*

[Markdown](https://daringfireball.net/projects/markdown/) is a text-to-HTML conversion tool for web writers. Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML). A Markdown document could contain chunks of embedded graphics, source codes and LaTex formula. [LaTeX](https://www.latex-project.org//) is a high-quality typesetting system; it includes features designed for the production of technical and scientific documentation. A basic knowledge about Markdown and LaTeX could help you to create HTML documents such as weblogs or reports easily. This tutorial provides a quick reference to use Markdown and LaTeX.

---

# Markdown
The following provides a quick reference to the most commonly used Markdown syntax.

## Headers
<h3>H3</h3>
#### H4
##### H5
###### H6

```markdown
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

```markdown
*Italic* and **Bold**
```

~~Scratched Text~~

```markdown
~~Scratched Text~~
```

superscript^2^

```markdown
superscript^2^
```

Markdown doesn't support underline, but we can use <u>HTML Text</u> instead. Also, <b>we</b> can <i>render</i> almost any <span style="color:red;">HTML</span> code that we &nbsp; <kbd>like</kbd>  &nbsp; such as superscript<sup>2</sup>.

```html
Markdown doesn't support underline, but we can use <u>HTML Text</u> instead. Also, <b>we</b> can <i>render</i> almost any <span style="color:red;">HTML</span> code that we &nbsp; <kbd>like</kbd> &nbsp; such as superscript<sup>2</sup>.
```

For manual line or page breaks, we can use following HTML and CSS codes:

- Line breaks:

```html
<br />
```

- Print breaks:

```css
<p style="page-break-after:always;"></p>
```

## Lists
- Item 1
- Item 2
    - Item 2a
    - Item 2b
        - Item 2b-1
        - Item 2b-2

```markdown
- Item 1
- Item 2
    - Item 2a (2 tabs)
    - Item 2b
        - Item 2b-1 (4 tabs)
        - Item 2b-2
```

1. Item 1
2. Item 2
3. Item 3
    - Item 3a
    - Item 3b

```markdown
1. Item 1
2. Item 2
3. Item 3
    - Item 3a
    - Item 3b
```

## Links
[Github](http://www.github.com/)

```markdown
[Github](http://www.github.com/)
```

## Images
<p align="center">
![logo](https://www.raspberrypi.org/app/uploads/2018/03/RPi-Logo-Reg-SCREEN-199x250.png "Raspberry pi")
</p>

```markdown
<p align="center">
![logo](https://www.raspberrypi.org/app/uploads/2018/03/RPi-Logo-Reg-SCREEN-199x250.png "Raspberry pi")
</p>
```

Also, we can use HTML to add more styles. For example:

```html
<img src="https://www.raspberrypi.org/app/uploads/2018/03/RPi-Logo-Reg-SCREEN-199x250.png" alt="Raspberry pi" style="width:20%; border:0;">
```

## Quotes
> Imagination is more important than knowledge.
>
> Albert Einstein

```markdown
> Imagination is more important than knowledge.
>
> Albert Einstein
```

## Hlines
Use three dashes `---` to draw an horizontal line like:

---

```markdown
---
```

## Tables
1st Header|2nd Header|3rd Header
:---|:---:|---: 
col 1 is|left-aligned|1
col 2 is|center-aligned|2
col 3 is|right-aligned|3

```markdown
1st Header|2nd Header|3rd Header
---|:---:|---: 
col 1 is|left-aligned|1
col 2 is|center-aligned|2
col 3 is|right-aligned|3
```

## Code blocks
In Markdown, we can simply add plain code blocks to display (not evaluating) by inserting triple back quote i.e. ` ``` `. For example:

```r
norm = function(x) {
  sqrt(x%*%x)
}
norm(1:4)
```

```markdown
` ``r
norm <- function(x) {
  sqrt(x%*%x)
}
norm(1:4)
` ``
```

For inline plain codes use single back quote before and after the code, for example we defined `this codes here` in this way.

## YAML header
At the top of a Markdown document, we can insert the following meta data such that:

```markdown
---
title: "Page Title"
subtitle: "Page sub-title"
author: "Ashkan Mirzaee"
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
We can use LaTeX to write mathematical equations in Markdown. To write inline LaTeX formula use a sigle `$` before and after the equation and use a double `$` to display equations. 

# LaTeX
A basic knowledge about LaTeX could let us to write mathematical equations in Markdown. You can find quick references to the most commonly used LaTeX syntax Markdown [here](https://ashki23.github.io/markdown-latex.html#latex_basics) and more extensive references at [LaTeX Wikibooks](https://en.wikibooks.org/wiki/LaTeX/Mathematics). 

---
Copyright 2018-2019, [Ashkan Mirzaee](https://ashki23.github.io/index.html) | Content is available under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) | Sourcecode licensed under [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html)
