# Setting up a development environment
Using the online website [Overleaf](https://www.overleaf.com/) is probably the
easiest way to get started with LaTeX. 

Should you want to set something up locally, I would recommend
[VSCode](https://code.visualstudio.com/) + [LaTeX Workshop](https://neovim.io/)
or (for the more daring) [Neovim](https://neovim.io/) +
[VimTeX](https://github.com/lervag/vimtex). You will also need a local copy of
LaTeX; I recommend either [MiKTeX](https://miktex.org/) or [TeX
Live](https://tug.org/texlive/).

# Creating your first document

## Quickstart
Copy and paste the following boilerplate into your `.tex` file (I'll explain
what it does later) and try compiling it.

<details>
<summary>Boilerplate Code</summary>

```tex
\documentclass{article}

\usepackage[margin=1in]{geometry}
\usepackage{amssymb}
\usepackage{enumitem}

\title{First Document}
\author{Joe Bruin}
\date{1970-01-01}

\begin{document}
  \maketitle
  \section{Introduction}

  This is a document!

\end{document}
```
</details>

### What does it do?
```tex
\documentclass{article}
```
This line in the file declares the document type---In this case we are creating
an article, and will suffice for most projects.

```tex
\usepackage[margin=1in]{geometry}
\usepackage{amssymb}
\usepackage{enumitem}
```
These next three lines import a variety of symbols and functionalities from
packages in order to extend LaTeX's functionality.
* The `geometry` package sets the margins of the page to be 1 inch on all sides.
* The `amssymb` package imports a variety of math symbols.
* The `enumitems` package allows you to embed bullet and numbered lists in your
  document.

```tex
\title{First Document}
\author{Joe Bruin}
\date{1970-01-01}
```
These lines are pretty self-explanatory, and use LaTeX's built-in template for
making a title page using the `\maketitle` command.

```tex
\begin{document}
  \maketitle
  \section{Introduction}

  This is a document!

\end{document}
```
This final portion begins the actual document, using a document *environment*
(more on that later). The section header does what you think it does.

**Note:** LaTeX syntax uses backslashes `\` to demarcate what is regular text
from what is a command.

**Note 2:** Environments are similar to HTML tags
