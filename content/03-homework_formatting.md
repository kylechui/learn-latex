# How to set up LaTeX to do homework sets

W## Problem numbering
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

<details>
<summary>Advanced setup</summary>

Alternatively, you could also define a custom environment to handle writing your
problem statements. The following code does just that, with an optional
parameter of a problem number. Copy-paste this into your code before your
`\begin{document}` line, but after all of your `\usepackage` statements.

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
some spacing depending on whether or not you pass a problem number into it.
Recall that environments always come in `\begin{env}` and `\end{env}` pairs.
What the `\newenvironment` command does is run what's in the first set of curly
braces as the `\begin` line, and the second set as the `\end` line.

The way LaTeX handles passing parameters to custom commands is via the following
syntax:
* In the declaration line, we see an optional `[n]` marker. This tells us that
  there are going to be <img
  src="assets/n.png"></img>
  parameters. 
* Each of these parameters is referred to by what order it came in, using `#1`
  through `#n`.

We can then use

```tex
\begin{problem}{1}
  Prove that the sum of two odd numbers is even.
\end{problem}
```
to render the same text as we did before!

**Note:** If you want to omit a particular parameter, you *shouldn't* omit the
curly braces, i.e. you would write `\begin{problem}{}`.

**Note:** While this might not be useful for this particular use case, it comes
in handy when you need to use and re-use more complex code blocks.

</details>

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
