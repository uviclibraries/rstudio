---
layout: default
title: 5-Data Manipulation
nav_order: 6
parent: Workshop Activities
customjs: http://code.jquery.com/jquery-1.4.2.min.js
---
5-Data Manipulation
================
DSC Chloe Farr
2024-01-18

- [Data Manipulation with Tidyverse](#data-manipulation-with-tidyverse)
  - [1. Getting Ready for Tidyverse : Installing
    Packages](#1-getting-ready-for-tidyverse--installing-packages)
  - [2. Getting data](#2-getting-data)
  - [3. Preparing our Workspace](#3-preparing-our-workspace)
  - [4. Introducing Piping](#4-introducing-piping)
    - [4.1 Before Piping](#41-before-piping)
    - [4.2 Piping](#42-piping)
    - [4.3 Selecting specific columns](#43-selecting-specific-columns)
    - [4.4 Select specific rows based on a
      condition](#44-select-specific-rows-based-on-a-condition)
    - [4.5 Modify a data frame with
      `mutate()`](#45-modify-a-data-frame-with-mutate)
    - [4.6 Sorting data with `arrange()`](#46-sorting-data-with-arrange)
    - [4.7 Summarizing variables with
      `summarise()`](#47-summarizing-variables-with-summarise)
    - [4.8 Analyzing groups with
      `group_by()`](#48-analyzing-groups-with-group_by)

<style type="text/css">
div.html-widget {
  overflow-x: auto;
}
&#10;table {
  display: block;
  max-width: none;
  white-space: nowrap;
}
</style>

<img src="images/tidyverse-01.png" alt="rstudio logo" style="float:right;width:180px;"/>

# Data Manipulation with Tidyverse

If you and your group have any questions or get stuck as you work
through this in-class exercise, please ask the instructor for
assistance. Have fun!

## 1. Getting Ready for Tidyverse : Installing Packages

One of the most fascinating things about R is that it has an active
community developing a lot of packages everyday, which makes R powerful.
A package is a compilation of functions (data sets, code, documentations
and tests) external to R that provide it with additional capabilities.

We can install packages in the console using the `install.packages()`
function.

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 1-1</u>

**Install the tidyverse package in the Console window.**

Package name: tidyverse

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
install.packages("tidyverse")
```

</details>

{::options parse_block_html='false'/} *Hint:* wrap the package name in
`""` quotations, because it is a string type.

</div>

*Note:* The installation may take a while, sometimes up to 10-15
minutes. When it’s complete, the right angle bracket `>` will appear at
the last line of your console.

**Confirm installation**

To check if the package is installed, enter the following in the console

``` r
# Paste both lines into the console, and then run. 
installed <- installed.packages()
"tidyverse" %in% rownames(installed)
```

    ## [1] TRUE

<details>
<summary>
Why no quotations for library()?
</summary>

<br> When you install a package in R using **`install.packages()`**, the
package name must be a character string, hence the quotes. This is
because **`install.packages()`** is a function that takes a character
vector as its argument, representing the names of the packages to be
installed.

However, when you load a package using **`library()`** or
**`require()`**, you’re not passing a character string; instead, you’re
using a non-evaluated expression that refers to the package name. Here,
the package name is an object of mode “name” which **`library()`**
interprets as the name of a package to load.

In summary, the quotes are needed for **`install.packages()`** because
it expects a character string, while **`library()`** is designed to take
an unquoted name that it interprets as a package name.

</details>

<br>

**Load the ‘tidyverse’ library.**

After we install a package, we have to load it using the `library()`
function.

- Do not wrap the package name in quotes when using `library()`.

- :heavy_exclamation_mark: Put this command in your R script, not in the
  console. Why? The package only needs to be *installed* once, but it
  needs to be *loaded* any time you open your script.

  - Packages also need to be reloaded every time the project is ‘knit’,
    an action covered in the intermediate workshop.

<details>
<summary>
Check Your Code
</summary>

``` r
library(tidyverse) #then, as always, type 'enter' or 'return' to submit the command for execution
```

</details>

{::options parse_block_html='false'/} <br>

## 2. Getting data

<div class="task-box" markdown="1">

⭐ <u>Task 2-1</u>

**Download and import data**

From [this
link](https://uviclibraries.github.io/rstudio/docs/Global_Superstore_Orders_2016.csv){:target=“\_blank”}
download the following data we have prepared for you to use in this
activity.

Save the file in the same folder as your R script.

Import the data as you learned in the previous activity.

</div>

<img src="images/messy_purchase_orders.png" alt="purchase orders photo" style="float:right;width:180px;"/>

*If you have your own data, you may use that as well although it may not
line up with the instructions in the activity.* <br>

*Note:* Activities 3 and 4 draw from Kaggle’s [Manipulating Data with
the
Tidyverse](https://www.kaggle.com/code/rtatman/manipulating-data-with-the-tidyverse/notebook){:target=“\_blank”}.

## 3. Preparing our Workspace

In this activity, we will be working with a table containing information
about shipping orders Each row represents one order, and each column
represents a specific type of data pertaining to the orders <br>

- Rename your data set to `purchaseData`

``` r
#if your file cannot be found, enter `getwd()` into your console and it will tell you the file path you should most likely use. If you cannot find the file, use Option a.
purchaseData <- read.csv("docs/Global_Superstore_Orders_2016.csv")
```

<br> :heavy_exclamation_mark: For larger data sets, it’s better to
*preview* than *view* our data. Purchase Data has quite a few columns
and rows! Let’s take a look at the first few rows and get the dimensions
(number of rows and columns) of the data set.

We can preview the data set using the `head()` function. This will
display the first number of rows.

- Parameters (in order):
  - data set name
  - number of rows to display

*Note:* In cases where there are more columns that fit horizontally in
the console, the results will wrap, as seen in the output of Task 3-1.

<div class="task-box" markdown="1">

⭐ <u>Task 3-1</u>

**Look at the first 5 rows of our purchase data.**

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# name of data set name: "purchaseData"
# number of rows to display: 5
head(purchaseData, 5)
```

</details>

{::options parse_block_html='false'/} *Hint:*
`head(*data setName*, *numberOfRows*)`

</div>

<br>

The following will be the output (For the purpose of readability, this
only shows 6 columns. Your output will be much wider, and columns will
continue to wrap below!):

    ##   Row_ID                 Order_ID Order_Date  Ship_Date    Ship_Mode
    ## 1  40098 CA-2014-AB10015140-41954 2014-11-11 2014-11-13  First Class
    ## 2  26341   IN-2014-JR162107-41675 2014-02-05 2014-02-07 Second Class
    ## 3  25330   IN-2014-CR127307-41929 2014-10-17 2014-10-18  First Class
    ## 4  13524  ES-2014-KM1637548-41667 2014-01-28 2014-01-30  First Class
    ## 5  47221  SG-2014-RH9495111-41948 2014-11-05 2014-11-06     Same Day
    ##    Customer_ID
    ## 1 AB-100151402
    ## 2    JR-162107
    ## 3    CR-127307
    ## 4   KM-1637548
    ## 5   RH-9495111

We can find out the dimensions (rows and columns) using the`dim()`
function.

- Parameter: data set name

Now, we’ve imported our data and previewed the first 10 rows of our
purchase data, but how big is the data set?

- How many rows?
- How many columns?

<div class="task-box" markdown="1">

⭐ <u>Task 3-2</u>

**Find out the dimensions of the data set**, i.e., number of rows and
columns.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
## name of data set name: "purchaseData"
dim(purchaseData)
```

    ## [1] 51290    24

</details>

{::options parse_block_html='false'/}

</div>

------------------------------------------------------------------------

:round_pushpin: Reminder! Save your work

------------------------------------------------------------------------

## 4. Introducing Piping

`%>%` This symbol is known as a “pipe,” and it’s used for feeding the
result of one function directly into the next function.

- e.g., To sort the column names alphabetically, you could either enter:
  - two separate commands creating two data objects
  - utilize piping to create one data object for your target object.

In pipes, you can choose to have a newline (shift+enter) after the %\>%
symbol or leave it all on one line. <br>

### 4.1 Before Piping

Piping allows us to perform multiple functions at once to achieve a
single result. So far, we have looked at commands that perform single
operations.

- Create a variable whose value is a single word
  - `y <- "word"`
- Create a variable whose value by mathematical expression
  - `x <- 1-2`
- viewing the dimensions of a data set
  - `dim(purchaseData)`

What if we want to get a list of column names in our data set, AND sort
it alphabetically?

- There are 2 ways that we can do this without the tidyverse package
  based on what we’ve already learned.

<br>

For the following activity, we’ll be using column names of our data
frame.

- To get a list of our column names we can use the `names()` function.
  - parameter: data frame
  - In this case, results appear in a vector rather than a list because
    the column names are all the same data type (strings).
  - *Note*: The `names()` function is only useful for data frames and
    matrices for which we have column names.

<div class="task-box" markdown="1">

⭐ <u>Task 4.1-1</u>

**Create an object**

Create an object containing the list of column names from our purchase
data.

- Name this object `purchaseDataColumnNames`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
purchaseDataColumnNames <- names(purchaseData)
```

</details>

{::options parse_block_html='false'/}

</div>

<br>

We can sort vectors into ascending and descending order (low to high or
high to low) using the `sort()` function.

- Parameter: the vector of column names

Let’s look at each of these functions on their own.

<div class="task-box" markdown="1">

⭐ <u>Task 4.1-2</u>

**Create an object**

Create an containing the list of column names from our purchase data
that is sorted alphabetically.

- Name this object `alphaPurchaseDataColumnNames`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
alphaPurchaseDataColumnNames <- sort(purchaseDataColumnNames)
```

</details>

{::options parse_block_html='false'/}

*Hint:* You already created the vector containing the list of column
names from our purchase data! <br>

</div>

<br> In Tasks 4.1-1 and 4.1-2, we ran two commands resulting in two
separate variables containing the column names:

- `purchaseDataColumnNames`: Ordered as they would be if the file were
  opened in excel
- `alphaPurchaseDataColumnNames`: Ordered alphabetically (sorted)

<br> However, if we only care about the list of column names if they are
sorted alphabetically:

- We can achieve that using only 1 command,
  - creating only 1 variable with “nesting”.

<br> **Definition - Nesting:** Use one function as a parameter of
another function.

- e.g., `function1(function2(parameter))`

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 4.1-3</u>

**Create a variable through nested functions**

In this task, use nesting to create 1 variable containing a sorted
vector of the column names.

- Name this variable: `alphabeticalColumnNames` <br>

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#names(purchaseData) creates a vector object of the column names from our purchase data
# sort() Orders the items in the purchase data column names alphabetically
alphabeticalColumnNames <- sort(names(purchaseData))
```

</details>

{::options parse_block_html='false'/}

<br> *Hints*: the parameter of `names()` is the `sort()` function, and
the parameter of `sort()` is the data set.

</div>

<br> As you might imagine, nesting could result in very long commands
that would be hard to interpret.

There is a cleaner way to do this than nesting: Piping!

------------------------------------------------------------------------

### 4.2 Piping

To pipe a command instead of nesting, we will enter the commands
sequentially, separated by the pipe symbol `%>%`.

- Creating a new variable with 2 criteria (functions or expressions):
  newVariable \<- criteria1() %\>% criteria2()

- Previewing our data with 2 criteria: criteria1() %\>% criteria2()

<br>

<div class="task-box" markdown="1">

⭐ <u>Task 4.2-1</u>

**Create a variable through piping**

In this task, use piping to create 1 variable containing the first 5
column names.

- Do not use objects you have created so far, except `purchaseData`
- Name your new variable: `purchaseDataNamesPeek` <br>

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# 'purchaseDataNamesPeek <-' creates a new variable
# 'names(purchaseData)' retrieves the column names from our purcgase data as a vector
# The pipe '%>%' passes the names vector to the 'head()' function
# 'head(5)' then extracts the first five elements (columns) of this vector
# The result is a 5-item vector of column names assigned to 'purchaseDataNamesPeek'
purchaseDataNamesPeek <- names(purchaseData) %>% head(5)

#remember, you can view the value assigned to a variable by entering just that variable name
purchaseDataNamesPeek
```

    ## [1] "Row_ID"     "Order_ID"   "Order_Date" "Ship_Date"  "Ship_Mode"

</details>

{::options parse_block_html='false'/}

*Hint*: the parameter of `names()` is the `head()` function. <br>

</div>

If you want to simply view what the first five column names are, but
don’t need to reference them later, you don’t need to create a new
variable. <br>

{::options parse_block_html='true' /}
<details>
<summary>
Show code for previewing with piping
</summary>

``` r
# Do not begin the command with `newVariableName <-`
names(purchaseData) %>% head(5)
```

    ## [1] "Row_ID"     "Order_ID"   "Order_Date" "Ship_Date"  "Ship_Mode"

</details>

{::options parse_block_html='false'/}

------------------------------------------------------------------------

When we work with data, it can be useful to work with smaller sections
of data.

In the remainder of activity 4, we will look at ways to select subsets
of our data to make it easier to work with.

- We will use piping to filter productData based on different
  conditions, such as:
  - Previewing only the column names that begin with `Product`
  - Previewing only the purchases from Tampa Bay
  - Previewing only the purchases that are corporate orders
  - Previewing only the purchases from Tampa that aren’t critical
    priority

Before we begin to filter, we need to look at Operators.

**Definition - “Operators”:** Special symbols or keywords used to
perform operations on arguments - logical operators specifically
designed for connecting or modifying boolean (true/false) logic
statements. <br>

**Operators**

- Logical operators
  - \< means “less than”
  - \<= means “less than or equal to”
  - \> means “greater than”
  - \>= means “greater than or equal to”
  - == means “exactly equal to”
  - != means “not equal to”
- Connecting logical statements:
  - x \| y means “x or y”
  - x & y means “x and y”

------------------------------------------------------------------------

:round_pushpin: Reminder! Save your work

------------------------------------------------------------------------

### 4.3 Selecting specific columns

The commands in this section (4.3) will not create data objects as we
won’t be using them later on.

**- End each command in this section with `%>% head(5)`**

- Not ending functions that extract full columns of data will display a
  LOT.

- This will make things easier for you.

- To get a specific column, use piping and the `select()` function on
  your data set.

  - The parameter is the name of the column you want to access.

<div class="task-box" markdown="1">

⭐ <u>Task 4.3-1</u>

**View a vector**

Preview the values in the Row ID column.

- Column name: `Row_ID`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#data set %>% select the column titled `Row ID` and view the first 5 items.
purchaseData %>% select(Row_ID) %>% head(5)
```

    ##   Row_ID
    ## 1  40098
    ## 2  26341
    ## 3  25330
    ## 4  13524
    ## 5  47221

</details>

{::options parse_block_html='false'/}

*Hint:* Begin with the name of the data set, followed by your select
function passing in the column name as the parameter.

</div>

To select all of the columns from our data set that do *not* start with
specific text, we do the inverse,

- Again using the `select()` function
- The parameter has a minus sign `-` before the string value we want to
  exclude.

<div class="task-box" markdown="1">

⭐ <u>Task 4.3-2</u>

**Get a set of vectors from data frame**

Select all the columns from your purchase data that do *not* start with
“Postal_Code”.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
purchaseData %>% select(-Postal_Code) %>% head(5)
```

    ##   Row_ID                 Order_ID Order_Date  Ship_Date    Ship_Mode
    ## 1  40098 CA-2014-AB10015140-41954 2014-11-11 2014-11-13  First Class
    ## 2  26341   IN-2014-JR162107-41675 2014-02-05 2014-02-07 Second Class
    ## 3  25330   IN-2014-CR127307-41929 2014-10-17 2014-10-18  First Class
    ## 4  13524  ES-2014-KM1637548-41667 2014-01-28 2014-01-30  First Class
    ## 5  47221  SG-2014-RH9495111-41948 2014-11-05 2014-11-06     Same Day
    ##    Customer_ID    Customer_Name     Segment          City           State
    ## 1 AB-100151402    Aaron Bergman    Consumer Oklahoma City        Oklahoma
    ## 2    JR-162107    Justin Ritter   Corporate    Wollongong New South Wales
    ## 3    CR-127307     Craig Reiter    Consumer      Brisbane      Queensland
    ## 4   KM-1637548 Katherine Murray Home Office        Berlin          Berlin
    ## 5   RH-9495111      Rick Hansen    Consumer         Dakar           Dakar
    ##         Country         Region       Market  Product_ID   Category Sub_Category
    ## 1 United States     Central US         USCA TEC-PH-5816 Technology       Phones
    ## 2     Australia        Oceania Asia Pacific FUR-CH-5379  Furniture       Chairs
    ## 3     Australia        Oceania Asia Pacific TEC-PH-5356 Technology       Phones
    ## 4       Germany Western Europe       Europe TEC-PH-5267 Technology       Phones
    ## 5       Senegal Western Africa       Africa TEC-CO-6011 Technology      Copiers
    ##                                Product_Name   Sales Quantity Discount  Profit
    ## 1                          Samsung Convoy 3  221.98        2      0.0   62.15
    ## 2 Novimex Executive Leather Armchair, Black 3709.40        9      0.1 -288.77
    ## 3         Nokia Smart Phone, with Caller ID 5175.17        9      0.1  919.97
    ## 4            Motorola Smart Phone, Cordless 2892.51        5      0.1  -96.54
    ## 5            Sharp Wireless Fax, High-Speed 2832.96        8      0.0  311.52
    ##   Shipping_Cost Order_Priority
    ## 1         40.77           High
    ## 2        923.63       Critical
    ## 3        915.49         Medium
    ## 4        910.16         Medium
    ## 5        903.04       Critical

</details>

{::options parse_block_html='false'/}

</div>

:heavy_exclamation_mark:We can also select a *subset* of columns

- e.g., columns whose names begin with a common string of characters.

- This will return a subset of our table, not necessarily a single
  vector

In our data set, multiple column names begin with “Product”. We want to
see only the data of columns whose names begin with “Product.” The
following explains the process.

- Use piping on your purchaseData

  - `purchaseData %>%`

- Use the `select()` function to select the columns

- Use the `starts_with()` function as the parameter for `select()`

  - notes that you’re selecting all columns that start with a specific
    name

    - rather one column that is exactly equal or not equal to a specific
      value

- The parameter for `starts_with()` is the value of the beginning of all
  columns you want to select.

<div class="task-box" markdown="1">

⭐ <u>Task 4.3-3</u>

**Get a set of vectors from data frame**

Select all the columns from our cleaned purchase data that start with
“Product”.

Write the one-line command to achieve this with piping

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
# Selects all columns (and their values) from purchaseData whose names begin with "Product"
purchaseData %>% select(starts_with("Product")) %>% head(5)
```

    ##    Product_ID                              Product_Name
    ## 1 TEC-PH-5816                          Samsung Convoy 3
    ## 2 FUR-CH-5379 Novimex Executive Leather Armchair, Black
    ## 3 TEC-PH-5356         Nokia Smart Phone, with Caller ID
    ## 4 TEC-PH-5267            Motorola Smart Phone, Cordless
    ## 5 TEC-CO-6011            Sharp Wireless Fax, High-Speed

</details>

{::options parse_block_html='false'/}

</div>

### 4.4 Select specific rows based on a condition

While we may only want to handle certain items (rows) in our data set
based on certain criteria.

- This is called “filtering”

- We can filter for different purposes, like processing statistical
  operations, making charts and so on.

- We can even create new data objects, which can make future analyses
  easier.

<br>

To select items (rows, *not* columns), we use the `filter()` function.

- The parameter for `filter()` is the name of the column holding the
  values that are being filtered.

<div class="task-box" markdown="1">

⭐ <u>Task 4.4-1</u>

**Filter conditionally**

Filter all the rows from your purchase data where `Quantity` is greater
than 10.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
purchaseData %>% filter(Quantity > 10) %>% head(5)
```

    ##   Row_ID                 Order_ID Order_Date  Ship_Date      Ship_Mode
    ## 1  27704  IN-2014-PF1912027-41796 2014-06-06 2014-06-08   Second Class
    ## 2  12069  ES-2015-PJ1883564-42255 2015-09-08 2015-09-14 Standard Class
    ## 3  15380 ES-2015-PO18865139-42018 2015-01-14 2015-01-18 Standard Class
    ## 4  25795  IN-2015-VG2180558-42273 2015-09-26 2015-09-28   Second Class
    ## 5   6550 MX-2015-JH15820141-42356 2015-12-18 2015-12-20   Second Class
    ##   Customer_ID     Customer_Name   Segment Postal_Code               City
    ## 1  PF-1912027      Peter Fuller  Consumer          NA         Mudanjiang
    ## 2  PJ-1883564     Patrick Jones Corporate          NA              Prato
    ## 3 PO-18865139 Patrick O'Donnell  Consumer          NA   Stockton-on-Tees
    ## 4  VG-2180558       Vivek Grady Corporate          NA Thiruvananthapuram
    ## 5 JH-15820141       John Huston  Consumer          NA           Paysandú
    ##          State        Country          Region       Market  Product_ID
    ## 1 Heilongjiang          China    Eastern Asia Asia Pacific OFF-AP-4959
    ## 2      Tuscany          Italy Southern Europe       Europe OFF-AP-4743
    ## 3      England United Kingdom Northern Europe       Europe TEC-CO-3598
    ## 4       Kerala          India   Southern Asia Asia Pacific FUR-BO-5951
    ## 5     Paysandú        Uruguay   South America        LATAM FUR-CH-4531
    ##          Category Sub_Category
    ## 1 Office Supplies   Appliances
    ## 2 Office Supplies   Appliances
    ## 3      Technology      Copiers
    ## 4       Furniture    Bookcases
    ## 5       Furniture       Chairs
    ##                                          Product_Name   Sales Quantity Discount
    ## 1                         KitchenAid Microwave, White 3701.52       12        0
    ## 2                                   Hoover Stove, Red 7958.58       14        0
    ## 3                          Brother Fax Machine, Laser 4141.02       13        0
    ## 4                Sauder Classic Bookcase, Traditional 5667.87       13        0
    ## 5 Harbour Creations Executive Leather Armchair, Black 3473.14       11        0
    ##    Profit Shipping_Cost Order_Priority
    ## 1 1036.08        804.54       Critical
    ## 2 3979.08        778.32            Low
    ## 3 1697.67        668.96           High
    ## 4 2097.03        658.35         Medium
    ## 5  868.12        634.53           High

</details>

{::options parse_block_html='false'/}

*Hint:* `>` is the ‘greater than’ operator.

</div>

<div class="task-box" markdown="1">

⭐ <u>Task 4.4-2</u>

**Filter conditionally**

Filter all the rows from your purchase data where `City` is “Sydney”.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
purchaseData %>% filter(City == "Sydney") %>% head(5)
```

    ##   Row_ID               Order_ID Order_Date  Ship_Date      Ship_Mode
    ## 1  22732 IN-2014-JM156557-41818 2014-06-28 2014-07-01   Second Class
    ## 2  25026 IN-2013-RP192707-41438 2013-06-13 2013-06-13       Same Day
    ## 3  29629 IN-2014-LC168857-41747 2014-04-18 2014-04-19    First Class
    ## 4  21263 IN-2015-MB173057-42179 2015-06-24 2015-06-28 Standard Class
    ## 5  20521 IN-2015-BE114557-42080 2015-03-17 2015-03-22   Second Class
    ##   Customer_ID   Customer_Name     Segment Postal_Code   City           State
    ## 1   JM-156557     Jim Mitchum   Corporate          NA Sydney New South Wales
    ## 2   RP-192707    Rachel Payne   Corporate          NA Sydney New South Wales
    ## 3   LC-168857  Lena Creighton    Consumer          NA Sydney New South Wales
    ## 4   MB-173057 Maria Bertelson    Consumer          NA Sydney New South Wales
    ## 5   BE-114557      Brad Eason Home Office          NA Sydney New South Wales
    ##     Country  Region       Market  Product_ID   Category Sub_Category
    ## 1 Australia Oceania Asia Pacific TEC-PH-5842 Technology       Phones
    ## 2 Australia Oceania Asia Pacific TEC-CO-3611 Technology      Copiers
    ## 3 Australia Oceania Asia Pacific TEC-CO-6012 Technology      Copiers
    ## 4 Australia Oceania Asia Pacific FUR-BO-5948  Furniture    Bookcases
    ## 5 Australia Oceania Asia Pacific TEC-CO-4568 Technology      Copiers
    ##                          Product_Name   Sales Quantity Discount  Profit
    ## 1 Samsung Smart Phone, with Caller ID 2862.68        5      0.1  763.28
    ## 2         Brother Wireless Fax, Laser 3068.36        9      0.1 1124.90
    ## 3           Sharp Wireless Fax, Laser 1601.64        5      0.1  587.19
    ## 4      Sauder Classic Bookcase, Metal 5486.67       14      0.1 2316.51
    ## 5         Hewlett Copy Machine, Color 3299.56       14      0.1  366.28
    ##   Shipping_Cost Order_Priority
    ## 1        897.35       Critical
    ## 2        555.77           High
    ## 3        511.47       Critical
    ## 4        346.60         Medium
    ## 5        336.02         Medium

</details>

{::options parse_block_html='false'/}

*Hint:* `==` is used for “equal to”

</div>

<div class="task-box" markdown="1">

⭐ <u>Task 4.4-3</u>

**Create a data frame**

Create a new data frame with all the rows from purchaseData where
`Country` is “United States” and `Discount` is greater than 0.

- Name this data frame: `discountedUSPurchases`

- :heavy_exclamation_mark: Do not add ” %\>% head(5)” to the command
  when <u>creating</u> a new data frame

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
discountedUSPurchases <- purchaseData %>% filter(Country == "United States" & Discount > 0)

#view your data frame
discountedUSPurchases %>% head(5)
```

    ##   Row_ID                 Order_ID Order_Date  Ship_Date      Ship_Mode
    ## 1  36258 CA-2012-AB10015140-40974 2012-03-06 2012-03-07    First Class
    ## 2  39519 CA-2012-AB10015140-40958 2012-02-19 2012-02-25 Standard Class
    ## 3  40977 CA-2013-AH10030140-41635 2013-12-27 2013-12-31 Standard Class
    ## 4  36651 CA-2012-AH10030140-41041 2012-05-12 2012-05-18 Standard Class
    ## 5  37425 US-2012-AH10030140-41206 2012-10-24 2012-10-27    First Class
    ##    Customer_ID Customer_Name   Segment Postal_Code          City      State
    ## 1 AB-100151404 Aaron Bergman  Consumer       98103       Seattle Washington
    ## 2 AB-100151402 Aaron Bergman  Consumer       76017     Arlington      Texas
    ## 3 AH-100301404 Aaron Hawkins Corporate       94122 San Francisco California
    ## 4 AH-100301404 Aaron Hawkins Corporate       90004   Los Angeles California
    ## 5 AH-100301404 Aaron Hawkins Corporate       94109 San Francisco California
    ##         Country     Region Market  Product_ID        Category Sub_Category
    ## 1 United States Western US   USCA FUR-CH-4421       Furniture       Chairs
    ## 2 United States Central US   USCA OFF-ST-3078 Office Supplies      Storage
    ## 3 United States Western US   USCA TEC-PH-4389      Technology       Phones
    ## 4 United States Western US   USCA FUR-CH-4840       Furniture       Chairs
    ## 5 United States Western US   USCA OFF-BI-4372 Office Supplies      Binders
    ##                                    Product_Name  Sales Quantity Discount Profit
    ## 1    Global Push Button Manager's Chair, Indigo  48.71        1      0.2   5.48
    ## 2                            Akro Stacking Bins  12.62        2      0.2  -2.52
    ## 3                          Geemarc AmpliPOWER60 668.16        9      0.2  75.17
    ## 4 Iceberg Nesting Folding Chair, 19w x 6d x 43h 279.46        6      0.2  20.96
    ## 5                       GBC VeloBind Cover Sets  49.41        4      0.2  18.53
    ##   Shipping_Cost Order_Priority
    ## 1         11.13           High
    ## 2          1.97            Low
    ## 3         45.74         Medium
    ## 4         11.69         Medium
    ## 5          2.84           High

</details>

{::options parse_block_html='false'/} *Hint:* `&` is used for “and”, in
cases where you want to manage multiple cases like filtering my two
variables<br> - e.g., values of the `Sub_Category` and `Order_Priority`
columns.

</div>

------------------------------------------------------------------------

:round_pushpin: Reminder! Save your work

------------------------------------------------------------------------

### 4.5 Modify a data frame with `mutate()`

“Mutation” involves creating or altering columns in a data frame,

- using the `mutate()` function
  - e.g., If you have a column with a range of numbers, but you want to
    be able to quickly work with the data only over or under a specific
    value, like any orders under \$10, you can create a “Cheap” column
    and the values would be TRUE or FALSE.
- adds new variables or modifies existing ones.

<br> <u>Here’s how we’ll do it:</u>

- Assign the mutation (modification) to an existing variable
  - `existing_data frame_name <-`
- Identify the existing variable name of the object you want to mutate
  - `purchaseData`
- Use a pipe to identify the action being performed on our existing
  variable
  - `%>%`
- Identify that the action being performed on the existing variable is
  the mutation
  - using the `mutate()` function
- Pass the condition in as the parameter for the `mutate` function
  - If we want to add a variable (column), begin the parameter of
    `mutate()` with `new_column_name =`
    - `=` means the values assigned to each item in that column is
      generated by the following condition
    - The new column name is `Low_Priority` and is followed by
      `= (condition)`
  - Say we want to add a column that has a TRUE/FALSE variable (aka
    boolean) for whether the order priority is low.
    - The condition will be `Order_Priority == "Low"`
      - `==` means “the left value is equal to the right value”
        - aka. The result will be everything in the data that is “Low”

``` r
purchaseData <- purchaseData %>% mutate(Low_Priority = (Order_Priority == "Low"))

#view first 3 rows of your data frame
purchaseData %>% head(3)
```

    ##   Row_ID                 Order_ID Order_Date  Ship_Date    Ship_Mode
    ## 1  40098 CA-2014-AB10015140-41954 2014-11-11 2014-11-13  First Class
    ## 2  26341   IN-2014-JR162107-41675 2014-02-05 2014-02-07 Second Class
    ## 3  25330   IN-2014-CR127307-41929 2014-10-17 2014-10-18  First Class
    ##    Customer_ID Customer_Name   Segment Postal_Code          City
    ## 1 AB-100151402 Aaron Bergman  Consumer       73120 Oklahoma City
    ## 2    JR-162107 Justin Ritter Corporate          NA    Wollongong
    ## 3    CR-127307  Craig Reiter  Consumer          NA      Brisbane
    ##             State       Country     Region       Market  Product_ID   Category
    ## 1        Oklahoma United States Central US         USCA TEC-PH-5816 Technology
    ## 2 New South Wales     Australia    Oceania Asia Pacific FUR-CH-5379  Furniture
    ## 3      Queensland     Australia    Oceania Asia Pacific TEC-PH-5356 Technology
    ##   Sub_Category                              Product_Name   Sales Quantity
    ## 1       Phones                          Samsung Convoy 3  221.98        2
    ## 2       Chairs Novimex Executive Leather Armchair, Black 3709.40        9
    ## 3       Phones         Nokia Smart Phone, with Caller ID 5175.17        9
    ##   Discount  Profit Shipping_Cost Order_Priority Low_Priority
    ## 1      0.0   62.15         40.77           High        FALSE
    ## 2      0.1 -288.77        923.63       Critical        FALSE
    ## 3      0.1  919.97        915.49         Medium        FALSE

<div class="task-box" markdown="1">

⭐ <u>Task 4.5-1</u>

**Add a column to your dataframe**

Now try it yourself. Add a new boolean (TRUE/FALSE) variable (column) to
the purchase data that identifies whether a purchase’s shipping cost is
greater than 100 dollars.

- Name the new column: `High_Shipping`
- The value will be TRUE if the `Shipping_Cost` value is over (`>`) 100.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
purchaseData <- purchaseData %>% mutate(High_Shipping = (Shipping_Cost > 100))

#view your data frame
purchaseData %>% head(5)
```

    ##   Row_ID                 Order_ID Order_Date  Ship_Date    Ship_Mode
    ## 1  40098 CA-2014-AB10015140-41954 2014-11-11 2014-11-13  First Class
    ## 2  26341   IN-2014-JR162107-41675 2014-02-05 2014-02-07 Second Class
    ## 3  25330   IN-2014-CR127307-41929 2014-10-17 2014-10-18  First Class
    ## 4  13524  ES-2014-KM1637548-41667 2014-01-28 2014-01-30  First Class
    ## 5  47221  SG-2014-RH9495111-41948 2014-11-05 2014-11-06     Same Day
    ##    Customer_ID    Customer_Name     Segment Postal_Code          City
    ## 1 AB-100151402    Aaron Bergman    Consumer       73120 Oklahoma City
    ## 2    JR-162107    Justin Ritter   Corporate          NA    Wollongong
    ## 3    CR-127307     Craig Reiter    Consumer          NA      Brisbane
    ## 4   KM-1637548 Katherine Murray Home Office          NA        Berlin
    ## 5   RH-9495111      Rick Hansen    Consumer          NA         Dakar
    ##             State       Country         Region       Market  Product_ID
    ## 1        Oklahoma United States     Central US         USCA TEC-PH-5816
    ## 2 New South Wales     Australia        Oceania Asia Pacific FUR-CH-5379
    ## 3      Queensland     Australia        Oceania Asia Pacific TEC-PH-5356
    ## 4          Berlin       Germany Western Europe       Europe TEC-PH-5267
    ## 5           Dakar       Senegal Western Africa       Africa TEC-CO-6011
    ##     Category Sub_Category                              Product_Name   Sales
    ## 1 Technology       Phones                          Samsung Convoy 3  221.98
    ## 2  Furniture       Chairs Novimex Executive Leather Armchair, Black 3709.40
    ## 3 Technology       Phones         Nokia Smart Phone, with Caller ID 5175.17
    ## 4 Technology       Phones            Motorola Smart Phone, Cordless 2892.51
    ## 5 Technology      Copiers            Sharp Wireless Fax, High-Speed 2832.96
    ##   Quantity Discount  Profit Shipping_Cost Order_Priority Low_Priority
    ## 1        2      0.0   62.15         40.77           High        FALSE
    ## 2        9      0.1 -288.77        923.63       Critical        FALSE
    ## 3        9      0.1  919.97        915.49         Medium        FALSE
    ## 4        5      0.1  -96.54        910.16         Medium        FALSE
    ## 5        8      0.0  311.52        903.04       Critical        FALSE
    ##   High_Shipping
    ## 1         FALSE
    ## 2          TRUE
    ## 3          TRUE
    ## 4          TRUE
    ## 5          TRUE

</details>

{::options parse_block_html='false'/}

*Hint:* `Shipping_Cost > 100`

</div>

<div class="task-box" markdown="1">

⭐ <u>Task 4.5-2</u>

**Add a new column based on TWO conditions**

Add a new variable `Discounted_US` that is TRUE if the purchase is made
in the United States and has been discounted

- Filter for United States orders using the `Country` column
- Filter for discounted orders by selecting all objects where the values
  in the `Discount` column are greater than 0.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
purchaseData <- purchaseData %>% mutate(Discounted_US = (Country == "United States" & Discount > 0))
#We can then get summary of our new variable values (i.e., the number or True values and number of False values in the new 'Discounted_US' column)
#request a summary of the values in the table $ column name
summary(purchaseData$Discounted_US)
```

    ##    Mode   FALSE    TRUE 
    ## logical   46094    5196

</details>

{::options parse_block_html='false'/}

*Hint:* `logicalStatement & logicalStatement`

</div>

### 4.6 Sorting data with `arrange()`

Being able to arrange data by ordering values numerically or
alphabetically is particularly handy for swiftly identifying which
measurements recorded the highest or lowest values.

<!--**CHLOE: ADD SOME SORT OF GRAPHIC**-->

The `arrange()` function enables you to order your data frame according
to the values of a specific variable.

- Parameter of `arrange()` is `Sales`

- This is particularly handy for swiftly identifying which measurements
  recorded the highest or lowest values.

When using `arrange()`, you specify the column name that you wish to
organize by.

- In this case, it will arrange the data based on the sales value
  - a new variable that we recently formulated using `mutate()`

*hint*: You can also use the `sort()` function but it only takes a
vector parameter, not a data frame.

<div class="task-box" markdown="1">

⭐ <u>Task 4.6-1</u>

**Sort data frame**

Update `purchaseData` to sort objects by price (low to high).

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
purchaseData <- purchaseData %>% arrange(Sales)

#view your data frame
purchaseData %>% head(5)
```

    ##   Row_ID                 Order_ID Order_Date  Ship_Date      Ship_Mode
    ## 1  35398 US-2015-ZC21910140-42175 2015-06-20 2015-06-24 Standard Class
    ## 2  40589 CA-2015-RS19765140-42066 2015-03-03 2015-03-03       Same Day
    ## 3  39955 CA-2014-KB16600140-41812 2014-06-22 2014-06-26 Standard Class
    ## 4  36008 CA-2012-JO15280140-40998 2012-03-30 2012-03-30       Same Day
    ## 5  33403 US-2012-HG14965140-41177 2012-09-25 2012-09-25       Same Day
    ##    Customer_ID    Customer_Name   Segment Postal_Code         City        State
    ## 1 ZC-219101402 Zuschuss Carroll  Consumer       77095      Houston        Texas
    ## 2 RS-197651402   Roland Schwarz Corporate       76706         Waco        Texas
    ## 3 KB-166001402      Ken Brennan Corporate       60623      Chicago     Illinois
    ## 4 JO-152801406    Jas O'Carroll  Consumer       19120 Philadelphia Pennsylvania
    ## 5 HG-149651402    Henry Goldwyn Corporate       75150     Mesquite        Texas
    ##         Country     Region Market  Product_ID        Category Sub_Category
    ## 1 United States Central US   USCA OFF-AP-4739 Office Supplies   Appliances
    ## 2 United States Central US   USCA OFF-BI-2935 Office Supplies      Binders
    ## 3 United States Central US   USCA OFF-BI-3268 Office Supplies      Binders
    ## 4 United States Eastern US   USCA OFF-BI-3318 Office Supplies      Binders
    ## 5 United States Central US   USCA OFF-BI-2880 Office Supplies      Binders
    ##                                                                 Product_Name
    ## 1 Hoover Replacement Belt for Commercial Guardsman Heavy-Duty Upright Vacuum
    ## 2                                   Acco Suede Grain Vinyl Round Ring Binder
    ## 3                         Avery Durable Slant Ring Binders With Label Holder
    ## 4                                              Avery Round Ring Poly Binders
    ## 5                                                          Acco 3-Hole Punch
    ##   Sales Quantity Discount Profit Shipping_Cost Order_Priority Low_Priority
    ## 1  0.44        1      0.8  -1.11          1.01         Medium        FALSE
    ## 2  0.56        1      0.8  -0.95          1.08         Medium        FALSE
    ## 3  0.84        1      0.8  -1.34          1.06         Medium        FALSE
    ## 4  0.85        1      0.7  -0.60          1.10           High        FALSE
    ## 5  0.88        1      0.8  -1.40          1.09           High        FALSE
    ##   High_Shipping Discounted_US
    ## 1         FALSE          TRUE
    ## 2         FALSE          TRUE
    ## 3         FALSE          TRUE
    ## 4         FALSE          TRUE
    ## 5         FALSE          TRUE

</details>

{::options parse_block_html='false'/} *Hint:* Do not wrap the column
name in quotations.

</div>

### 4.7 Summarizing variables with `summarise()`

The `summarise()` function synthesizes information into a data frame
with information like totals, averages, medians, and so on.

- `summarise()` takes an unlimited number of parameters, where each
  parameter will appear as a column. <br>

<div class="task-box" markdown="1">

⭐ <u>Task 4.7-1</u>

**Preview statistics**

Preview the mean sales values and mean discount values in the discounted
US purchases data using the `summarise()` function.

- parameter 1: `columnName = mean(column)`
- another parameter: `columnName2 = mean(another column)`

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#Only purchases made in the US with discounts
discountedUSPurchases %>% 
   #average sale price and average discount
   summarise(meanSales = mean(Sales), meanDiscount = mean(Discount))%>%
      #finish the command with view() to preview this
      view() 

#To retrieve this data later, assign this command to a new variable.
```

</details>

{::options parse_block_html='false'/}

*Hint:* Both spellings, `summarize` or `summarise`, will work.

</div>

### 4.8 Analyzing groups with `group_by()`

Let’s say we wanted to know how profitable each US city is.

We can get the average profit, but grouped by US city.

From this, we can sort by profit to see what the most and least
profitable cities are.

<div class="task-box" markdown="1">

⭐ <u>Task 4.8-1</u>

**Create a data frame**

Create a data frame of US Cities and their average profit for each.

- You will use the `discountedUSPurchases` data frame to create this
  *new* data frame.
- Name the new data frame `USCityProfits`.
- You will use `group_by()` with `City`, where each row will be a city.
- You will use `summarise()` function to get the summary statistics for
  each city.
- The statistic you will be summarizing total `Profit` values on
  purchases made in the US where the items have been discounted.

**Do not create a new variable using `head(5)`**

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
#Only purchases made in the US with discounts
USCityProfits <- discountedUSPurchases %>% 
      group_by(City) %>% # group by city purchase was made in
      summarise(totalProfit = sum(Profit)) # average profit for each city
```

</details>

{::options parse_block_html='false'/}

</div>

The table will be sorted by city, alphabetically

You can use the functions you just learned to review this new data
frame.

⭐ **Sort the table by `Profit` using the `arrange()` function to order
it by the lowest profitable city to the highest profitable city.**

<br>

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
USCityProfits <- USCityProfits %>% arrange(totalProfit)
```

</details>

{::options parse_block_html='false'/}

<br>

⭐ **View the 5 least profitable cities.** <br>

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
USCityProfits <- USCityProfits %>% arrange(sum(totalProfit))
  
# Least profitable are at the top of our data frame, since `arrange()` puts data in ascending order by default. 
USCityProfits %>% head(5)
```

    ## # A tibble: 5 × 2
    ##   City         totalProfit
    ##   <chr>              <dbl>
    ## 1 Philadelphia     -13838.
    ## 2 Houston          -10153.
    ## 3 San Antonio       -7299.
    ## 4 Lancaster         -7243.
    ## 5 Chicago           -6655.

</details>

{::options parse_block_html='false'/}

⭐ **View the 5 most profitable cities.**

Use `tail()` to get the last 5 rows of a data frame.

{::options parse_block_html='true' /}
<details>
<summary>
Check your code
</summary>

``` r
USCityProfits <- USCityProfits %>% arrange(totalProfit)
  
# Most profitable are at the end of our data frame
USCityProfits %>% tail(5)
```

    ## # A tibble: 5 × 2
    ##   City          totalProfit
    ##   <chr>               <dbl>
    ## 1 San Diego           2895.
    ## 2 San Francisco       7067.
    ## 3 Seattle             7452.
    ## 4 Los Angeles        12697.
    ## 5 New York City      16994.

</details>

{::options parse_block_html='false'/}

------------------------------------------------------------------------

:round_pushpin: Reminder! Save your work

------------------------------------------------------------------------

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

[NEXT STEP: Tidyverse and Data Manipulation](ggplot2-data.html){: .btn
.btn-blue }
