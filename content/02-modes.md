# LaTeX modes

There are three basic modes that constitute LaTeX code:
* Text mode: renders regular text in a
  [WYSIWYG](https://en.m.wikipedia.org/wiki/WYSIWYG) fashion
* Math mode: renders *in-line* math
* Display mode: renders math in a larger format, typically on its own line

## Math mode

Anything that is between two dollar signs `$` or escaped parentheses `\(` and
`\)` is considered to be in math mode, for example

```tex
$x^{2} - x - 1 = 0$
```
would get rendered as 
  <img src="assets/02-01.png"></img>.

**Note:** Variables rendered in math mode will get special formatting and will
look different from the same variable rendered in text mode. For example,
observe the difference between <img src="assets/x.png"></img> and <img
src="assets/02-02.png"></img>.

The characters `^` and `_` denote superscripts and subscripts, respectively. The
curly braces after `^` or `_` denote that we are grouping them together
to all be super/sub scripted. To actually render curly braces (say, for set
notation), escape them, i.e. `\{` and `\}`.

**Note:** When the exponent is only one digit or one variable, i.e. `2` or
`\alpha`, it is fine to omit the curly braces for the exponent, and LaTeX will
choose the first valid item after the `^` to be superscripted. In the previous
example, we could have opted to write `$x^2 - x - 1 = 0$` instead.

Many of the symbols that you will need to typeset, say Greek letters, are
relatively easy to remember. It is simply a matter of memorizing the command
names, such as `\alpha` and `\implies`. I recommend searching them up as you come
across them, or if you cannot remember their names, use
[Detexify](https://detexify.kirelabs.org/classify.html) to decipher a drawing of
the symbol you're imagining.

## Display mode

While similar to math mode, equations rendered in display mode take up more
space, which changes how some math terms are displayed. Elements are rendered
using display mode when they are between double dollar signs `$$` (not
recommended), or escaped square brackets `\[` and `\]`. For example,

```tex
\[
  a_2x^2 + a_1x + a_0 = \frac{1}{2}.
\]
```
would be rendered as
<center>
  <img src="assets/02-03.png"></img>
</center>
In particular, fractions, limits, summations, and integrals will exhibit
different behavior.

**Note:** The fraction command `\frac` takes in two parameters that are enclosed
in curly braces, the former being the numerator and the latter the denominator.
What would happen if you rendered the fraction `\frac{2}{3}` in regular math
mode instead of display mode?
