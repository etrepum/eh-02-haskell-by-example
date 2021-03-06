# Haskell by Example {.small-title}
<h2>Bob Ippolito</h2>
<h3>January 2014</h3>

Want to learn more? Take my [Intro to Haskell] course at<br/>
[enginehere.com/courses/intro-to-haskell-etrepum](http://www.enginehere.com/courses/intro-to-haskell-etrepum/)

# Getting Haskell {.big-code .small-title}

(In order of preference)

* Download from
  [haskell.org/platform](http://www.haskell.org/platform/)
* Use [FP Haskell Center]
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
* If you're using the code window here, or [FP Haskell Center], the program should
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

# Exercise 2 {.big-code .small-title}

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

# What can I do? {.small-title}

* Haskell's built-in functionality is all in the Prelude module
* Go to <http://www.haskell.org/hoogle/>
* Search for Prelude
* Click on the `module Prelude` result
* Keep this tab open :)

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

# Exercise 4 {.big-code .small-title}

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

# Exercise 5 {.big-code .small-title}

* Refactor your implementation of Exercise 4 to use a function named
  `circumference` that takes an argument `r` and evaluates to the
  circumference of a circle with the given radius.
* Bonus: Try doing it with and without the `\lambda ->` syntax

# Lists {.big-code .small-title}

* Lists in Haskell are linked lists
* They are homogeneous, can only store one type in a list
* The constructors are `:` and `[]`
* There are several kinds of syntax sugar for creating lists

# Making lists {.big-code .small-title}

```haskell
λ> [1, 2, 3, 4]
[1,2,3,4]
λ> 1 : 2 : 3 : 4 : []
[1,2,3,4]
λ> (:) 1 ((:) 2 ((:) 3 ((:) 4 [])))
[1,2,3,4]
λ> ['a', 'b', 'c', 'd']
"abcd"
λ> 'a' : 'b' : "cd"
"abcd"
λ> [True, 1 == 0, 1 > 0]
[True,False,True]
λ> [1, 2] ++ [3, 4]
[1,2,3,4]
```

# Strings! {.big-code .small-title}

* Strings in Haskell are lists of Char, or `[Char]`
* They support the full range of unicode
* There are other data types for bytes and text in the Haskell
  Platform that can be more efficient, but we'll start with String

# Exercise 6 {.big-code .small-title}

* Implement a function named `showNumber` that given a number,
  evaluates to the string "Your number is: " with the given number
  as a string appended to it.
* For example: `showNumber 10` would evaluate to<br/>`"Your number is: 10"`
* HINT: Use the `show` function to do this, `show 10` evaluates to `"10"`

# If/then/else {.big-code .small-title}

* if *predicate* then *consequent* else *alternative*

```haskell
fib x =
  if x > 1 then fib (x - 1) + fib (x - 2) else x

fib x =
  if x > 1
    then fib (x - 1) + fib (x - 2)
    else x
```

# Exercise 7 {.big-code .small-title}

* Implement a function named `fac` that given a positive integer,
  evalues to the factorial of that number.
* In pseudocode:
  `fac n = n * (n - 1) * (n - 2) * … * 2 * 1`

# Pattern matching {.big-code .small-title}

```haskell
fib x =
  case x of {0 -> 0; 1 -> 1; _ -> fib (x-1) + fib (x-2)}

fib x = case x of
  0 -> 0
  1 -> 1
  _ -> fib (x - 1) + fib (x - 2)
  
fib 0 = 0
fib 1 = 1
fib x = fib (x - 1) + fib (x - 2)
```

# Matching lists {.big-code .small-title}

```haskell
lastElem [] = error "empty list"
lastElem (x : []) = x
lastElem (_ : xs) = lastElem xs

lastElem [] = error "empty list"
lastElem [x] = x
lastElem (_ : xs) = lastElem xs
```

# Exercise 8 {.big-code .small-title}

* Implement a function named `firstElem` that evaluates to the first element
  of the given list, or `error "empty list"` if given an empty list.
* Use only pattern matching and recursion to implement this function.
* Example: `firstElem [1,2,3] == 1`

# Exercise 9 {.big-code .small-title}

* Implement a function named `nth` that evaluates to the nth element of a
  list (with zero based indexing), or `error "index too large"` if the list
  is too short.
* Use only pattern matching and recursion to implement this function.
* Example: `nth 1 [1,2,3] == 2`

# Guards {.big-code .small-title}

* Guards are great syntax sugar for checking conditions
* Can be used with case or when defining functions
* `otherwise` is equivalent to `True`

```haskell
evens xs = case xs of
  [] -> []
  (x : xs') | x `rem` 2 == 0 -> x : evens xs'
            | otherwise      -> evens xs'

evens [] = []
evens (x:xs)
  | x `rem` 2 == 0 = x : evens xs
  | otherwise      = evens xs
```

# Exercise 10 {.big-code .small-title}

* Using guards, implement `select` which returns the list elements
  that match the given predicate.
* Example: `select (>5) [2,4,6,8,10] == [6,8,10]`

# foldr {.big-code .small-title}

* `foldr` is a right fold, which can be used to implement many other
  functions on lists
* You can think of it as replacing `:` with `k` and `[]` with `z`

```haskell

foldr k z []     = z
foldr k z (x:xs) = x `k` foldr k z xs
```

# map {.big-code .small-title}

* `map` is a commonly used list function that can be expressed
  in terms of `foldr`
* `map (+1) [1,2,3,4] == [2,3,4,5]`

```haskell

map f xs = foldr (\x acc -> f x : acc) [] xs
```

# Simplifying map {.big-code .small-title}

```haskell

map f xs = foldr (\x acc -> f x : acc) [] xs

-- eta-reduction, remove xs from both sides
map f = foldr (\x acc -> (f x : acc)) []

-- rewrite in prefix form
map f = foldr (\x acc -> (:) (f x) acc)) []

-- eta-reduction of inner function
map f = foldr (\x -> (:) (f x))) []

-- reduce inner function further with .
map f = foldr ((:) . f) []
```

# Going point-free {.big-code .small-title}

* Some people call this "pointless". I agree in many cases.

```haskell
map f = foldr ((:) . f) []

-- move arguments around for easier reduction
map f = flip foldr [] ((:) . f)

-- reduce further with .
map = flip foldr [] . ((:) .)

-- rewrite flip using an infix section
map = (`foldr` []) . ((:) .)

-- What does this accomplish?
-- Not much. Don't bother.
-- But you may see code like this.
```


# Exercise 11

* Implement `select` from Exercise 10 using `foldr` without any
  explicit recursion
* `select (>5) [2,4,6,8,10] == [6,8,10]`


# Basic IO {.big-code .small-title}

* Programs don't do anything without IO
* Haskell will call your main function and interpret IO actions
* IO actions can be sequenced, or combined

# Running Haskell programs {.big-code .small-title}

* The EngineHere code runner doesn't support input
* Please use a locally installed Haskell to run these
* Or use [FP Haskell Center], which does support input
* Create the .hs file with a text editor and use `runhaskell` to
  interpret them

# putStr {.big-code .small-title}

Hello.hs
```haskell
main = putStr "hello\n"
```

<hr/>

```bash
$ runhaskell Hello.hs
hello
```

# putStrLn {.big-code .small-title}

Hello.hs
```haskell
main = putStrLn "hello"
```

<hr/>

```bash
$ runhaskell Hello.hs
hello
```

# print {.big-code .small-title}

Hello.hs
```haskell
main = do
  print "hello"
  putStrLn (show "hello")
  putStr (show "hello" ++ "\n")
```

<hr/>

```bash
$ runhaskell Hello.hs
"hello"
"hello"
"hello"
```

# getLine {.big-code .small-title}

* `<-` binds the result of an IO action to a variable

```haskell
main = do
  putStrLn "Enter your name:"
  name <- getLine
  putStrLn ("You entered: " ++ name)
```

# return {.big-code .small-title}

* `return` creates an IO action from a value
* It has nothing to do with exiting a function!

```haskell
main = do
  putStrLn "Enter your name:"
  name <- return "Bob"
  putStrLn ("You entered: " ++ name)
```

# Recursion in IO {.big-code .small-title}

* You can press ^C (Control and C at the same time) to abort this!

```haskell
main = do
  putStrLn "Enter your name:"
  name <- return "Bob"
  putStrLn ("You entered: " ++ name)
  main
```

# State {.big-code .small-title}

```haskell
nameLoop names = do
  putStrLn "Who are you?"
  name <- getLine
  if name `elem` names
    then do
      putStrLn ("I already know " ++ name)
      nameLoop names
    else do
      putStrLn ("Nice to meet you " ++ name)
      nameLoop (name : names)

main = nameLoop []
```

# Modules {.big-code .small-title}

# Types {.big-code .small-title}

# Defining types {.big-code .small-title}

[Intro to Haskell]: http://www.enginehere.com/courses/intro-to-haskell-etrepum/
[FP Haskell Center]: https://www.fpcomplete.com/page/project-build
