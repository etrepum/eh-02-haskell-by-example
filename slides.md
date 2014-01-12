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

# Calling functions {.big-code .small-title}

* Function application looks like `function arg`.
* No parentheses.
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

# Basic IO {.big-code .small-title}

* `print`, `putStrLn`, `getLine`, &hellip;

# What can I do? {.small-title}

* Haskell's built-in functionality is all in the Prelude module
* Go to <http://www.haskell.org/hoogle/>
* Search for Prelude
* Click on the `module Prelude` result

[Intro to Haskell]: http://www.enginehere.com/courses/intro-to-haskell-etrepum/
