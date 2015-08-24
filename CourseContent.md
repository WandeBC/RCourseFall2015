---
title: "Course Schedule / Content"
author: "Brooke Anderson"
date: "August 24, 2015"
output: html_document
---

# Broad overview

The course will cover four large themes in R programming for research:

- Entering and cleaning data
- Exploring data
- Reporting data results
- Reproducible research

The first course is preliminaries, and after that there will be three "cycles" of covering these topics:

- **Preliminaries** Week 1, August 24
- **Basic** Weeks 2--5, August 31, September 14, 21, and 28
- **Intermediate** Weeks 6--9, October 5, 12, 19, and 26
- **Advanced** Weeks 10--13, November 2, 9, 16, 30
- **Final** Week 14, December 7

# Detailed overview

Here is an overview of the content. Since this is the first time this class is being held, this is subject to changes as we get into the course and I see how the pace is working.

## Preliminaries

- Week 1 (August 24). **Preliminaries**: *Downloading R and RStudio; A tour of the
R Studio interface; Finding course materials on GitHub; The very basics of
using R-- Reading in basic datasets, most basic objects (dataframes,
vectors), using indexing to pull out parts of objects; What are packages in R? Using packages in R*

## Basic

These are skills you will use all the time and will need to know by heart to
use R productively for academic research. These are the bare minimum
you will need to know to be an R user.

- Week 2 (August 31). **Entering and cleaning data 1**: *What are flat files (.csv,
.txt, etc.)? How to enter different types of flat files using the `read.table()`
group of functions; How do get data into R from other common file
formats (Excel, SAS, SPSS, Stata, etc.); How to use basic subsetting and
indexing commands in R to pick out certain parts of the data; How to
replace parts of the data (e.g., replace "-999.9"" strings with "NA"); Basics
of merging data; Introduction to writing code in a script file, to use later,
rather than running all commands from R Studio command line; Explanation of importance of using a script file to save all code used to
clean up original data*
- Week 3 (September 14). **Exploring data 1**: *What can go wrong when reading
in data? How to use `str()`, `summary()`, `head()`, `tail()`, and `dim()` to do basic
checks on data; Using R's base plot functions to plot data; Using basic
plots to looks for outliers, patterns in missing data, etc.; How to write your
data out to other files for others to use; Role of README files in explaining
data files to other users; The basics of using R for statistical tests and
fitting basic GLMs (e.g., `t.test()`, `lm()`, `glm()`, `anova()`); How to use help
functions, Google, and StackOverflow to get help with R; R cheat
sheets*
- Week 4 (September 21). **Reporting data results 1**: *Basic plotting
functions; Principles of R's default plotting; Difference between default
plotting and plotting using ggplot2; Basics of using ggplot2 to create
publication-quality plots in R; How to save plots as pdf or graphics files;
Basic principles of creating effective graphs (e.g., Tufte, Howard Wainer)*
- Week 5 (September 28). **Reproducible research 1**: *What is a mark-up
language? Writing a basic document in Markdown and compiling it to
HTML code; What is the `knitr` package and how does it work? Writing a
basic RMarkdown document that includes R code; Finding and using the
RMarkdown cheat sheet; A very basic introduction to what Tex and LaTex
are and how they work into reproducible research in R; Why is it important
to make your research reproducible?*

## Intermediate

These are skills you will use regularly as you become a better R
programmer. These skills will really increase your ability to do efficient,
reproducible, and publication-ready academic research.

- Week 6 (October 5). **Entering and cleaning data 2**: *Using Hadley Wickham's
tools to clean up data; What is piping / chaining? How to use the pipe function; Using
tools from the `dplyr` package to clean up and merge data; What does it
mean to reshape data and when would you need to do that? Using tools
from the `tidyr` package to reshape data; Listing files within a directory;
What is a loop? Using a loop to read, clean, and re-save all files in a
directory*
- Week 7 (October 12). **Exploring data 2**: *More about fitting GLMs to data in R;
Using `dplyr` functions to summarize data by groups to explore patterns;
Dates and times in R; What are functions? Writing functions for tasks you
do often.*
- Week 8 (October 19). **Reporting data results 2**: *More on the principles of
creating effective graphs (e.g., Tufte, Wainer); Basics of creating effective
tables (e.g., Wainer); Intermediate / advanced ggplot to create fancier
plots in R, including changing themes, using faceting, adding regression
lines and smooth lines; Adding text to graphs; How to use Google Images
and RPubs to get new ideas for ways to present data and R code to start
from*
- Week 9 (October 26). **Reproducible research 2**: *Using `kable` to write out
tables in RMarkdown documents; Introduction to BibTex for including
citations in reproducible documents; Creating a presentation using
RMarkdown; An introduction to using RPubs to publish RMarkdown
documents; Hadley Wickham's style guides for R and why style in code is
important*

## Advanced

These are skills that are great for you to know about, although you may
not use them all the time (or may not use them in your research yet).
Hopefully, as you continue to use R in your academic research, you will
have times when you'll want to do some of these things, and they are very
powerful ways to use R, which will really set you apart from many other
students outside of computer science.

- Week 10 (November 2). **Entering and cleaning data 3**: *How is data
published online? A few of the ways to pull data directly from the web
(e.g., reading csv files directly, using the download.file() function, etc.); A
very basic introduction to some of the more complex on-line formats (XML,
JSON); What is an API? Examples of how people have used APIs to pull in
information from Google Maps and Twitter; Using the `substr()` function; What
are regular expressions? Using regular expressions as a powerful way to
clean up and explore data; Introduction to using `readLines()` to read in
very messy data*
- Week 11 (November 9). **Exploring data 3**: *More on creating your own
functions to work with your data; The very basics of using R to explore
interesting questions using simulations; Basics of geographic data in R;
Overview of how R is being used in research in a variety of areas--
Statistical Genetics, Environmental Epidemiology, Econometrics, Ecology,
Phylogenetics, Machine Learning--and what resources exist to learn more
about how to use R for a research area you're interested in*
- Week 12 (November 16). **Reporting data results 3**: *An overview of grid
graphics and how it can be used to make customized graphics; Where to
find out more about how to use grid graphics; How to use R to create
interactive data displays: `Shiny`, `htmlWidgets`*
- Week 13 (November 30). **Reproducible research 3**: *An in-depth look at what
R packages are and how they work; Why would you want to create an R
package? The basics of how to create R packages; How can you publish a
package for others to use? An introduction to package vignettes and the
Journal of Statistical Software; An introduction to tools for reproducible
research in other languages (e.g., SAS)*

## Final week

- Week 14 (December 7). **Wrapping up**: Group project reports; Students' choice of
lecture

# Important dates

**Quizzes**. You will have in-class quizzes on the following dates:

- August 31
- September 14
- September 21
- September 28
- October 5
- October 12
- October 19
- October 26

**Journal entries**

You will have journal entries due by email by noon the Friday following every class meeting:

- August 28
- September 4
- September 18
- September 25
- October 2
- October 9
- October 16
- October 23
- October 30
- November 6
- November 13
- November 20
- December 4
- December 11 (final group project)

**Group project**. 

- You will present your final group project during our last day of class, **December 7**. 
- The final write-up of your group project will be due to me by email by 12:00 pm (noon) the following Friday, **December 11** (only one email per group).

