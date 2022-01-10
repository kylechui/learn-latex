# How to set up LaTeX to do homework sets

## Problem numbering
One simple way to do this is to make use of the `\textbf` command (text bold
face). It takes a parameter as input and renders it in bold face. For example,
we could write:
```tex
\textbf{Problem 1.} Prove that the sum of two odd numbers is even.
```
and it would render as
<center>
  <img src="assets/03-01.png"></img>
</center>

## Writing solutions
For proofs classes, we use the `proof` environment provided by the `amsthm`
package to generate a nice template for us. For example, we can write a simple
solution to the above problem as follows:
```tex
\begin{proof}
  Let $m, n$ be odd integers. Thus we may write $m = 2j + 1$ and $n = 2k + 1$
  for some integers $j, k$. Hence
  \[
    m + n = (2j + 1) + (2k + 1) = 2j + 2k + 2 = 2(j + k + 1).
  \]
  Therefore $m + n$ is even.
\end{proof}
```
<center>
  <img src="assets/03-02.png"></img>
</center>

## Lists
The two main ways to create lists in LaTeX are using the `enumerate` and
`itemize` environments. The former is used to create "ordered" lists, whereas the
latter is for "unordered" lists. By default, `enumerate` numbers off your items
in the form `n.`, whereas `itemize` just creates a bulleted list. The syntax is
as follows (and is the same for itemize):
```tex
\begin{enumerate}
  \item % First item in the list
  \item % Second item in the list
  \item % And so on and so forth...
\end{enumerate}
```

**Note:** By default, both `enumerate` and `itemize` will change the item prefix
when you nest environments. For example, the `itemize` environment starts with
solid bullets and then indents to empty bullet points when you nest
environments. 

If you prefer to use a different method for listing off your items, you may
include an *optional* parameter to change the schema. Say you want to use
letters instead of numbers:

```tex
\begin{enumerate}[label=\alph*)]
  \item % This will be preceded by a)
  \item % This will be preceded by b)
  \item % And so on and so forth...
\end{enumerate}
```

In this case the `\alph*` denotes the usage of lowercase letters, and the
closing parenthesis is the literal closing parenthesis that appears in the list.
Other naming commands include `\roman`(roman numerals) and `\arabic`(regular
numbers).

## Typefaces (fonts, boldness, italics, etc.)
There are a few different ways that you might want to format text for math
applications:
* Italics and boldface can both be applied using `\textit` or `\emph`, and
  `\textbf`, respectively.

An example of the above styles:

<img src="assets/03-03.png"></img>

and the corresponding code:
```tex
\emph{This is italics!} \textbf{This is bold!}
```

* There are also three main fonts that are useful to know (code samples below):
  * `\mathbb` or "blackboard": Used to style sets like the reals, <img
    src="assets/mathbb_R.png"></img>.
  * `\mathscr` or "script": I only really use it for the power set, <img
    src="assets/mathscr_P.png"></img>.
  * `\mathcal` or "calligraphic": Laplace transform, big O notation, etc., <img
    src="assets/03-04.png"></img>.

They're all implemented in the same way as before, i.e. `\mathbb{R}`,
`\mathscr{P}`, and `\mathcal{O}(n^2)`.

**Note:** These last three fonts can only be applied in math/display mode, so be
sure to remember your `$`!

**Note:** You'll need the `mathrsfs` package in order to use the `\mathscr`
typeface.

## Whitespace commands
Here's a list of common whitespace commands that you might want to use:
* `\\` --- Starts a new line
  * Can take an optional parameter like `\\[10pt]` to add more whitespace after
* `\par` --- Starts a new paragraph (similar to `\\`, but with different
  indentation rules)
* `\newpage` --- Starts a new page
* `\hspace{5pt}` --- Puts horizontal space on the page
* `\vspace{20pt}` --- Puts vertical space on the page

## Syntax sugar

Oftentimes there are a few commands that are used frequently, that are a bit of
a pain to type out every single time. Here we will define macros, or shortcuts,
to help you focus on the math and not the syntax.

### `\newcommand`

You can define custom commands via `\newcommand`. The syntax is as follows:

```tex
\newcommand{key}[number of parameters]{value}
```
**Note:** If your custom command won't need to take in any parameters (i.e. it's
just an alias), you may omit the middle portion of the above command.

To access the values in the <img src="assets/n.png"></img>th parameter, we just
use `#n`.

Here are a few examples of how you might use custom commands:
```tex
\newcommand{\R}{\mathbb{R}}     % real numbers
\newcommand{\eps}{\varepsilon}  % better epsilon

\newcommand{\tuple}[1]{\left\langle #1 \right\rangle} % dynamically-sized tuples
\newcommand{\set}[1]{\left\{#1\right\}}               % dynamically-sized sets
```

The latter two commands would be used via `\set{x : x < \frac{1}{2}}` or
`\tuple{1, x, \frac{1}{2}x^2}`.

Not only do these macros save you time while typing, but also clean up your
code, making it easier to read through and make edits.

### `\newenvironment` [optional]

Similar to `\newcommand`, the `\newenvironment` allows you to define macros, but
for `\begin{env}` and `\end{env}` pairs. Say for instance we want to create a
`problem` environment, that accomplishes something similar to what we had
before. We could then write

```tex
\newenvironment{problem}[1]
  {
    \ifx &#1& \textbf{Problem. }
    \else \textbf{Problem #1.} \fi
  }
  {
  }
```

You don't need to worry too much about the if statement syntax, it just formats
some spacing depending on whether or not you pass a problem number into it. What
the `\newenvironment` command does here is run what's in the first set of curly
braces as `\begin{problem}`, and what's in the second set as `\end{problem}`.

We can then use

```tex
\begin{problem}{1}
  Prove that the sum of two odd numbers is even.
\end{problem}
```
to render the same text as we did before!

**Note:** If you want to omit a particular parameter, you *shouldn't* omit the
curly braces, i.e. you would write `\begin{problem}{}` to omit the problem
number.

**Note:** While this might not be useful for this particular use case, it comes
in handy when you need to use and re-use more complex code blocks.
