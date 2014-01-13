# Haskell by Example {.small-title}
<h2>Bob Ippolito</h2>
<h3>January 2014</h3>

Want to learn more? Take my [Intro to Haskell] course at<br/>
[enginehere.com/courses/intro-to-haskell-etrepum](http://www.enginehere.com/courses/intro-to-haskell-etrepum/)

# Getting Haskell

(In order of preference)

* Download from
  [haskell.org/platform](http://www.haskell.org/platform/)
* Use [FP Haskell Center](https://www.fpcomplete.com/page/project-build)
* Play with [tryhaskell.org](http://tryhaskell.org/)

# Interactive Haskell {.small-title}

* `λ>` is the interpreter prompt.
* The code to the right of it is what you type.
* Lines that start with `--` are comments.
* The line below is the result after pressing return.

# Haskell as a calculator {.big-code .small-title}

<style>
.code-table pre code { padding: 0; }
</style>
<table width="100%" class="code-table"><tr><td width="50%">
```haskell
λ> 486
486
λ> 137 + 349
486
λ> 1000 - 334
666
λ> -2 - (-3)
1
λ> 5 * 99
495
λ> 2 ^ 16
65536
```
</td><td>
```haskell
λ> -2
-2
λ> 1.1
1.1
λ> 10 / 5
2.0
λ> 2.7 + 10
12.7
λ> 0.1 * 1.0e4
1000.0
λ> 36 ** 0.5
6.0
```
</td></tr></table>

# Exercise 1 {.big-code .small-title}

* Try using Haskell's operators to find out what 2 to the 100th
  power is.
* If you're using the code window here, or FPComplete, the program should
  look like this, with `…` replaced by the expression you want to
  evaluate:

```haskell
main = print (…)
```

# In (prefix) form {.big-code .small-title}

<table width="100%" class="code-table"><tr><td width="50%">
```haskell
λ> -2
-2
λ> 1.1
1.1
λ> (/) 10 5
2.0
λ> (+) 2.7 10
12.7
λ> (*) 0.1 1.0e4
1000.0
λ> (**) 36 0.5
6.0
```
</td><td>
```haskell
λ> -2
-2
λ> 1.1
1.1
λ> 10 / 5
2.0
λ> 2.7 + 10
12.7
λ> 0.1 * 1.0e4
1000.0
λ> 36 ** 0.5
6.0
```
</td></tr></table>

# Exercise 2 {.small-title}

* Convert your program from Exercise 1 to use the operators in prefix
  form.

# Calling functions {.big-code .small-title}

* Function application looks like `function arg`.
* No parentheses required.
* Function application has the highest precedence (higher than any operator).

# Using functions {.big-code .small-title}

```haskell
λ> even 10
True
λ> negate 4
-4
λ> negate 1 + 10
9
λ> max 4 5
5
λ> True && not (False || True)
False
```

# &#96;infix&#96; syntax sugar {.big-code .small-title}

<table width="100%" class="code-table"><tr><td width="50%">
```haskell
λ> max 4 5
5
λ> div 10 2
5
λ> lcm 360 13
4680
λ> divMod 360 13
(27,9)
λ> elem 'a' "apple"
True
λ> elem 4 [1, 2, 3]
False
```
</td><td>
```haskell
λ> 4 `max` 5
5
λ> 10 `div` 2
5
λ> 360 `lcm` 13
4680
λ> 360 `divMod` 13
(27,9)
λ> 'a' `elem` "apple"
True
λ> 4 `elem` [1, 2, 3]
False
```
</tr></td></table>

# Exercise 3 {.big-code .small-title}

* Write an expression to calculate the last four decimal digits of `3 ^ 1337`.
* You can use the `mod` function for this, try evaluating these expressions:

```haskell
λ> mod 1234 100
…
λ> 1234 `mod` 10
…
```

# Let there be variables {.big-code .small-title}

* Variables must start with a lower-case letter or underscore.
* By convention, `theyAreWrittenLikeThis`.
* A leading underscore implies that it is an unused variable,
  but this is only used to silence compiler warnings.

# Using let {.big-code .small-title}

```haskell
λ> let x = 10 in x * x
100
λ> let { x = 10; y = 2 } in x * y
20
λ> let { x = 2 * y; y = 40 } in x * y
3200
λ> let { x = undefined; y = 2 } in y
2
λ> let { r = 2; area = pi * r * r } in area
12.566370614359172
```

# Exercise 4

* Use a `let` expression with variables `r` and `circumference` that
  evaluates to the circumference of a circle with that radius

# Define your own functions {.big-code .small-title}

* All functions in Haskell take exactly one argument
* &hellip; but there's syntax to make it seem like there
  are multi-argument functions!

# Functions and Lambdas (λ) {.big-code .small-title}

```haskell
-- this is far more common than lambda syntax
λ> let inc x = x + 1 in inc 10
11
λ> let add x y = x + y in add 1 2
3
```

```haskell
-- parentheses only used for clarity here
λ> let inc = (\x -> x + 1) in inc 10
11
λ> let add = (\x -> (\y -> x + y)) in add 1 2
5
```

# Exercise 5

* Refactor your implementation of Exercise 4 to use a function named
  `circumference` that takes an argument `r` and evaluates to the
  circumference of a circle with the given radius.
* Bonus: Try doing it with and without the `\lambda ->` syntax

# Lists

* Lists in Haskell are linked lists
* They are homogeneous, can only store one type in a list
* The constructors are `:` (which takes a value on the left and
  another list on the right) and `[]` which is the empty list
* There are several kinds of syntax sugar for creating lists

# Making lists

* ...

# Strings! {.big-code .small-title}

# Basic IO {.big-code .small-title}

* `print`, `putStrLn`, `getLine`, &hellip;

# What can I do? {.small-title}

* Haskell's built-in functionality is all in the Prelude module
* Go to <http://www.haskell.org/hoogle/>
* Search for Prelude
* Click on the `module Prelude` result

[Intro to Haskell]: http://www.enginehere.com/courses/intro-to-haskell-etrepum/
