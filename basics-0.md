---
layout: default
title: 3-Data Types, Basic Commands and Charting
nav_order: 4
parent: Workshop Activities
customjs: http://code.jquery.com/jquery-1.4.2.min.js
---

3-Data Types, Basic Commands and Charting
================

- [1. Creating and Manipulating Vectors and Basic
  Variables](#1-creating-and-manipulating-vectors-and-basic-variables)
  - [1.1 Variables and Basic Data
    Types](#11-variables-and-basic-data-types)
  - [1.2 Vectors](#12-vectors)
- [2. Descriptive Statistics](#2-descriptive-statistics)
  - [2.1 Basic statistical measures](#21-basic-statistical-measures)
  - [2.2. Histogram Plot for Pig
    Weights](#22-histogram-plot-for-pig-weights)

<img src="images/rstudio-22.png" alt="rstudio logo" style="float:right;width:220px;"/>
<br>

## 1. Creating and Manipulating Vectors and Basic Objects

The key to understanding R is that you will be working with what we 
call "objects". Anything in R can be an object: a number, a string of 
characters, a data frame with data, and even plots. 

To create any object:

- The command will begin with the name for the new object
- followed by: - an assignment operator `<-`
- and then the data or expression that defines the content of the
  object.

-This can include direct values, function calls, operations, or other
objects.

``` r
objectName <- "word"
```

**Attention:** Object names are never wrapped in quotes. String/character 
values being assigned to an object must be wrapped in quotes. Object 
names cannot begin with anything other than an alphabetical character, 
but otherwise can contain special characters and numbers (\*\_13). Object
names cannot contain spaces, but string values can. 
<br> 
**Definition - “Function”:** A set of instructions defined to perform a specific task.

-E.g., help() : ‘help’ is a function to get information

**Definition - “Function Call”:** The act of executing a function with
specific arguments, if required, to produce a result. <br>

- e.g., help(“integer”)
- This calls the ‘help’ function with the argument (aka parameter)
  “integer”
- It will return information about an ‘integer’ object type.

<br>

### 1.1 Basic Data Types

Let’s start by looking at types of data.

<br>

**Definition - “Basic Data Types”:** Types of data representing the
simplest forms of data.

**Basic Data Types**:

- *Numeric*: Decimal or floating-point numbers (e.g., 4.5, -3.2).

- *Integer*: Whole numbers (e.g., 1, -5, 20).In R, integers are often
   just treated as numeric unless explicitly specified.

- *Logical*: Boolean values, either TRUE or FALSE.
  
- *Character*: Text or strings (e.g., “hello”, “1234”).

- *Factor*: A special type of character data, includes levels
  or an order (e.g., “low”, “medium”,  “high”).

<br> Here we’ll look at basic operations with objects with character data.

Note: whenever you enter a string parameter, the string will more likely
than not be wrapped in quotes. If it doesn’t work, add or remove quotes.

<div class="task-box" markdown="1">

⭐ <u>Task 1.1-1</u>

**Create an object.**

Create an object for a pig’s first name. The first pig's first name is "Bart".

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# Assign the first name 'Bart' to the first pig (pig1)
pig1.first_name <- "Bart"
```
**Note:** You might have created an object with a different name, which is 
completely okay (as long as it is an understandable name; remember the best
practices for naming objects from the previous section). However, we will 
continue using the object `pig1.first_name` for this activity, so you might 
want to use the same name to make it easier to follow.
</details>

{::options parse_block_html='false'/}

</div>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.1-2</u>

**Create an object.**

Create an object for Bart’s last name. Bart's last name is "Smith".

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# Assign the last name 'Smith' to the first pig (pig1)
pig1.last_name <- "Smith"
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.1-3</u>

**Create an object.**

Create an object that equals Bart’s first and last name, then display
the full name in the console <br>

The `paste()` function combines two strings and inserts a space between
them. `paste()` takes two arguments, like `paste(string1, string2)`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# Concatenate the first pig's (pig1) first ('Bart') and last name ('Smith')
pig1.full_name <- paste(pig1.first_name, pig1.last_name)

# After pig1.full_name has been created, print (display) Bart’s full name...
pig1.full_name
```

    ## [1] "Bart Smith"

</details>

{::options parse_block_html='false'/}

</div>

<br>

Now we’ll look at basic operations with **numeric and integer
variables**. First, we’ll create height information for Bart and find out
how much he’s grown in height.

<br>

<img src="images/rstudio-basics-Bart.png" alt="Bart as a piglet and adult" style="width:420px;"/>

<div class="task-box" markdown="1">

⭐ <u>Task 1.1-4</u>

**Create an object.**

Create an object for Bart’s height as a piglet: 10

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# Assign the value of Bart’s piglet height
pig1.heightA <- 10
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.1-5</u>

**Create an object.**

Create an object for Bart’s height now: 22.3

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# Assign the value of Bart's current height
pig1.heightB <- 22.3
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.1-6</u>

**Create an object.**

Now create an object expressing the amount he’s grown.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# Find the difference in height using the expression: 'heightB - heightA' 
# using the subtraction operator. 
pig1.heightGain <- pig1.heightB - pig1.heightA

# after pig1.heightGain has been created, print (display) the value of pig.heightGain...

pig1.heightGain
```

    ## [1] 12.3

</details>

{::options parse_block_html='false'/}

*Hint:* “Expressing” indicates that the value will require an
expression, in this case, a mathematical operation.

</div>

<br>

`pig1.heightA` is an ‘integer’ data type (whole number)

`pig1.heightB` is a ‘numeric’ data type (decimal number)

R can perform operations on different data types, like getting the
difference of a value.

------------------------------------------------------------------------

📍 As you work through these activities, remember to save your script(s)
regularly.

------------------------------------------------------------------------

To remove objects from your environment, execute the ‘remove’
function in the console: `rm()`, e.g. `rm(full_name)`.

<br>

**Time for logical or boolean values!**

We can denote whether Bart is small or large with a Boolean value.

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.1-7</u>

**Create two objects.**

Create two objects (pig1.mini and pig1.large) containing Boolean values
which indicate that Bart is a large pig and not a mini pig.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
pig1.mini <- FALSE

pig1.large <- TRUE
```

</details>

{::options parse_block_html='false'/}

*Hint:* Boolean values are either ‘TRUE’ or ‘FALSE’ (case sensitive).

</div>

<br>

### 1.2 Vectors

A vector is a 1-dimensional list of items that are of the same data type
(all character, all numeric, etc.)

To create a vector object, you will use the `c()` function. <br>

- The ‘c’ stands for ‘combine’.

- It’s used to create a vector by grouping individual values into a
  list-like structure.

- Think of it as placing items into a container where each item remains
  distinct and can be individually accessed.

  - For example, `vector1 <- c(value1, value2)` creates a vector named
    ‘vector1’ containing the elements ‘value1’ and ‘value2’ as separate
    items in a sequence, not as a single merged item.

  - A value in a vector can be accessed by using square brackets and its
    index (the value’s place in the vector), where **1** is the first
    index.

    - `vector1[1]` will output: ‘value1’

<br>

As you might have seen if you tested the help() function by looking up
information on vectors, you will know that <!--check its output--> many
functions and operations in R are designed to work naturally with
vectors.

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.2-1</u>

**Create a vector.**

Make a vector for the following weight values of miniature goats. Name
your variable ‘goat.weights’

`Goat weights: 13.3, 17.2, 14.8, 14.6, 12.4`

<br>

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# The period between 'goat' and 'weight' has no special purpose. 
# It only shows the person reading the code that 'weights' is information that pertains to the goats
goat.weights <- c(13.3, 17.2, 14.8, 14.6, 12.4)
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

The command you just ran has now appeared in your console (bottom left
window)

- the goat.weight vector is now listed in the Environment tab (top right
  window) under <u>Values</u>.<br>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.2-2</u>

**View objects.**

Show the contents of the vector containing the goat weights.

If at any point you want to view the value of an object, you can
just type the name of the object in the console and type ‘enter’ 
or ‘return’ to execute. 

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
goat.weights
```

    ## [1] 13.3 17.2 14.8 14.6 12.4

</details>

{::options parse_block_html='false'/}

</div>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.2-3</u>

**View objects.**

Display the weight of the second goat in the vector.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
goat.weights[2]
```

    ## [1] 17.2

</details>

{::options parse_block_html='false'/}

*Hint:* `data_object_name[indexNumber]`

</div>

<br>

You have just worked with numeric vectors. Now let’s move to character
vectors.

<img src="images/rstudio-basics-goats.png" alt="a row of goats" style="width:420px;"/>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.2-4</u>

**Create a new vector.**

Make a vector for the following name values of miniature goats.

Name your variable `goat.name`

Goat names: baby, pickles, cookie, sparkle, gabbie

**Note:** Text values must be wrapped in quotations. You can use double
or single quotes, but must be consistent - Good: `"text"` - Good:
`'text'` - Bad: `'text"`

<br>

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
goat.name <- c("baby", "pickes", "cookie", "sparkle", "gabbie")
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

To get the length of a vector, we can use the <code>length()</code>
function.

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1.2-5</u>

**View information about vectors.**

Display the length of the vector of miniature goat names.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
length(goat.name)
```

    ## [1] 5

</details>

{::options parse_block_html='false'/}

</div>

<br>

#### Lists (Additional Information)

A ‘list’ can hold items of different types (even vectors), while items
in a ‘vector’ must all be the same type. <br>

To make a list, we’ll use the `list()` function.

**Hint:** Remember that all items in a vector must be the same type, but
can be different types if in a list.

If you want to create 2D lists, also known as a table, you will create a 
data.frame suing the `data.frame()` function or a matrix using the 
`matrix()` function. 
<br> - Instead of creating our own data.frames, we will be importing data
- For more on matrices,
[check me
out](https://www.w3schools.com/r/r_matrices.asp){:target=“\_blank”}.
<br>
later on.

------------------------------------------------------------------------

📍 As you work through these activities, remember to save your script(s)
regularly.

------------------------------------------------------------------------

<br>

## 2. Descriptive Statistics

Statistics is:

- the science of collecting, analyzing, and interpreting

- data to uncover patterns and trends,

- and inform decisions based on this data.

If you’re unfamiliar with statistics, you can learn more about it from
the [w3school Statistics
Tutorial](https://www.w3schools.com/statistics/index.php){:target=“\_blank”}

In this section, we’ll be focusing on

- Basic statistical measures
- Presenting data in a histogram
- More on presenting data will be covered in [Activity 4-Data
  Visualization](https://uviclibraries.github.io/rstudio/ggplot2-data.html){:target=“\_blank”}
- Importing data

### 2.1 Basic statistical measures

The function names for the following three statistical measures (mean,
median, standard deviation) are quite intuitive.

It is just the name or abbreviation of the statistical measure, where
the argument is the object containing the set of values we are
analyzing.

Each function takes the vector containing the values of the variable as 
its argument.

These three functions are designed for sets of numerical and integer
data types. If run on other types (character, aka text, and boolean, aka
true/false), result will be `NA`.

<div class="task-box" markdown="1">

⭐ <u>Task 2.1-1</u>

**Create a variable to be summarised.**

For this task, we will use a new vector object containing weights for a
set of pigs.

Create a vector object with the weights of a set of pigs. Name your
variable ‘pigs.weight’

`Weights of pigs: 22, 27, 19, 25, 12, 22, 18`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
pigs.weight <- c(22, 27, 19, 25, 12, 22, 18)
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 2.1-2</u>

**Get the mean (average) value.**

**Mean:** the average value in a set.

The `mean()` function calculates the sum of the values in the set and 
divides the sum by the number of items in the set.

Write and execute a command that outputs the mean value of the pigs’
weights.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# output the average weight of all of the pigs
mean(pigs.weight)
```

    ## [1] 20.71429

</details>

{::options parse_block_html='false'/}

</div>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 2.1-3</u>

**Get median value.**

Write and execute a command that outputs the median value of the pigs’
weights

**Median:** The middle value in a sorted set (e.g. lowest - highest).
`median()`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
median(pigs.weight)
```

    ## [1] 22

</details>

{::options parse_block_html='false'/}

</div>

<br> The output tells you the weight of the pig that falls between the
lighter half and the heavier half of the pigs. <br>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 2.1-4</u>

**Get standard deviation.**

**Standard deviation:** Describes how spread out the data is. 

The function in R is `sd()`

Write and execute a command that outputs the standard deviation of the
pigs’ weights

The output tells you how much the weights of the pigs vary from the
average weight.

- A small standard deviation means that most pigs’ weights are close to
  the average, indicating uniformity in size.
- A large standard deviation suggests a wide range of weights. <br>

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
sd(pigs.weight)
```

    ## [1] 4.956958

</details>

{::options parse_block_html='false'/}

</div>

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 2.1-5</u>

**Get summary of value statistics.**

Display a summary of values pertaining to the pigs’ weights

We can execute a **‘summary’** to generate several descriptive
statistics at the same time. `summary()`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
summary(pigs.weight)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   12.00   18.50   22.00   20.71   23.50   27.00

</details>

{::options parse_block_html='false'/}

</div>

<br>

### 2.2. Histogram Plot for Pig Weights

**Histogram:** A graph used for understanding and analysing the
distribution of values in a vector.

A histogram illustrates:

- Where data points tend to cluster
- The variability of data
- The shape of variability

The histogram will appear in the Plots tab (bottom right quadrant if you
haven’t modified your RStudio layout).

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 2.2-1</u>

**Create a histogram.**

Create a histogram for the pigs’ weights using the histogram function
`hist()`

- Parameter: vector of pig weights

{::options parse_block_html='true' /}
<details>
<summary>
Check your code and see the histogram
</summary>

``` r
hist(pigs.weight)
```

![](basics-0_files/figure-gfm/unnamed-chunk-53-1.png)<!-- -->

``` r
# The histogram will appear in the Plot tab.
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

We can also pass in additional parameters to control the way our plot
looks.

Some of the frequently used parameters are:

- `main` : The title of the plot
  - e.g., `main = "This is the Plot Title"` <br>
- `xlab` : The x-axis label
  - e.g., `xlab = "The X Label"` <br>
- `ylab` : The y-axis label
  - e.g., ylab = “The Y Label”

Multiple parameters are given to a function by putting them in
parentheses separated by commas, `function_name(parameter1, parameter2)`

- E.g.,
  `hist(dataset, xlab="x-label", ylab = "y-label", main = "main title")`

<div class="task-box" markdown="1">

⭐ <u>Task 2.2-2</u>

**Create a histogram.**

Create a histogram for the pigs’ weights, with axes labels.

In your histogram for the pigs’ weights, use:

- X-label: “Weight”
- Y-label: “Frequency”
  - This is a default value.
  - You don’t have to specify it unless you would like a different
    label.
- Graph title: “Histogram of Pigs’ Weights”

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# The first parameter is the name of the data (vector) object
# 'main' is the graph title 
# 'xlab' is the label of the x-axis
# label parameters can be in any order, but following the data object
# y-label on a histogram defaults to "frequency". You can add 'ylab=""' if you'd like.

hist(pigs.weight,main='Histogram of Pig Weight',xlab='Weight')
```

![](basics-0_files/figure-gfm/unnamed-chunk-56-1.png)<!-- -->

``` r
# The histogram will appear in the Plot tab.
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

------------------------------------------------------------------------

📍 As you work through these activities, remember to save your script(s)
regularly.

- File
- Save (or cmd+s on Mac, ctrl+s on Windows)

------------------------------------------------------------------------

<br>

<script>  
function toggle(input) {
    var x = document.getElementById(input);
    if (x.style.display === "none") {
        x.style.display = "block";
    } else {
        x.style.display = "none";
    }
}
</script>
<style>
details {
    background-color: lightgray; 
    padding: 10px;
    margin: 5px;
    border-radius: 5px;
}
.task-box {
      border: 1.5px solid #ccc;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      background-color: #f5f2f6;
  }
  &#10;</style>
<!--https://gist.github.com/rxaviers/7360908-->

[NEXT STEP: Importing Data](basics-importing-data.html){: .btn .btn-blue
}
