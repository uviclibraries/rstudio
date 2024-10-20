---
layout: default
title: 2-Data Types, Basic Commands and Charting
nav_order: 3
parent: Workshop Activities
customjs: http://code.jquery.com/jquery-1.4.2.min.js
---

2-Data Types, Basic Commands and Charting
================

- [1. Getting familiar with the RStudio
  Interface](#1-getting-familiar-with-the-rstudio-interface)
  - [Working in the Code Editor](#working-in-the-code-editor)
  - [Working in the Console](#working-in-the-console)
- [2. Creating and Manipulating Vectors and Basic
  Variables](#2-creating-and-manipulating-vectors-and-basic-variables)
  - [2.1 Variables and Basic Data
    Types](#21-variables-and-basic-data-types)
  - [2.2 Vectors](#22-vectors)
- [3. Descriptive Statistics](#3-descriptive-statistics)
  - [3.1 Basic statistical measures](#31-basic-statistical-measures)
  - [3.2. Histogram Plot for Pig
    Weights](#32-histogram-plot-for-pig-weights)
- [4. Importing Data](#4-importing-data)
  - [4.1 Importing Excel data into R](#41-importing-excel-data-into-r)
  - [4.2 Visualize Income with a Histogram
    plot](#42-visualize-income-with-a-histogram-plot)

<img src="images/rstudio-22.png" alt="rstudio logo" style="float:right;width:220px;"/>
<br>

## 1. Getting familiar with the RStudio Interface

![Code Editor, R console, Workplace and Plots](images/rstudio-01.png)
<br> The RStudio interface is divided into several key areas, each
serving a specific purpose. - One of the great features of RStudio is
that you can customize the layout by reorganizing these windows to suit
your workflow.

> Hint: You can rearrange these windows and tabs to fit your personal
> preference by dragging them around the
> workspace.<!--chloe make a video on rearranging windows and resetting-->
> When you rearrange the panes in RStudio on your computer, the layout
> stays as you set it across future sessions.

*Main components of the RStudio interface:*

1.  *Code Editor:* This is where you write and edit your R scripts.

    - It features syntax highlighting, code completion, and other
      helpful tools to make coding easier.

2.  *Console:* The console is where R code is executed.

    - You can type commands directly into the console, and it displays
      outputs, messages, and errors.

    - You might prefer to use the console for immediate execution, or
      testing of small code snippets or commands.

3.  *Files/Plots/Packages/Help Pane:*

- *Files:* Browse, open, and manage files in your working directory.

- *Plots:* View graphical outputs from your R code, such as plots and
  graphs.

- *Packages:* Install, update, and load R packages.

- *Help:* Access R documentation and help files for:

  - functions and packages
  - example code
  - information about datasets built in to R
  - information about other general R-related topics.

- *Viewer:* Used to view local web content.

  - We won’t be covering this
  - E.g., web graphics generated using packages like
  - googleVis,
  - htmlwidgets
  - rCharts
  - local web application created using Shiny, Rook, or OpenCPU.
  - See more at the RStudio [Viewer
    Page](https://rstudio.github.io/rstudio-extensions/rstudio_viewer.html){:target=“\_blank”}

- *Presentation:* You can use RStudio to create presentations. The
  presentations can be viewed in this tab.

> We won’t be covering this<br> See more at the RStudio [Viewer
> Page](https://rstudio.github.io/rstudio-extensions/rstudio_viewer.html){:target=“\_blank”}<br>
> To learn how, click
> [here](https://fish497.github.io/website/lectures/week_09/lec_27_presentations.html){:target=“\_blank”}

<https://rmarkdown.rstudio.com/lesson-11.html>

4.  *Environment/History Pane:*

- *Environment:* Shows your current workspace, including:

  - defined variables
  - data frames
  - function objects.

- *History:* Records all the commands you’ve run in the current and
  previous sessions.

- *Connections:* Used to manage and configure the integration of data
  sources with your projects.

- E.g., Oracle, SQL, Salesforce

- *Tutorial:* Used to run tutorials that will help you learn and master
  the R programming language.

  - See more at the RStudio [Tutorial
    Page](https://rstudio.github.io/rstudio-extensions/rstudio-tutorials.html){:target=“\_blank”}

<br>

#### <u>Task 1.0:</u> Create new Project

In the top left corner of your screen, click the File dropdown menu, then "New Project"

Select "New Directory" > "New Project"

In the "Directory Name" field, enter "DSC_RIntro"

Click "Browse" to choose where to store this project on your computer. 

You do not need to save this periodically.

#### <u>Task 1.1:</u> Open RStudio and get familiar with the interface

by identifying the 4 windows and switching between the tabs.

> Note: This task is just for you to get comfortable. There is no
> solution for this task.

### Working in the Code Editor

Use the code editor if you want to develop more complex, reusable, and
maintainable code that can be saved in a script and executed later.

- We won’t be working in the code editor at this level.

- It will be introduced at the beginning of the Intermediate level
  workshop. <br>

### Working in the Console

Each new line of code (aka. command line) begins with the angle bracket
`>` also known as the ‘prompt’ symbol. <br>

You will type the commands into the Console after the most recent angle
bracket `>`.

*command line:* lines of code in your console.

*‘prompt’ symbol* `>` : Each new command starts with this.

*execute:* run your command by pressing the ‘enter’ or ‘return’ key on
your keyboard.

- When you are ready to execute (‘run’) the command, type ‘enter’ or
  ‘return’ key on your keyboard.
- The output to the command will appear below your command.

*Things to be mindful of:*

- You cannot execute a command until the previous command has been
  completely executed.

- If you don’t see the prompt symbol, one of two things is happening:

- R is still processing your previous command, and you must wait for it
  to finish.

- You might instead see the plus `+` symbol, which indicates that you
  have entered an incomplete command.

- If you see the `+` symbol, you must enter the remainder of the command
  before entering a new one.

- An error will occur if you write the `+` symbol into your command.

- Sometimes the output can be extensive and show more information than
  you expected

- E.g., when you load in a package (we will discuss packages more in
  Activity 3). <br>

For all tasks in this workshop, enter your commands in the Console
(bottom left) (top tabs say ‘console’, ‘terminal’, and ‘background
jobs’).<br>

<br>

#### <u>Task 1.2:</u> Try getting help!

To do this, you’ll run the `help()` function. - Try getting information
on vectors.

<br>

{::options parse_block_html='true' /}
<details>
<summary>
Check Your Code for custom number of intervals
</summary>

``` r
#Get additional information about "vectors" (a data type), 
help("vector") # then type 'enter' or 'return'
```

</details>

{::options parse_block_html='false'/}

<br> `help("vector")` will provide you with information about the mean
function in RStudio. - The help information will be displayed in the
Console following your command.

<br>

<div id="gif1">

<img src="images/rstudio-02.gif"/> <br>

</div>

</details>

<br>

> Note: You can get help on related content by selecting the dropdown
> list at the top of the Help tab. <!--screenshot-->

<br>

------------------------------------------------------------------------

As you work through these activities, make sure to Save if you use are working in an R script 
- Save your workspace by clicking on the top menu bar:

- File
- Save

------------------------------------------------------------------------

<br> <br>

## 2. Creating and Manipulating Vectors and Basic Variables

Remember: Write all of your code in the **Console** tab.

<!--add infographic about the trajectory of this section (broad to narrow)-->

> Note: For the purposes of this workshop, ‘variable’ and ‘data object’
> are used interchangeably.

To create any data object:

- the command will begin with the a name for the new variable
- followed by: - an assignment operator `<-`
- and then the data or expression that defines the content of the
  variable.

-This can include direct values, function calls, operations, or other
variables. <br>

    variableName <- "word"

<br> Variable names are never wrapped in quotes. String/character values
being assigned to variable must be wrapped in quotes. Variable names
cannot begin with anything other than an alphabetical character, but
otherwise can contain special characters and numbers (\*\_13). Variable
names cannot contain spaces, but string values can. <br> **Definition -
“Function”:** A set of instructions defined to perform a specific task.

-E.g., help() : ‘help’ is a function to get information

**Definition - “Function Call”:** The act of executing a function with
specific arguments, if required, to produce a result. <br>

- e.g., help(“integer”)
- This calls the ‘help’ function with the argument (aka parameter)
  “integer”
- It will return information about an ‘integer’ object type.

<br>

### 2.1 Variables and Basic Data Types

Let’s start by looking at types of variables.

<br>

**Definition - “Basic Data Types”:** Types of data representing the
simplest forms of data.

**Basic Data Types**:

- *Numeric*: Decimal or floating-point numbers (e.g., 4.5, -3.2).

- *Integer*: Whole numbers (e.g., 1, -5, 20).

- In R, integers are often just treated as numeric unless
      explicitly specified.

- *Character*: Text or strings (e.g., “hello”, “1234”).

- *Logical*: Boolean values, either TRUE or FALSE.

- *Factor*: Categorical data, or data as levels (e.g., “low”, “medium”,
  “high”).

<br> Here we’ll look at basic operations with character variables.

<br>

Whenever you enter a string parameter, the string will more likely than
not be wrapped in quotes. If it doesn’t work, add or remove quotes.

#### <u>Task 2.1.1:</u> Create a variable for a pig’s first name. `The first pig's first name is 'Bart'.`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#assign the first name 'Bart' to the first pig (pig1)
pig1.first_name <- "Bart"
```

</details>

{::options parse_block_html='false'/} <br>

#### <u>Task 2.1.2:</u> Create a variable for a Bart’s last name. `Bart's last name is 'Smith'.`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#assign the last name 'Smith' to the first pig (pig1)
pig1.last_name <- "Smith"
```

</details>

{::options parse_block_html='false'/}

<br>

#### <u>Task 2.1.3:</u>

Create a variable that equals Bart’s first and last name, then display
the full name in the console <br>

The `paste()` function combines two strings and inserts a space between
them. `paste()` takes two arguments, like `paste(string1, string2)`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#concatenate the first pig's (pig1) first ('Bart') and last name ('Smith')
pig1.full_name <- paste(pig1.first_name, pig1.last_name)

#after pig1.full_name has been created, print (display) Bart's full name...
pig1.full_name
```

    ## [1] "Bart Smith"

</details>

{::options parse_block_html='false'/} <br>

Now we’ll look at basic operations with **numeric and integer
variables**. First we’ll create height information for Bart and find out
how much he’s grown in height.

<br>

<img src="images/rstudio-basics-Bart.png" alt="Bart as a piglet and adult" style="width:420px;"/>

#### <u>Task 2.1.4:</u> Create a variable for Bart’s height as a piglet: 10

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#Assign the value of Bart's piglet height
pig1.heightA <- 10
```

</details>

{::options parse_block_html='false'/}

<br>

#### <u>Task 2.1.5:</u> Create a variable for Bart’s height now: 22.3

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#Assign the value of Bart's current height
pig1.heightB <- 22.3
```

</details>

{::options parse_block_html='false'/}

<br>

#### <u>Task 2.1.6:</u>

Now create a variable expressing the amount he’s grown.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# Find the difference in height using the expression: 'heightB - heightA' 
# using the subtraction operator. 
pig1.heightGain <- pig1.heightB - pig1.heightA

#after pig1.heightGain has been created, print (display) the value of pig.heightGain...

pig1.heightGain
```

    ## [1] 12.3

</details>

{::options parse_block_html='false'/}

*Hint:* “Expressing” indicates that the value will require an
expression, in this case, a mathematical operation.

<br>

`pig1.heightA` is an ‘integer’ data type (whole number)

`pig1.heightB` is a ‘numeric’ data type (decmial number)

R can perform operations on different data types like getting the
difference of a value.

------------------------------------------------------------------------

Reminder! Save your work

------------------------------------------------------------------------

> Additional: To remove data objects from your environment, execute the
> ‘remove’ function in the console: `rm()`.<br> e.g., `rm(full_name)`

<br> **Time for logical or boolean values!**

We can denote if Bart is small or large with a boolean value.

<br>

#### <u>Task 2.1.7:</u> Create two variables (pig1.mini and pig1.large) which indicate that Bart is a large pig and not a mini pig.

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

<br>

### 2.2 Vectors

A vector is a 1-dimensional list of items that are of the same data type
(all text, all whole numbers, etc.)

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

#### <u>Task 2.2.1:</u> Make a vector for the following weight values of miniature goats. Name your variable ‘goat.weights’

`Goat weights: 13.3, 17.2, 14.8, 14.6, 12.4`

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

<br>

The command you just ran has now appeared in your console (bottom left
window)

- the goat.weight vector is now listed in the Environment tab (top right
  window) under <u>Values</u>.<br>

<br>

#### <u>Task 2.2.2:</u> Show the contents of the vector containing the goat weights.

If at any point you want to view the value of a variable, use the
`print()` function with the name of the variable name and type ‘enter’
or ‘return’ to execute.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
print(goat.weights)
```

    ## [1] 13.3 17.2 14.8 14.6 12.4

</details>

{::options parse_block_html='false'/}

<br>

#### <u>Task 2.2.3:</u> Display the weight of the second goat in the vector.

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

<br>

You have just worked with numeric vectors. Now let’s move to string
vectors.

<img src="images/rstudio-basics-goats.png" alt="a row of goats" style="width:420px;"/>

<br>

#### <u>Task 2.2.4:</u> Make a vector for the following

name values of miniature goats. Name your variable ‘goat.name’

`Goat names: baby, pickles, cookie, sparkle, gabbie`

> Note: Text values must be wrapped in quotations. You can use double or
> single quotes, but must be consistent - Good: “text” - Good: ‘text’ -
> Bad: ’text”

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

<br>

To get the length of a vector, we can use the <code>length()</code>
function.

<br>

#### <u>Task 2.2.5:</u> Print (display) the length of the vector of miniature goat names.

Note: In a script (code editor), you often need to use the print()
function explicitly to see the output, especially when running multiple
lines of code or within functions. However, in the console, R
automatically displays the output of expressions upon execution of the
command.

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

<br>

#### (Additional Information) Lists

A ‘list’ can hold items of different types (even vectors), while items
in a ‘vector’ must all be the same type. <br>

To make a list, we’ll use the `list()` function.

> Hint: Remember that all items in a vector must be the same type, but
> can be different types if in a list.

> Additional: If you want to create 2D lists, also known as a table, you
> will create a matrix using the `matrix()` function. <br> - For more on
> matrices, [check me
> out](https://www.w3schools.com/r/r_matrices.asp){:target=“\_blank”}.
> <br>- Instead of creating our own matrices, we will be importing data
> later on.

------------------------------------------------------------------------

Reminder! Save your work

------------------------------------------------------------------------

<br>

## 3. Descriptive Statistics

Statistics is:

- the science of collecting, analyzing, interpreting

- presenting data to uncover patterns and trends

- making informed decisions based on this data.

If you’re unfamiliar with statistics, you can learn more about it from
the [w3school Statistics
Tutorial](https://www.w3schools.com/statistics/index.php){:target=“\_blank”}

In this section, we’ll be focusing on

- Basic statistical measures
- Presenting data in a histogram
- More on presenting data will be covered in [Activity 4-Data
  Visualization](https://uviclibraries.github.io/rstudio/ggplot2-data.html){:target=“\_blank”}
- Importing data

### 3.1 Basic statistical measures

The function names for the following three statistical measures (mean,
median, standard deviation) are quite intuitive.

- It is just the name or abbreviation of the measure,

- where the argument is the object containing the set of values we are
  analyzing.

- Each function takes the vector as its argument.

These three functions are designed for sets of numerical and decimal
values. If run on other types (string, aka text, and boolean, aka
true/false), result will be `NA`.

#### <u>Task 3.1.1:</u>

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

<br>

#### <u>Task 3.1.2:</u>

**Mean:** the average value in a set.

The `mean()` function calculates the sum of the in the set and divides
the sum by the number of items in the set.

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

<br>

#### <u>Task 3.1.3:</u>

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

<br> The output tells you the weight of the pig that falls between the
lighter half and the heavier half of the pigs. <br>

<br>

#### <u>Task 3.1.4:</u>

**Standard deviation:** Describes how spread out the data is. `sd()`

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

<br>

#### <u>Task 3.1.5:</u>

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

<br>

### 3.2. Histogram Plot for Pig Weights

**Histogram:** A graph used for understanding and analysing the
distribution of values in a vector.

A histogram illustrates:

- Where data points tend to cluster
- The variability of data
- The shape of variability

<br>

#### <u>Task 3.2.1:</u>

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

![](basics-0_files/figure-gfm/unnamed-chunk-56-1.png)<!-- -->

``` r
# The histogram will appear in the Plot tab.
```

</details>

{::options parse_block_html='false'/}

<br>

<u>Task 3.2.2:</u> Create a histogram for the pigs’ weights, with axes
labels.

We can also pass in additional parameters to control the way our plot
looks.

Some of the frequently used parameters are:

- `main` : The title of the plot
  - e.g., `main = "This is the Plot Title"` <br>
- `xlab` : The x-axis label
  - e.g., `xlab = "The X Label"` <br>
- `ylab` : The y-axis label
  - e.g., ylab = “The Y Label”

<br>

In your histogram for the pigs’ weights, use:

- X-label: “Weight”
- Y-label: “Frequency”
  - This is a default value.
  - You don’t have to specify it unless you would like a different
    label.
- Graph title: “Histogram of Pigs’ Weights”

*Hint:* Remember, a parameter is information that goes in the
parenthesis of the function.

Multiple parameters: `function_name(parameter1, parameter2)`

- E.g.,
  `hist(dataset, xlab="x-label", ylab = "y-label", main = "main title")`

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

![](basics-0_files/figure-gfm/unnamed-chunk-59-1.png)<!-- -->

``` r
# The histogram will appear in the Plot tab.
```

</details>

{::options parse_block_html='false'/}

The histogram will appear in the Plots tab (bottom right quadrant if you
haven’t modified your RStudio layout).

<br>

## 4. Importing Data

So far, we’ve create our own objects by manually entering all of the
data in the console. In this section, we’ll learn how to create objects
by importing (aka ‘reading’) data (compiled outside of R) into R and
visualise it with a histogram.

### 4.1 Importing Excel data into R

R can handle multiple file types:

- .csv (comma separated values)
- excel (.xls, .xlsx)
- .txt (and .tsv - tab separated values)
- .json (used for nested data structures)
  - These would likely be arrays of more than 2 dimensions.
- SPSS (another specialized statistics software)
- Data scraped from the web or via an API.

#### <u>Task 4.1.1</u> Download and save test data

Download and save [this Excel spreadsheet of Income
data](docs/income.xlsx){:target=“\_blank”}

- *Note:* Please remember where the income.xlsx file is saved (usually
  in a “downloads” or “desktop” folder).

#### <u>Task 4.1.2:</u> Import the dataset of Income data

- From the top menu bar, select…
- File
- Import dataset
- From Excel
- In the ‘Import Excel Data’ window select your file by:
- Entering the file path to the income.xlsx file you just downloaded.
- Selecting “Browse” on the right side of the path bar and locating it
  in the browser.
- Under ‘Import Options,’ make sure ‘Name’ is the same text as you wish
  for the variable to be named. Ours will be ‘income’.
- Click “Import”
- If asked to install the `readxl` package, click **Yes**.

> Note: Don’t worry about making a mistake importing this data. You can
> always remove it using the `rm()` function.

<figure>
<img src="images/rstudio-15.png"
alt="Browse and import menu and buttons" />
<figcaption aria-hidden="true">Browse and import menu and
buttons</figcaption>
</figure>

<figure>
<img src="images/rstudio-17.png" alt="Import excel data window" />
<figcaption aria-hidden="true">Import excel data window</figcaption>
</figure>

<!-- remove summary command from screenshot-->

<br>

What you just imported is now stored as a ‘data frame’ object whose name
is `income`.

**Definition - Data frame:** essentially a table. It is 2-dimensional
object that can hold different types of data types.

> Additional: Data frames contain information about a set of objects
> (e.g., cats).<br> - The data frame will contain one or more columns
> and one or more rows.<br> - One column contains related values (column
> 1 = age, column 2 = eye color).<br> - Because the column contains the
> same type of information, it is equivalent to a vector. <br> - i.e.,
> the ‘eye color’ column will contain characters, not numbers.<br> - One
> row denotes one object from the set. In a data frame of information
> about a set of cats, each row is information about one specific cats.

A row can contain many different bits of information, like age
(numerical), eye color (character), breed (character), whether or not
it’s spayed/neutered (boolean). Because rows may contain values of
different types, one row would most likely not be a vector. It would
likely be a list, which can contain values of different types.

To see the data in our data frame, simply enter the name of the data
frame in the console and type ‘enter’ or ‘return’.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
income
```

</details>

{::options parse_block_html='false'/}

<br>

The following will be the output:

    ## # A tibble: 10 × 4
    ##       id gender income experience
    ##    <dbl> <chr>   <dbl>      <dbl>
    ##  1     1 M       23000          3
    ##  2     2 M       55000          7
    ##  3     3 M       43000          5
    ##  4     4 F       37000          5
    ##  5     5 M       75000          9
    ##  6     6 M       72000         10
    ##  7     7 F      121000         13
    ##  8     8 F       27000          1
    ##  9     9 F       57000          8
    ## 10    10 F       91000         10

> Note: We will explore other ways to view and preview content of our
> data frames in Activity 3.

> Note: `<char>` stands for “character” data type and `<dbl>` stands for
> “double-precision floating point numbers data” type. <br>

We can see now that our data frame `income` contains 10 objects (rows),
and 4 variables (columns)

- It can be inferred that this data relates to 10 people
- The values with each person are:
  - id (in lieu of a name) (dbl)
  - gender (char)
  - income (dbl)
  - experience (dbl) <br>

#### <u>Task 4.1.3:</u> Display a summary of statistics for the `income` data.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
summary(income)
```

    ##        id           gender              income         experience   
    ##  Min.   : 1.00   Length:10          Min.   : 23000   Min.   : 1.00  
    ##  1st Qu.: 3.25   Class :character   1st Qu.: 38500   1st Qu.: 5.00  
    ##  Median : 5.50   Mode  :character   Median : 56000   Median : 7.50  
    ##  Mean   : 5.50                      Mean   : 60100   Mean   : 7.10  
    ##  3rd Qu.: 7.75                      3rd Qu.: 74250   3rd Qu.: 9.75  
    ##  Max.   :10.00                      Max.   :121000   Max.   :13.00

</details>

{::options parse_block_html='false'/}

<br>

### 4.2 Visualize Income with a Histogram plot

In 3.2 we made a histogram to visualize the distribution of the pig
weights. Remember that the parameter that the histogram function takes
is a vector.

To extract a vector (column) from our data frame, we will pass in
`dataframeName$columnName`, where the name of our data is separated by
the name identifying a single set of values within that data frame.

- Replace *dataframeName* with the name of your imported data
- Replace *columnName* with the column name representing the information
  you would like to analyse.
- e.g. ‘eyeColour’ might be the column name in a dataframe named ‘cats’.

#### <u>Task 4.2.1:</u> Display the vector of data relating to ‘experience’ in a histogram.

- X-label: ‘Experience’
- Title: ‘Histogram of Experience’ <br>

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#Remember, the generated histogram will appear in the Plot tab.
hist(income$experience, main='Histogram of Experience',xlab='Experience')
```

</details>

{::options parse_block_html='false'/}

<br>

The following will be the output:

![](basics-0_files/figure-gfm/unnamed-chunk-71-1.png)<!-- -->

We can see in the histogram that there are 7 intervals with equally
spaced breaks. In this case, the height of a cell is equal to the number
of observations falling in that cell.

- Why are there 7 intervals? R automatically chooses the number of
  intervals for you.

> Additional: If you preferred having 4 intervals (i.e., ‘bins’), use
> can set that using the `breaks=''` parameter.

{::options parse_block_html='true' /}
<details>
<summary>
Check Your Code for custom number of intervals
</summary>

``` r
#breaks is equal to the number of intervals
#You can add the custom labels if you would like `main='Histogram of Experience',xlab='Experience', `
hist(income$experience, breaks=3)
```

![](basics-0_files/figure-gfm/unnamed-chunk-73-1.png)<!-- -->
</details>

{::options parse_block_html='false'/}

<br>

<script>  
&#10;function toggle(input) {
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
</style>

[NEXT STEP: Tidyverse and Data Manipulation](tidyverse-data.html){: .btn
.btn-blue }
