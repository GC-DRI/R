Data types and Objects
================

[\<\<\< Previous](01-introduction.md) | [Next \>\>\>](03-functions.md)

-----

> ## Learning Objectives
> 
>   - Describe the different data types in R and use `typeof()` function to identify data types.
>   - Understand R objects and how to create them.
>   - Learn about vectors in R

-----

# Data types

Data type are classifications associated with specific data that let the computer know how to interpret the value and how a programmer intends to use a piece of data. We've already encoutered a data type, integers, in the previous section when we tried the expression `3 + 3`. Data types are common in many programming language, and each *data type* has its own unique properties. In R, certain functions can only take specific data types, and attempts at using a different data type can result in errors. 

Here is a list of some of the data types you might use:

  - `int` stands for integers, or whole numbers.

  - `dbl` stands for doubles, or numbers with decimals.

  - `chr` stands for character vectors, or strings.

  - `dttm` stands for date-times (a date + a time).

  - `lgl` stands for logical, vectors that contain only TRUE or FALSE.

  - `fctr` stands for factors, which R uses to represent categorical
    variables with fixed possible values.

  - `date` stands for dates.

## typeof()

`typeof()` is a handy function that returns the data type of your data. If you’re ever in doubt, check your data with `typeof()`\! 

``` r
typeof(5.44445)
```

    ## [1] "double"
    
``` r
typeof("hello!")
```

    ## [1] "character"

But wait, you might ask what is a function? For now, you can think of a function as a a way of doing something, a way of saving some code for reuse, and a way of taking an input, transforming that input, and returning an output. In the next sections, we will be learning more about functions.

-----

# Creating objects

As seen previously, you can get an output from R simply by typing math in the console:

``` r
5 * 30
```

    ## [1] 150

``` r
2 / 3
```

    ## [1] 0.6666667

However, you often need to save output or *values* to *objects*. Storing
values in objects allows you to do interesting things with them later.
To create an object, you pick a succinct, easy to remember name and then
use the assignment operator `<-` to give the name a value. The format is
`name <- value`. The value on the right is assigned to the object on the
left.

For instance:

``` r
head_size <- 40
```

This statement can be interpreted as “40 **goes into** head\_size”. For
historical reasons, you can also use `=` for assignments, but not in
every context. Because `=` can throw unexpected results in some
situations, it is good practice to always use `<-` for assignments.

**Quick tip**: In RStudio, typing <kbd>Alt</kbd> + <kbd>-</kbd> (push
<kbd>Alt</kbd> at the same time as the <kbd>-</kbd> key) will write `<-`
in a single keystroke in a PC, while typing <kbd>Option</kbd> +
<kbd>-</kbd> (push <kbd>Option</kbd> at the same time as the
<kbd>-</kbd> key) does the same in a Mac.

Objects can be given any name such as `x`, `body_size`, or
`signal_length`. You want your object names to be explicit and not too
long. They cannot start with a number (`2x` is not valid, but `x2` is).
R is case sensitive (e.g., `weight_kg` is different from `Weight_kg`).
There are some names that cannot be used because they are the names of
fundamental functions in R (e.g., `if`, `else`, `for`, see
[here](https://stat.ethz.ch/R-manual/R-devel/library/base/html/Reserved.html)
for a complete list). In general, even if it’s allowed, it’s best to not
use other function names (e.g., `c`, `T`, `mean`, `data`, `df`,
`weights`). If in doubt, check the help to see if the name is already in
use. It’s also best to avoid dots (`.`) within an object name as in
`my.data`. There are many functions in R with dots in their names for
historical reasons, but because dots have a special meaning in R (for
methods) and other programming languages, it’s best to avoid them. It is
also recommended to use nouns for object names, and verbs for function
names. It’s important to be consistent in the styling of your code
(where you put spaces, how you name objects, etc.). Using a consistent
coding style makes your code clearer to read for your future self and
your collaborators. In R, three popular style guides are
[Google’s](https://google.github.io/styleguide/Rguide.html), [Jean
Fan’s](http://jef.works/R-style-guide/) and the
[tidyverse’s](https://style.tidyverse.org/). The tidyverse’s is very
comprehensive and may seem overwhelming at first. You can install the
[lintr](https://github.com/jimhester/lintr) package to automatically
check for issues in the styling of your code.

**Exercise 1**

Which of the following object names is *invalid*?

1)  site\_num

2)  R2

3)  1st\_try

4)  fish.scale.size

-----

You might have noticed that assigning a value to an object doesn’t print
anything. To print the value, you can either use parentheses around the
assignment or type the object name:

``` r
head_size <- 40 # doesn't print anything
(head_size <- 40) # prints output
```

    ## [1] 40

``` r
head_size # prints output if you've already assigned a value to the object
```

    ## [1] 40

Important aside: The comments written to the right of the hash mark
don’t get run as code. Using informative comments is good coding
practice. Clear comments are essential for when you want someone else to
run your code and be able to interpret what you’re typing. In addition,
they’re critical for you to understand what you did when you have to
read your code two months (*years*, *decades*) later. Clear comments
should state what you are doing, define your objects, and clarify any
non-standard code you may employ. Don’t assume that you’ll know what
your code means down the line\!

## Using objects

Okay, now that `head_size` is in memory, you can do things with it\!
Let’s try some math.

``` r
# take the square of head_size
head_size ** 2
```

    ## [1] 1600

Quick question- what is the value of head size now? Why do you think
that is? Don’t read ahead\!

## Modifying objects

If you want to change an object’s value, just assign it a new one. Your
object’s value doesn’t change until a new assignment is made. R will not
hesitate to overwrite the value, giving you no warnings when you are
doing so. So, be careful and always double-check that the object doesn’t
already exist or you are sure in your intent to overwrite\!

``` r
# assign a new number
(head_size <- 45)
```

    ## [1] 45

``` r
# assign a new value with arithmetic
(head_size <- head_size * 1.25)
```

    ## [1] 56.25

**Exercise 2**

Create a new object called `weight_kg` and assign it the value **70**.
Now, convert it to pounds, using the conversion factor **2.2**. Assign
this new value to the object `weight_lb`.

-----
# What is a vector?

A vector is the most basic data structure in R and is foundational to
coding in R. A vector is a series of values that all have the same *data
type*. 

A numeric vector looks like this

``` r
my_vector <- c(1, 2, 3, 4)

#print the vector
my_vector
```

    ## [1] 1 2 3 4

A character vector looks like this

``` r
char_vector <- c("I", "love", "to", "code", "in", "R.")

char_vector
```

    ## [1] "I"    "love" "to"   "code" "in"   "R."

Vectors are one-dimensional. Adding another dimension (e.g. a 2 x 2
grid) makes it a *matrix*. Since they’re one-dimensional, you can count
the number of elements in a vector with the `length()` function.

``` r
length(char_vector)
```

    ## [1] 6
-----

## Answers

**Exercise 1**

3)  1st\_try. Names can’t start with a number

**Exercise 2**

Here is one method:

``` r
weight_kg <- 70
weight_lb <- weight_kg * 2.2
```

Here’s another:

``` r
weight_kg <- 70
weight_lb <- 70 * 2.2
```

Note that I used parentheses around the first operation. You can use
parantheses to specify the order you want operations to be performed. R
follows the order of operations, so the parentheses aren’t really
necessary here, but they can be helpful to clarify your code or prevent
mistakes.

-----

[\<\<\< Previous](01-introduction.md) | [Next \>\>\>](04-vectors.md)

-----

Material modified from [R Studio
Primers](https://rstudio.cloud/learn/primers) and [Data
Carpentry](https://datacarpentry.org/R-ecology-lesson/01-intro-to-r.html)
