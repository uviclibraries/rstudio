---
layout: default
title: 4-Importing Data
nav_order: 5
parent: Workshop Activities
customjs: http://code.jquery.com/jquery-1.4.2.min.js
---

4-Importing Data
================

- [1. Importing Excel data into R](#1-importing-excel-data-into-r)
- [2 Visualize Income with a Histogram
  plot](#2-visualize-income-with-a-histogram-plot)

<img src="images/rstudio-22.png" alt="rstudio logo" style="float:right;width:220px;"/>
<br>

So far, we’ve create our own objects by manually entering all of the
data in the console. In this section, we’ll learn how to create objects
by importing (aka ‘reading’) data (compiled outside of R) into R and
visualise it with a histogram.

## 1. Importing Excel data into R

R can handle multiple file types:

- .csv (comma separated values)
- excel (.xls, .xlsx)
- .txt (and .tsv - tab separated values)
- .json (used for nested data structures)
  - These would likely be arrays of more than 2 dimensions.
- SPSS (another specialized statistics software)
- Data scraped from the web or via an API.

<div class="task-box" markdown="1">

⭐ <u>Task 1-1</u>

**Download data.**

Download and save [this Excel spreadsheet of Income
data](docs/income.xlsx){:target=“\_blank”}

- *Note:* Please remember where the income.xlsx file is saved (usually
  in a “downloads” or “desktop” folder).

</div>

<div class="task-box" markdown="1">

⭐ <u>Task 1-2</u>

**Import data.**

Import the dataset of Income data

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

</div>

Don’t worry about making a mistake importing this data. You can always
remove it using the `rm()` function.

Browse and import menu and buttons <br>

<img src="images/rstudio-15.png" alt="Browse and import menu and buttons" style="width:600px;"/>

<br> Import excel data window

<img src="images/rstudio-17.png" alt="Import excel data window" style="width:600px;"/>

<br>

What you just imported is now stored as a ‘data frame’ object whose name
is `income`.

**Definition - Data frame:** essentially a table. It is 2-dimensional
object that can hold different types of data types.

<details>
<summary>
More about Data frames
</summary>
Data frames contain information about a set of objects (e.g.,
cats).<br> - The data frame will contain one or more columns and one or
more rows.<br> - One column contains related values (column 1 = age,
column 2 = eye color).<br> - Because the column contains the same type
of information, it is equivalent to a vector. <br> - i.e., the ‘eye
color’ column will contain characters, not numbers.<br> - One row
denotes one object from the set. In a data frame of information about a
set of cats, each row is information about one specific cats.
</details>

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

We will explore other ways to view and preview content of our data
frames in Activity 3.

**Note:** `<char>` stands for “character” data type and `<dbl>` stands
for “double-precision floating point numbers data” type. <br>

We can see now that our data frame `income` contains 10 objects (rows),
and 4 variables (columns)

- It can be inferred that this data relates to 10 people
- The values with each person are:
  - id (in lieu of a name) (dbl)
  - gender (char)
  - income (dbl)
  - experience (dbl) <br>

<div class="task-box" markdown="1">

⭐ <u>Task 1-3</u>

**Display summary statistics.**

Display a summary of statistics for the `income` data.

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

</div>

<br>

## 2 Visualize Income with a Histogram plot

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

<div class="task-box" markdown="1">

⭐ <u>Task 2</u>

**Create a histogram.**

Display the vector of data relating to ‘experience’ as a histogram.

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

</div>

The following will be the output:

![](basics-importing-data_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

We can see in the histogram that there are 7 intervals with equally
spaced breaks. In this case, the height of a cell is equal to the number
of observations falling in that cell.

- Why are there 7 intervals? R automatically chooses the number of
  intervals for you.

*Additional:* If you preferred having 4 intervals (i.e., ‘bins’), use
can set that using the `breaks=''` parameter.

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

![](basics-importing-data_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->
</details>

{::options parse_block_html='false'/}

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

[NEXT STEP: Tidyverse and Data Manipulation](tidyverse-data.html){: .btn
.btn-blue }
