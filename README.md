
# R Markdown and LaTeX
*[Ashkan Mirzaee](https://ashki23.github.io/index.html) - December 2018*

R Markdown is a file format for making dynamic HTML documents with R Studio. An R Markdown document is written in Markdown and could contain chunks of embedded source codes, LaTeX formula and graphics. A basic knowledge about Markdown and LaTeX is required to create HTML documents by R Markdown. This tutorial provides a quick reference to use Markdown and LaTeX.

# Markdown
The following provides quick references to the most commonly used R Markdown syntax.

## Headers
### H3
#### H4
##### H5
###### H6

```{markdown}
# Markdown
The following provides quick references to the most commonly used R Markdown syntax.

## Headers
### H3
#### H4
##### H5
###### H6
```

## Emphasis
*Italic* and **Bold**
```{markdown}
*Italic* and **Bold**
```

~~Scratched Text~~
```{markdown}
~~Scratched Text~~
```

Markdown doesn't support underline, but we can use <u>HTML Text</u> instead. Also, <b>we</b> can <i>render</i> almost any <span style="color:red;">HTML</span> code that we &nbsp; <kbd>like</kbd> &nbsp; such as superscript<sup>2</sup>.
```{markdown}
Markdown doesn't support underline, but we can use <u>HTML Text</u> instead. Also, <b>we</b> can <i>render</i> almost any <span style="color:red;">HTML</span> code that we &nbsp; <kbd>like</kbd>  &nbsp; such as superscript<sup>2</sup>.
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

```{markdown}
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

```{markdown}
1. Item 1
2. Item 2
3. Item 3
    - Item 3a
    - Item 3b
```

## Links
http://www.github.com/

```{markdown}
http://www.github.com/
```

[Github](http://www.github.com/)

```{markdown}
[Github](http://www.github.com/)
```

## Images

![Raspberry Pi](https://raw.githubusercontent.com/iiiypuk/rpi-icon/master/raspberry-pi-logo_resized_256.png)

```{markdown}
![Raspberry Pi](https://raw.githubusercontent.com/iiiypuk/rpi-icon/master/raspberry-pi-logo_resized_256.png)
```

Also, we can use HTML to add more styles:

```{markdown}
<img src="images/raspberry-pi-logo.png" alt="Raspberry Pi" style="width:50%; border:0;">
```

## Quotes
> Imagination is more important than knowledge.
>
> Albert Einstein

```{markdown}
> Imagination is more important than knowledge.
>
> Albert Einstein
```

## Horizontal Lines
Use three dashes `---` to draw an horizontal line like:

---

```{markdown}
---
```

## Tables
1st Header|2nd Header|3rd Header
:---|:---:|---: 
col 1 is|left-aligned|1           
col 2 is|center-aligned|2
col 3 is|right-aligned|3

```{markdown}
1st Header|2nd Header|3rd Header
---|:---:|---: 
col 1 is|left-aligned|1           
col 2 is|center-aligned|2
col 3 is|right-aligned|3
```

## Code blocks
In Markdown, we can simply add plain code blocks to display (not evaluating) by inserting ` ``` `. For example:
```
This text is displayed verbatim / preformatted
```
```{markdown}
` ``
This text is displayed verbatim / preformatted
` ``
```

For a plain R, or Python and other languages, we can use ` ```r ` or ` ```python ` and etc. For example:

```r
norm <- function(x) {
  sqrt(x%*%x)
}
norm(1:4)
```
```{markdown}
` ``r
norm <- function(x) {
  sqrt(x%*%x)
}
norm(1:4)
` ``
```

For inline plain codes, for example, we defined the `add` function to compute the sum of two numbers.

```{markdown}
we defined the `add` function to compute the sum of two numbers.
```

## Code chunks
In R Markdown, we can evaluate source codes such as R and Python. For example we can display and run the following R codes by inserting ` ```{program} `. For example:
```{markdown}
` ``{r}
summary(cars$dist)
summary(cars$speed)
` ``
```

We can also run Python codes in R Markdown. To do that, first we need to install `reticulate` package. 
```{markdown}
` ``{python}
n = 5  
while n < 10:
    print(n)
    n += 1
else:
    print(n)
` ``
```

R Markdown can execute code in many languages besides R and Python. Some of the available language engines include:

- SQL
- Bash
- Rcpp
- Stan
- JavaScript
- CSS
- Markdown

You can find more details [here](https://rmarkdown.rstudio.com/authoring_knitr_engines.html%23sql).

Also, we can evaluate inline codes. For example, there were 50 cars in the study.

```{markdown}
For example, there were `r nrow(cars)` cars in the study.
```

## Chunk options
Chunk output can be customized in R Markdown with arguments set in the `{}` of a chunk header.

```{r echo = FALSE, fig.align = "center", fig.cap = paste("Figure", 1:5, sep = " "), warning = FALSE}
plot(cars, main = "Main Title")
```

```{markdown}
` ``{r echo = FALSE, fig.align = "center", fig.cap = paste("Figure", 1:5, sep = " "), warning = FALSE}
plot(cars, main = "Main Title")
` ``
```

Above, we used the following arguments:

- `echo = FALSE` prevents code, but not the results from appearing in the finished file. This is a useful way to embed figures 
- `fig.align = "center"` center alignment of figures in the output document 
- `fig.cap = "..."` adds a caption to graphical results
- `warning = FALSE` prevents warnings that are generated by code from appearing in the finished

Some other important arguments are:

- `eval`: whether to evaluate the code chunk
- `include`: whether to include the chunk output in the final output document
- `results`: takes one of `hold/hide/asis/markup` 
- `collapse`: collapse all the source and output blocks from one code chunk into a single block
- `out.width`: width and of the plot in the final output file (can be `"100%"` or less) 
- `fig.align`: one of `left, right` and `center` 

You can learn more about knitr options [here](https://yihui.name/knitr/options/).

## YAML header
At the top of the R Markdown document, we can insert the following to adjust the final output.

```{markdown}
---
title: "Page Title"
subtitle: ""
author: "[Ashkan Mirzaee](https://ashki23.github.io/)"
institute: ""
date: "`r format(Sys.time(), "%d %B %Y")`"
abstract: ""
keywords: 
  - R markdown
  - R Studio
  - Anything
tags:
  - Anything
output:
  html_document:
    theme: default/paper/lumen/cosmo/yeti/flatly/sandstone/darkly/cerulean/journal/readable
    highlight: default/pygments/haddock/kate/textmate/tango/monochrome/espresso/zenburn
    code_folding: show/hide
    toc: true/false
    toc_depth: 3
    number_sections: true/false
    toc_float:
      collapsed: true/false
      smooth_scroll: true/false
    include:
      in_header: header.html (your header file)
      before_body: script.html (your script file)
      after_body: footer.html (your footer file)
    css: styles.css (your css file)
    keep_md: TRUE
---
```

`keep_md: TRUE` in last line or add `github_document` to outputs keep a Markdown file to use in GitHub or GitLab repositories. You may learn more about YAML header [here](https://bookdown.org/yihui/rmarkdown/html-document.html).

# LaTeX
A basic knowledge about LaTeX could help us to make better documents in R Markdown. You can find quick references to the most commonly used LaTeX syntax in R Markdown [here](https://ashki23.github.io/markdown_latex.html#latex_basics) and more extensive references at [LaTeX Wikibooks](https://en.wikibooks.org/wiki/LaTeX/Mathematics). 

---
Copyright 2018-2019, [Ashkan Mirzaee](https://ashki23.github.io/index.html) | Content is available under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) | Sourcecode licensed under [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html)
