Vectors and data types
================

[\<\<\< Previous](02-functions.md) | [Next \>\>\>](06-data-structure.md)

# What is a vector?

A vector is the most basic data structure in R and is foundational to
coding in R. A vector is a series of values that all have the same *data
type*. We will elaborate on data types later, but numbers and characters
are two examples.

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

**Exercise 1**

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

I keep referring to data types. What are they?

## Data types

R interprets the type of your vector based on the characteristics of its
values.

Each *data type* has its own unique properties.

Here is a list of the different data types:

  - `int` stands for integers, or whole numbers.

  - `dbl` stands for doubles, or numbers with decimals.

  - `chr` stands for character vectors, or strings.

  - `dttm` stands for date-times (a date + a time).

  - `lgl` stands for logical, vectors that contain only TRUE or FALSE.

  - `fctr` stands for factors, which R uses to represent categorical
    variables with fixed possible values.

  - `date` stands for dates.

## typeof()

`typeof()` is a handy function that returns the data type of your
vector. If you’re ever in doubt, check your vector with `typeof()`\!

``` r
dec <- c(3.24, 5.4, 2.04, 6.55)

typeof(dec)
```

    ## [1] "double"

## Getting it right

Vectors cannot contain more than one type of data. If you try, R will
coerce your vector to a single data type that you weren’t intending.

``` r
mix_vec <- c(1, "two", 3L)

mix_vec
```

    ## [1] "1"   "two" "3"

``` r
typeof(mix_vec)
```

    ## [1] "character"

**Quick exercise**

Check the type of this vector:

``` r
mix_nums <- c(1L, 2L, 2.5, 3)
```

What type does it evaluate to?

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

**Exercise 2**

You have two vectors that contain the words in a sentence.

``` r
sentence_1 <- c("I", "want", "a", "pet", "turtle")

sentence_2 <- c("It", "will", "be", "green", "and", "brown")
```

1)  Count the number of words in each sentence.

2)  Concatenate the two vectors and assign them to a new object (for
    simplicity, call it `sentences`).

3)  Now for a tricky task. Count the number of letters in the combined
    sentences. Some hints: Use the `nchar()` function to count the
    number of letters in each word. You will need to assign an
    intermediate variable.

-----

## Subsetting vectors

What do you do if you wanted to extract a specific element or elements
in a vector? Square brackets `[]` with one or more indices inside allow
you to do this.

``` r
z <- c(10, 11, 12, 13, 14, 15)

z[3] 
```

    ## [1] 12

This is telling R to look for the 3rd element in the vector z and to
return that result, which in this case is the number 12.

You can also use multiple indices to retrieve more than one element
using the `c()` function within `[]`.

``` r
z[c(1, 4, 5)]
```

    ## [1] 10 13 14

This extracts the first, fourth, and fifth elements in the `z` vector.

**Exercise 3**

Let’s take our favorite sentence (I’m reassigning it here for clarity)

``` r
sentence_1 <- c("I", "want", "a", "pet", "turtle")
```

Create a new object that contains all of the words that contain more
than one letter. Note- use numerical indexing to do this. You don’t need
to use the `nchar()` function. Just eyeball the words.

-----

We will revisit subsetting in more detail in the next section.

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

R is a vectorized language. Just like with the addition you performed
earlier, you can simply divide your body measurement vector by body size
(which happens to be a vector with a single element).

``` r
limb_meas_corrected <- limb_meas / body_size

limb_meas_corrected
```

    ##     humerus       femur tibiofibula 
    ##       0.250       0.500       0.625

**Exercise 2**

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

**Exercise 3**

``` r
big_words <- sentence_1[c(2, 4, 5)]

big_words
```

    ## [1] "want"   "pet"    "turtle"

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

[\<\<\< Previous](02-functions.md) | [Next \>\>\>](06-data-structure.md)

-----

1.  Modified template from [Nice R
    Code](https://nicercode.github.io/guides/functions/) and [Data
    Carpentry](https://datacarpentry.org/R-ecology-lesson/01-intro-to-r.html)
