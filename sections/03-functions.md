Functions
================

[\<\<\< Previous](02-datatypes.md) | [Next \>\>\>](04-gettinghelp.md)

-----

> ## Learning Objectives
> 
>   - Understanding how to use pre-defined functions and arguments in R.
>   - Applying functions on vectors.
>   - Create a simple function from scratch.

-----

# Functions

We have been using a couple of different functions in the previous section such as `typeof()` and `length()`, and it's time to take a deeper look at what it is. When you want to make something happen in R, you can call a function. Most functions will produce results that you can see immediately, such
as the `sqrt()` (square root) function in R. `sqrt()` is part of the base R package that comes with your installation of R.

``` r
sqrt(16)
```

    ## [1] 4

You can think of functions as “canned scripts” that automate more
complicated sets of commands. The structure of “calling” (or “running”
or “executing”) a function is: `function(argument1, argument2, ...)`.
Calling the function results in some sort of output. Functions can take
one or a few inputs, or *arguments* (see below). The `sqrt()` function
has one argument, which we supply the value **16** to. It outputs, or
*returns*, a single numeric value.

## Arguments

The input you provide for your function are called arguments. Some
functions take a single argument while others take multiple.

``` r
#Example of a function that takes a single argument:
factorial(3)
```

    ## [1] 6

``` r
#Example of a function that takes multiple arguments:
paste("Hello", " World!", sep = "")
```

    ## [1] "Hello World!"

### args()

The `args()` function tells you what inputs, or *arguments* a function
recognizes.

``` r
#For example:
args(round)
```

    ## function (x, digits = 0) 
    ## NULL

From the output of `args(round)`, we know that this function takes 2
arguments, `x` and `digits`. Looking at the help documentation (you’ll
learn how to access that in a second), the `x` argument requires a
number or a set of numbers that you wish to round. The `digits` argument
requires a whole number that determines the number of decimal places you
want to round to. The `= 0` part of `digits = 0` denotes a default
value. In this instance, the `round()` function will round to the first
whole number if you don’t supply the `digits` argument with a value.

**Exercise 1**

See what arguments are within the `sum()` function. One of them is `...`
(ellipsis). Use Google to figure out what the `...` argument means.

-----

### Matching arguments

You can also use the names of the arguments to specify the input. If you
don’t use argument names, R will match your inputs based on the order
that they are written.

``` r
log(100, 10) 
```

    ## [1] 2

``` r
#is different from 
log(10, 100)
```

    ## [1] 0.5

Specifying your input with the argument names can help avoid potential
errors.

``` r
# both of these return the same value
log(x = 100, base = 10)
```

    ## [1] 2

``` r
log(base = 10, x = 100)
```

    ## [1] 2

### Default arguments

Some arguments are optional, such as `base` in `log()`. In the case of
an optional argument, you need not supply a value and the function will
still run. In this case, the `base` argument has a default value of
*exp(1)* and if you do not provide an alternative base value it will use
its default value. However, the argument of `x` is not optional and
requires an input or the function will not run.

### Code body

Typing the name of the function without the parentheses will return the
code that is stored in the function. A couple examples of where this can
be helpful are if you are performing a statistical test and you want to
know exactly how R is performing the calculations, or you are looking
for inspiration for writing your own functions. Here is an example with
the `cor()` function, which calculates correlations among variables. I
restricted the output to only the first ten lines here- there is a lot
of underlying code to calculate a correlation\!

``` r
cor
```

    ## function (x, y = NULL, use = "everything", method = c("pearson", 
    ##     "kendall", "spearman")) 
    ## {
    ##     na.method <- pmatch(use, c("all.obs", "complete.obs", "pairwise.complete.obs", 
    ##         "everything", "na.or.complete"))
    ##     if (is.na(na.method)) 
    ##         stop("invalid 'use' argument")
    ##     method <- match.arg(method)
    ##     if (is.data.frame(y)) 
    ##         y <- as.matrix(y)
    ...

## c() function

The `c()` function combines its arguments into a vector. This can be
very useful for creating data sets or when applying the same function on
a series of elements.

``` r
b <- c(1, 2, 3, 4)

# You can add one to each element of the vector
b + 1
```

    ## [1] 2 3 4 5

You can also name the elements in your vector to increase their
accessibility.

``` r
c <- c(pop = 10, soda = 20, cola = 30)

c
```

    ##  pop soda cola 
    ##   10   20   30

You can even combine existing vectors\! For instance, you may obtain
vectors from two different data sets that you want to combine for a
single analysis.

``` r
char_vector_2 <- c("But", "Python", "is", "ok", "too.")

c(char_vector, char_vector_2)
```

    ##  [1] "I"      "love"   "to"     "code"   "in"     "R."     "But"    "Python"
    ##  [9] "is"     "ok"     "too."

Note that all elements in the vectors have to be of the same type; if
they are different, this function will attempt to coerce them into the
same elements.

**Exercise 2**

You have a vector of limb measurements from your favorite frog species.

``` r
limb_meas <- c(humerus = 10, femur = 20, tibiofibula = 25)

limb_meas
```

    ##     humerus       femur tibiofibula 
    ##          10          20          25

However, you eventually want to compare these measurements with other
frog species, and limb measurements are highly correlated with body
size. You want to correct for this.

Body size is 40 mm.

``` r
body_size <- 40
```

The easiest way to correct for body size is to divide each measurement
by the body size. Do this so you can compare these measures with those
you collect from other species.

-----

## Functions that use vectors

Some functions require vectors. For example, the `mean()` function
computes the mean of a vector.

``` r
my_nums <- c(3, 5, 5)

mean(my_nums)
```

    ## [1] 4.333333

### Vectorized functions

Many R functions are *vectorized*. This means that when a vector with
more than one element is provided as input, the function will apply
separately for each element in the vector and return the results as a
new vector. Take the `factorial()` function (the factorial of 4 is 4 \*
3 \* 2 \* 1 = 24). It takes the factorial of each number in `my_nums`.

``` r
factorial(my_nums)
```

    ## [1]   6 120 120

Math is vectorized in R, as you’ve already seen.

You can apply some functions to multiple vectors, and R will apply the
function to each vector’s elements in order until it reaches the end of
the vector.

For instance, the `pmax` function finds the maximum among pairwise
comparisons of each element in a set of vectors. For instance,

``` r
vec <- c(1, 2, 3, 4, 5)

vec2 <- c(4, 3, 2, 6, 8)

pmax(vec, vec2)
```

    ## [1] 4 3 3 6 8

**Exercise 3**

You have two vectors that contain the words in a sentence.

``` r
sentence_1 <- c("I", "want", "a", "pet", "turtle.")

sentence_2 <- c("It", "will", "be", "green", "and", "brown!")
```

1)  Count the number of words in each sentence. Hint: each sentence is a vector. How can we find the length of a vector?

2)  Concatenate the two vectors and assign them to a new object (for
    simplicity, call it `sentences`). Hint: concatenate can be understood as combine in this case

3)  Now for a tricky task. Count the number of letters in the combined
    sentences. Hint: The nchar() function counts the number of letters in each word. You will then need a function to find the sum of each word in sentences. You will probably need to assign an intermediate variable.

-----

## The guts of a function

Now that we have gone over some of the basic components in a piece of R
code, let’s write a function\! This is not as intimidating or scary as
it seems, and can be very useful if you are performing the same set of
tasks over and over again. Although writing functions is a useful skill,
the main purpose of this section is to impress upon you that functions
aren’t magic black boxes that take input, perform magic, then give
something back.

In writing your own function, it follows a fairly standard template
\[1\]

``` r
function_name <- function(arg_1, arg_2, arg_3 = 2) {
  
  # do some useful stuff
  new_var <- sum(arg_1) + sum(arg_2) 
  
  # do some more useful stuff
  div_out <- new_var / arg_3
  
  # return the value
  return(div_out) 
}
```

`function_name` is the name of the funciton you’re creating. Name it
something that is easy to remember but does not clash with existing
functions in base R packages such as `mean()` or `sum()`. Although not
all R functions do this, it is good practice to use verbs for function
names.

`arg_1`, `arg_2`, and `arg_3` are your arguments. `arg_1` and `arg_2`
are mandatory because they have no default values, while `arg_3` has a
default value of 2, so it does not have to be specified.

`{}` is called the function body and it specifies the code that will run
when the function is called and applied. All of the code in your
function needs to fall between the two curly brackets. When writing your
own function, try to be concise, but clear. Remember, functions are to
help make your work run more efficiently\!

`return` is the last line of code that will return the value of the
function. Remember this last line of *code* is written within the `{}`\!

## Function to take an average.

Here you’re making your own version of the `mean()` function, called
`take_avg()`.

``` r
take_avg <- function(x){
  
  # this function takes the same of all values in x. Assumes x is a numeric vector
  s <- sum(x)
  
  # this counts the number of elements in x
  l <- length(x)
  
  # we're dividing the sum of values by the number of values to calculate the mean
  avg <- s / l
  
  # this specifies the value to be returned by the function
  return(avg)
}
```

Let’s take the average of a random vector of doubles.

``` r
v <- c(2.4, 3.65, 7.5, 1.22)

take_avg(v)
```

    ## [1] 3.6925

Super cool\! Well, at least I think so. To take a deeper dive into
writing your own functions, check out [this excellent chapter in R for
Data Science](https://r4ds.had.co.nz/functions.html).

## Recap exercise

**Exercise 4**

You’re interested in whether modern Western households stick to the
“three meals a day” norm that has persisted since the middle ages.
Work demands have increased and you think that people may be sherking a
meal in favor of more work time. In a preliminary survey of your
apartment complex, you surveyed four households and asked how many meals
each member consumes on average each day.

Complete the following to analyze your preliminary data.

1)  Check your data vectors to make sure you are indeed working with
    numeric data.

<!-- end list -->

``` r
# hh = household
hh_1 <- c(2, 3, 3)
hh_2 <- c(3, 2, 2, 3)
hh_3 <- c(2, 4)
hh_4 <- c(3, 2)
```

2)  Take the average of each household using the `take_avg()` function
    you created earlier. Assign each one to a unique object.
3)  Create a new vector of your averages.
4)  Visualize your new household averages using the `barplot()`
    function. Just put your object from step 3) inside the function,
    e.g. `barplot(hh_averages)`.
5)  Since you’re interested in average across households, take the
    average of your household averages. What does your preliminary
    survey tell you?

-----

## Answers

**Exercise 1**

``` r
args(sum)
```

    ## function (..., na.rm = FALSE) 
    ## NULL

From [this blog
post](https://www.r-bloggers.com/r-three-dots-ellipsis/): “…it means
that the function is designed to take any number of named or unnamed
arguments.”

**Exercise 2**

R is a vectorized language. Just like with the addition you performed
earlier, you can simply divide your body measurement vector by body size
(which happens to be a vector with a single element).

``` r
limb_meas_corrected <- limb_meas / body_size

limb_meas_corrected
```

    ##     humerus       femur tibiofibula 
    ##       0.250       0.500       0.625

**Exercise 3**

1)  
<!-- end list -->

``` r
# number of words in sentence 1
length(sentence_1)
```

    ## [1] 5

``` r
# number of words in sentence 2
length(sentence_2)
```

    ## [1] 6

2)  
<!-- end list -->

``` r
sentences <- c(sentence_1, sentence_2)

sentences
```

    ##  [1] "I"      "want"   "a"      "pet"    "turtle" "It"     "will"   "be"    
    ##  [9] "green"  "and"    "brown"

3)  
<!-- end list -->

``` r
# count the number of letters in each word
letter_count <- nchar(sentences)

# get the total number of letters
num_letters <- sum(letter_count)

num_letters
```

    ## [1] 36


**Exercise 4**

1)  
<!-- end list -->

``` r
typeof(hh_1)
## [1] "double"
typeof(hh_2)
## [1] "double"
typeof(hh_3)
## [1] "double"
typeof(hh_4)
## [1] "double"
```

2)  
<!-- end list -->

``` r
hh_avg_1 <- take_avg(hh_1)
hh_avg_2 <- take_avg(hh_2)
hh_avg_3 <- take_avg(hh_3)
hh_avg_4 <- take_avg(hh_4)
```

3)  
<!-- end list -->

``` r
all_avgs <- c(hh_avg_1, hh_avg_2, hh_avg_3, hh_avg_4)
all_avgs
```

    ## [1] 2.666667 2.500000 3.000000 2.500000

4)  
<!-- end list -->

``` r
barplot(all_avgs)
```

![](04-vectors_files/figure-gfm/unnamed-chunk-31-1.png)<!-- -->

5)  
<!-- end list -->

``` r
take_avg(all_avgs)
```

    ## [1] 2.666667

-----

[\<\<\< Previous](02-datatypes.md) | [Next \>\>\>](04-gettinghelp.md)

-----

1.  Modified template from [Nice R
    Code](https://nicercode.github.io/guides/functions/) and [Data
    Carpentry](https://datacarpentry.org/R-ecology-lesson/01-intro-to-r.html)
