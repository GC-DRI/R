Getting help
================

[\<\<\< Previous](03-functions.md) | [Next \>\>\>](05-data-structure.md)

-----

> ## Learning Objectives
> 
>   - Understand how to read packages and functions' documentation
>   - Explore where and how to ask for help

-----

## Getting help

I don’t think I have ever had a coding session where I didn’t have to
get help at least once. Effectively getting help for a problem in R is a
crucial skill. Programmers often joke that they don’t actually code,
they’re just really good at using Google. While a bit of an
exaggeration, this isn’t far off from the truth. However, before jumping
straight to Google, there are a few places within R and RStudio where
you can get help.

Adding a `?` in front of a function will open up the documentation for
that particular function. If you’re using RStudio, it’ll open in your
help tab. It can help explain what that function can do and serves as a
pretty useful help page when you are learning or troubleshooting.

``` r
# you don't need the parentheses, but ?sum() also works
?sum
```

A typical help page has these sections: **Description**, **Usage**,
**Arguments**, **Details**, **Value**, **S\* methods**, **References**,
**See Also**, and **Examples**.

The help page for `sum()` looks like this:

![](../images/help.png)

**Explore**

Explore the `sum()` help page to get an idea of what a help page looks
like. Feel free to look around at the help pages for different functions
when you’re comfortable with the **sum()** page.

Sometimes you may not know the exact name of the function you need help
with or you only know the package it came in (we’ll get to what a
package is later. For now, think of it as a folder that holds a suite of
functions). In this case, `??` is helpful. `??` executes a broader
search of R, looking for functions and packages that contain your search
terms. It will return **Vignettes**, **Code demonstrations**, and **Help
pages** that contain your search term.

Try this in your console:

``` r
??mean
```

When I run it, I get this in my help tab. Yours will likely look
different.

![](../images/help_qq.png)

These vignettes, packages, and examples all involve the keyword *mean*.
Sometimes the returned results are daunting and it could take a while to
search through them if your search term is used in a lot of functions. A
helpful aspect of RStudio is that you can search within your results
with the “Find in Topic” search bar.

![](../images/find-in-topic.png)

For instance, I’m interested in calculating the geometric mean rather
than the average, so I typed “geo” into the Find in Topic bar:

![](../images/find-in-topic-geo.png)

Depending on the function author, the help pages can either be very
informative and clear, or they can be opaque. They may have plenty of
information about one use of the function, but nothing about the use
you’re interested in. Maybe you’re trying to run your function and a
weird error message keeps popping up. Maybe you want to perform an
analysis, but don’t know which function(s) are appropriate. In this
case, Google is your friend. In most cases, especially for beginners,
your question has already been answered somewhere. The hard part is
entering the correct search terms and knowing where quality answers are.

I’ll demonstrate a typical Google search here. You’re interested in
rounding a bunch of numbers to the nearest tens place (e.g. 46 rounds to
50), but the `round()` function appears to only round to digit values.
You scanned the help page, but didn’t notice anything that solves your
problem. So, using your R googling skills, you search “round to the tens
place r”. R is sufficiently common that tacking on “r” or “r stats” to
the end of the question is enough to find an R solution for your
problem.

![](../images/google-bar.png)

This is a typical Google result for a coding problem. The first or
second result will typically be a
[stackoverflow](https://stackoverflow.com/) page. Stackoverflow is a
forum for answering technical questions. The large result is typically
what Google considers the most relevant, followed by smaller links that
seem to match your search requirement.

**Quick question**

Type the search string into your own console and click on this result.
Does this seem like a good solution to your problem? Why or why not?

**Quick answer** Unfortunately this isn’t what you’re interested in.
This user is seeking to only round up. The next google selection looks
promising\! Click on the “Rounding numbers to nearest 10 in R” link.

The questions looks like this:

![](../images/stackoverflow-question.png)

The user has a similar goal to you- they want to round to the 10s place.
Note that they provide examples of what they would like to see and have
stated what they have tried already\!

Now how to find the right answer? Fortunately, this question only has
two answers to sift through. Usually the best answer is the answer
accepted by the author (with the green checkmark), but sometimes the
author doesn’t select a top answer or the community disagrees with the
question author’s selection. It’s worth it to take a look at other
highly upvoted answers so you don’t miss anything\! In this case, we
have a straightforward decision. The top answer is this:

![](../images/stackoverflow-topanswer.png)

Well, this is embarrassing. The answer was in the help documentation\!
Don’t feel embarrassed though. Be glad the answer was simple.

Asking good questions and assessing quality answers is a skill that
takes a while to develop (at least it did for me). However, it is one of
the most important skills to develop. Check out [this
post](https://stackoverflow.com/help/how-to-ask) for a short and sweet
overview of how to ask good questions in forums like stackoverflow.
Google has another [good blog
post](https://webmasters.googleblog.com/2010/09/tips-for-getting-help-with-your-site.html)
that should get you started asking good questions\!

### More help resources

Here are some more resources to help you get help.

[How to make a reproducible example](https://www.tidyverse.org/help/)

[The RStudio community for help with RStudio products, tidyverse, and
more](https://community.rstudio.com/)

I’ll probably link to this book many times, but [R for Data
Science](https://r4ds.had.co.nz/) is a great reference.

-----

[\<\<\< Previous](03-functions.md) | [Next \>\>\>](05-data-structure.md)

-----
