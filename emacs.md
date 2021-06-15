# Emacs: a powerful text editor
*[Ashkan Mirzaee](https://ashki23.github.io/index.html)*

A text editor provides an environment to write and edit plain text files
such as source codes. Many would like to use IDEs to write and run
source codes. That might be very useful for small programs, but as long
as your projects being larger, writing and editing codes with IDEs
become a very tedious task. [Emacs](https://www.gnu.org/software/emacs/)
is one of the best text editors that let us edit and write source codes
faster and easier. It might be very challenging to start using any
editors like Emacs, but it is definitely worth to spend some time to
learn the first steps. This tutorial provides a list of commands,
configurations and features that we need to begin.

-----

## Installation

To start working Emacs you might need to install it first. To install
Emacs follow the instruction at [GNU
Emacs](https://www.gnu.org/software/emacs/download.html). Briefly for:

  - Linux (Debian) use `sudo apt install emacs`
  - Mac use [binaries](https://emacsformacosx.com/) - see config
    [here](https://github.com/ashki23/Linux-notes/blob/master/mac-terminal.md)

## Config file

Use a text editor to create Emacs config file called `.emacs` in the
home directory `cd ~` then insert the following to make our very
preliminary configurations by:

``` lips
;; Add MELPA
(package-initialize)
(add-to-list 'package-archives '("melpa" . "http://melpa.org/packages/") t)

;; Personal information
(setq user-full-name "Your Name"
      user-mail-address "your@email.com")

;; Backup in one place
(setq backup-directory-alist '(("" . "~/.emacs.d/backup")))

;; Turn on bracket match highlight
(show-paren-mode 1)

;; Auto insert closing bracket
(electric-pair-mode 1)
```

Note that we can use `(setq make-backup-files nil)` and
`(electric-indent-mode -1)` to disable automatic backup and new lines
auto-indentation.

## Commands

The following are some important commands in Emacs. Note that `C` and
`M` stand for `Ctrl` and `Alt` respectively.

  - `C-x C-c`: exit
  - `C-z`: suspend
  - `C-k`: kill the line
  - `C-w`: cut the line/text
  - `M-w`: copy the line/text
  - `C-y`: uncut/paste the line/text (yank)
  - `C-space arrow keys`: select text
  - `C-shift arrow keys`: select paragraphs
  - `C-x u`: undo
  - `C-a`: move to the beginning of the line
  - `C-e`: move to the end of the line
  - `M-left`: one word left
  - `M-right`: one word right
  - `C-home/M-<`: move to the beginning of the buffer
  - `C-end/M->`: move to the end of the buffer
  - `M-g g`: go to line
  - `C-s/C-r`: search/reverse search
  - `M-%`: replace
  - `C-g`: stop a command
  - `C-x C-f`: make/open a file as a new buffer
  - `C-x b`: change the buffer
  - `C-x k`: kill the buffer
  - `C-x 1`: close other windows
  - `C-x 0/q`: close/quit windows
  - `C-x o`: switch to other windows
  - `C-h ?`: help list
  - `C-h t`: tutorial
  - `C-h d`: search help for a pattern
  - `C-h c`: show help for the command
  - `M-x <command>`: run commands
  - `M-x ispell`: spell check; enter the suggested `digit` or `a` to
    accept and `r` to rewrite
  - `M-x package-install`: install packages
  - `M-x package-list-packages`: list of packages

You may find more details in:

  - [7 Basic Editing
    Commands](https://www.gnu.org/software/emacs/manual/html_node/emacs/Basic.html#Basic)
  - [Emacs
    manual](https://www.gnu.org/software/emacs/manual/html_node/emacs/index.html)

## Customize faces

An easy way to change the appearance of Emacs is changing faces. `M-x
list-faces-display` shows current faces that can be modified (use GUI
Emacs to access them by clicking). To customize certain faces, use `M-x
customize-face` and select the face that you want to change (press tab
to see all options).

Also, we are able to customize faces from Emacs config file. For
instance, adding the following to the `.emacs` file will change some
faces in the Emacs terminal mode:

``` lips
;; Customize faces
(custom-set-faces
 '(font-lock-builtin-face ((t (:foreground "SkyBlue1"))))
 '(font-lock-comment-delimiter-face ((t (:foreground "salmon"))))
 '(font-lock-comment-face ((t (:foreground "chocolate1" :slant oblique))))
 '(font-lock-constant-face ((t (:foreground "lime green"))))
 '(font-lock-doc-face ((t (:foreground "light coral" :slant oblique))))
 '(font-lock-function-name-face ((t (:foreground "green" :weight bold))))
 '(font-lock-keyword-face ((t (:foreground "SteelBlue1" :weight bold))))
 '(font-lock-preprocessor-face ((t (:foreground "cornflower blue" :slant italic))))
 '(font-lock-regexp-grouping-backslash ((t (:weight bold))))
 '(font-lock-regexp-grouping-construct ((t (:weight bold))))
 '(font-lock-string-face ((t (:foreground "violet" :slant italic))))
 '(font-lock-type-face ((t (:foreground "green" :weight bold))))
 '(font-lock-variable-name-face ((t (:foreground "lime green"))))
 '(font-lock-warning-face ((t (:foreground "dark orange" :weight bold))))
 '(minibuffer-prompt ((t (:foreground "lime green" :weight bold)))))
```

To change the theme use `M-x load-theme`, then press `tab` to see list
of the available themes. To unload the theme use, `M-x disable-theme`.
Also, we can set a theme permanently, by adding `(load-theme
'<theme-name>)` to the `.emacs` init file. For example:

``` lips
;; Load tango-dark theme
(load-theme 'tango-dark)
```

## Install packages

In Emacs we can install extra packages based on our needs. To install a
new package, press `M-x` and type `package-refresh-contents` to fetch
all packages and then use `M-x package-install` and enter the new
package’s name. For example we can install Markdown-mode, htmlize, ESS
(R-mode), autocomplete-mode and
[Jedi](https://tkf.github.io/emacs-jedi/latest/) with:

``` lips
M-x package-install markdown-mode
M-x package-install htmlize
M-x package-install ess
M-x package-install auto-complete
M-x package-install jedi
```

To see list of the available packages use `M-x package-list-packages`.
And to delete packages, use `M-x package-delete` and enter the package’s
name. Note that you may use `C-s / C-r` for searching and `C-g` to
cancel any actions and `q` to close buffers in Emacs.

## Org-mode

[Org website](https://orgmode.org) describes “Org mode is for keeping
notes, maintaining TODO lists, planning projects, and authoring
documents with a fast and effective plain-text system”. Org-mode in
Emacs is very similar to Markdown. They let us combine text and codes
and evaluate codes and generate PDF or HTML outputs. Following are great
resources to learn Org:

  - [Org mode beginning at the
    basics](https://orgmode.org/worg/org-tutorials/org4beginners.html)
  - [Org tutorials](https://orgmode.org/worg/org-tutorials/index.html)

Recent Emacs includes Org mode, to begin, use `emacs test.org` to create
an Org file by Emacs.

### Introduction

Let’s learn how use *org-mode* to:

  - insert headlines `M-enter`
  - move headlines up and down `M-up/down`
  - fold/unfold `tab/shift-tab`
  - insert blocks
      - example blocks `<e-tab`
      - source code blocks `<s-tab`
          - for example org/bash/python
  - create tables
  - create TODO items
  - save `C-x C-s`, export `C-c C-e`, and exit `C-x C-c`
      - use `C-c C-e` and press `h` and then `o` to see HTML output

To create above list in Org use:

``` org
 ** Introduction
 Let's learn how use *org-mode* to:
 - insert headlines (=M-enter=) - press =M-enter= to go to the next line
 - move headlines up and down (=M-up/down=)
 - fold/unfold (=tab/S-tab=)
 - insert blocks 
   - example blocks (=<e-tab=)
   - source code blocks (=<s-tab=) 
     - for example org/bash/python
 - create tables
 - create TODO items
 - save (=C-x C-s=), export (=C-c C-e=), and exit (=C-x C-c=)
   - use =C-c C-e= and press =h= and then =o= to see HTML output
```

Use `M-up/down` to see how easy we can move headlines and use `C-c C-e h
o` to see the outputs in the browser.

**Note:** *unordered* lists in Org start with **-** or **+** and
*ordered* lists start with **a number and a dot** and descriptions use
**::**.

**For example**, this is an *ordered* list:

1.  First - press `M-enter`
2.  Second - press `M-enter`
3.  Third is a link to [org-mode](https://orgmode.org/) website

To create above list in Org use:

``` org
*For example*, this is an /orderd/ list:
 1. First - press =M-enter=
 2. Second - press =M-enter=
 3. Third is a link to [[https://orgmode.org/][org-mode]] website
```

### Tables

The following is table of key abbreviations:

| Name    | key   | Abbr. |
| ------- | ----- | ----- |
| Control | Ctrl  | C     |
| Meta    | Alt   | M     |
| Shift   | Shift | S     |
| Return  | Enter | RET   |

    | Name    | key   | Abbr. |
    |---------+-------+-------|
    | Control | Ctrl  | C     |
    | Meta    | Alt   | M     |
    | Shift   | Shift | S     |
    | Return  | Enter | RET   |

To create above table in org, we only need to insert `|Name|Key|Abbr.`
and press `tab` to make new row and insert `-tab` (i.e. `dash tab`) to
draw the hline and press `tab`. Also you can use (these might be
different in different OS):

  - `M-up/down` to move rows
  - `M-left/right` to move columns
  - `M-S-up/down` to add/remove rows
  - `M-S-left/right` to add/remove columns

We can use `<c>`, `<l>` or `<r>` for center, left or right alignment.

### Basic TODO

To create a TODO list you only need:

``` org
 ** TODO learn org-mode
 ** DONE learn emacs
    DEADLINE: <2019-11-16 Sat>
```

To change a TODO task to DONE or remove it use `S-left/right`. Use `C-c
C-d` to add a deadline.

### LaTeX

We can use LaTeX to write equations in Org. For example:

``` org
#+BEGIN_SRC latex
\begin{equation}
x=\sqrt{b}
\end{equation}
If $a^2=b$ and $b=2$, then the solution must be either $$a=+\sqrt{2}$$ or $$a=-\sqrt{2}$$
#+END_SRC
```

Org processes LaTeX codes in the HTML/PDF outputs.

---

Copyright 2018-2019, [Ashkan Mirzaee](https://ashki23.github.io/index.html) | Content is available under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/) | Sourcecode licensed under [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html)
