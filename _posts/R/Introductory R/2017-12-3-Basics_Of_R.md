---
layout: page
title: Basics Of R
published: true
category: R Tutorials
tags: R 
sitemap: true
author: "AKASH JADHAV"
---

R is more than just a program that does statistics. It is a sophisticated computer language and environment for statistical computing and graphics. R is available from the R-Project for Statistical Computing website (www.r-project.org), and following is some of its introductory material:

R is an open-source (GPL) statistical environment modeled after S and S-Plus. The S language was developed in the late 1980s at AT&T labs. The R project was started by Robert Gentleman and Ross Ihaka (hence the name, R) of the Statistics Department of the University of Auckland in 1995. It has quickly gained a widespread audience.

It is currently maintained by the R core-development team, a hard-working, international team of volunteer developers. The R project webpage is the main site for information on R. At this site are directions for obtaining the software, accompanying packages, and other sources of documentation.

R is a powerful statistical program but it is first and foremost a programming language. Many routines have been written for R by people all over the world and made freely available from the R project website as "packages."


-   [**The Help Command in R**](#the-help-command-in-r)
-   [**Command Packages**](#command-packages)
-   [**Using R like a calculator**](#using-r-like-a-calculator)
-   [**Named Objects**](#named-objects)
    -   [**Assigning Named Objects**](#assigning-named-objects)
    -   [**Viewing Named Object's Value**](#viewing-named-objects-value)
    -   [**Viewing List Of All Objects**](#viewing-list-of-all-objects)
    -   [**Viewing Only Matching Objects**](#viewing-only-matching-objects)
    -   [**Removing Objects From R**](#removing-objects-from-r)
-   [**Reading & Getting Data Into R**](#reading-getting-data-into-r)
    -   [**Using Combine command**](#using-combine-command)
        -   [**Entering Numerical Data**](#entering-numerical-data)
        -   [**Entering Text Data Items**](#entering-text-data-items)
    -   [**Using Scan Command: *scan()* **](#using-scan-command-scan)
        -   [**Entering Numerical Data**](#entering-numerical-data-1)
        -   [**Entering Text Data Items**](#entering-text-data-items-1)
        -   [**Reading a File From Disk**](#reading-a-file-from-disk)
    -   [**Reading Bigger Data Files**](#reading-bigger-data-files)
-   [**Data Types In R**](#data-types-in-r)
    -   [**Number Data**](#number-data)
    -   [**Text Items**](#text-items)
-   [**Converting Between Number & Text Data**](#converting-between-number-text-data)
    -   [**character to Factor**](#character-to-factor)
    -   [**Factor to character**](#factor-to-character)
    -   [**Integer to Numeric**](#integer-to-numeric)
    -   [**Character to Numeric**](#character-to-numeric)
    -   [**Character to Integer**](#character-to-integer)
    -   [**Numeric to Integer**](#numeric-to-integer)
    -   [**Factor to Numeric**](#factor-to-numeric)
    -   [**Misc**](#misc)
-   [**Data Structures of Items In R**](#data-structures-of-items-in-r)
    -   [**Vector Items**](#vector-items)
    -   [**Data Frames**](#data-frames)
    -   [**Matrix Objects**](#matrix-objects)
    -   [**List Objects**](#list-objects)
-   [**Examining Data Structure**](#examining-data-structure)


**The Help Command in R**
-------------------------

When getting started, you can get the help by firing command:

    help.start()

R contains a lot of built-in help. The basic command to bring up help is:

    help(topic) //replace topic with name of item you want help on.

    ?topic //Alternative way to achieve the same

**Command Packages**
--------------------

The R program is built from series of modules, called packages. These packages are libraries of commands we use. When you first start R, several packages are loaded on your computer and become ready to use.

you can see what packages are available to you.

``` r
search()
```

    ## [1] ".GlobalEnv"        "package:stats"     "package:graphics" 
    ## [4] "package:grDevices" "package:utils"     "package:datasets" 
    ## [7] "package:methods"   "Autoloads"         "package:base"

several other packages are ready installed but not automatically loaded and immediately available. To see list of such packages:

    installed.packages()

To install extra package:

    install.packages('PACK_Name')

TO use packages you must load them as required

    library(PACK_Name)

To Remove/Unload Packages use following commad, but note that when you remove package, a package is not removed from your local disk; you can still use the *library()* command to get it back when required.

    detach(PACK_Name)

**Using R like a calculator**
-----------------------------

``` r
3 * pi + 78 - sqrt(9) * (2^2) + factorial(3) + 0.00458
```

    ## [1] 81.42936

**Named Objects**
-----------------

R uses the term 'named object' to denote variable's name.

### **Assigning Named Objects**

Assignment to named object can be done using any following method

``` r
NamedObject = 45

NamedObject <- 45

45 -> NamedObject
```

### **Viewing Named Object's Value**

``` r
NamedObject
```

    ## [1] 45

### **Viewing List Of All Objects**

You can view list of all objects created using **ls()** command.

So, lets create few more named objects

``` r
beta = 1
bf  = 45*2
bird = 48.5
envs = 8
aebet = 53
```

Now lets see all objects created..

``` r
ls()
```

    ## [1] "aebet"       "beta"        "bf"          "bird"        "envs"       
    ## [6] "NamedObject"

### **Viewing Only Matching Objects**

You may want to look for specific objects created so far. This can be done by giving R a search pattern to match.

-   **Objects conatining letter 'b'**

``` r
ls(pattern = 'b') 
```

    ## [1] "aebet"       "beta"        "bf"          "bird"        "NamedObject"

-   **Objects conatining letter 'be'**

``` r
ls(pattern = 'be') 
```

    ## [1] "aebet" "beta"

-   **Objects beginning with 'be'**

``` r
ls(pattern = '^be') 
```

    ## [1] "beta"

-   **Objects beginning with 'b' or 'e'**

``` r
ls(pattern = '^b|^e') 
```

    ## [1] "beta" "bf"   "bird" "envs"

-   **Objects ending with 'b'**

The result of following example shows R didn't find any object ending with letter 'b', ehich is true!!

``` r
ls(pattern = 'b$')
```

    ## character(0)

-   **Searching object with wildcard pattern**

You can use period('.') as a wildcard and R will match any character:

``` r
ls(pattern = 'b...t')
```

    ## [1] "NamedObject"

### **Removing Objects From R**

You can remove objects from memory permanently using **rm()** or **remove()** command. Inside those braces you have to mention name of object to remove.

If you want to remove all objects staring with letter 'b'

``` r
rm(list = ls(pattern = '^b'))
```

to see its result: indeed it removed all objects starting with b.

``` r
ls()
```

    ## [1] "aebet"       "envs"        "NamedObject"

**Reading & Getting Data Into R**
---------------------------------

-   Using Combine Command: *c()*

-   Using Scan Command: *scan()*

-   Reading Bigger Data Files: *read.csv()*,*read.table* etc.

### **Using Combine command**

This is the simplest method to create list of values. This command is useful when you don't have very large samples.

#### **Entering Numerical Data**

``` r
data1 = c(2,45,65,78,86,48)
```

R always try to set same precision for every item in the list.

``` r
float.data = c(data1 , 45.2, 15.23)

float.data
```

    ## [1]  2.00 45.00 65.00 78.00 86.00 48.00 45.20 15.23

#### **Entering Text Data Items**

If the data is not numerical, you simply use single or double quotes to differentiate them from numbers.

``` r
text.data <- c("Monkey", 'lion', "Dog", 'cat' )
```

If you try to mix up text data with numerical, R converts all of them to characters.

``` r
mixed.data = c(float.data , text.data)

mixed.data
```

    ##  [1] "2"      "45"     "65"     "78"     "86"     "48"     "45.2"  
    ##  [8] "15.23"  "Monkey" "lion"   "Dog"    "cat"

### **Using Scan Command: *scan()* **

This command prompts user to enter data.

#### **Entering Numerical Data**

    my.data = scan()

#### **Entering Text Data Items**

You must tell R to expect that items typed in are characters, not numbers; to do this you need to add *what = 'character'* part in parantheses.

    days.data = scan(what = 'char')

If you are copying data from somewhere which is separated by ',' and paste it when R prompts to enter data, you need to tell R that data items are separated by comma ','.

following code in the snippet will read numerical data separated by ','

    numbers = scan(sep = ',')

#### **Reading a File From Disk**

To read file from disk you need to include *file = 'FileName'* to coomand.

``` r
food.menu = scan(file = 'food.csv' ,  sep = ',' , what = 'char')
```

Note that you can use simply fileName(e.g 'food.csv') only when that file exist in the workung directory. Otherwise, you have to mention full path of the required file.

head() command shows first few values in the object

``` r
head(food.menu)
```

    ## [1] "Item"          "Category"      "Price"         "Profit"       
    ## [5] "Actual Profit" "Calories"

To know current working directory

    getwd()

To set working directory

    setwd('FULL_PATH')

To list files/folders in the directory:

-   *all.files = TRUE* will force to show hidden file also in the directory.

<!-- -->

    dir(all.files = TRUE)

    list.files(all.files = TRUE)

### **Reading Bigger Data Files**

The scan() command is useful to read a simple vector. To read large amount of data you need to use

``` r
menu.card = read.csv(file = 'food.csv',  header = TRUE, sep = ',') 

head(menu.card)
```

    ##            Item  Category  Price Profit Actual.Profit Calories
    ## 1          Beer Beverages $4.00     50%        $2.00       200
    ## 2     Hamburger  Hot Food $3.00     67%        $2.00        NA
    ## 3       Popcorn  Hot Food $5.00     80%        $4.00        NA
    ## 4         Pizza  Hot Food $2.00     25%        $0.50        NA
    ## 5 Bottled Water Beverages           83%        $2.50        NA
    ## 6       Hot Dog  Hot Food           67%        $1.00        NA

*header = TRUE*,the default, reads first row of csv file & sets as name for each coloumn.

In 'caloreis' column, note there are some values as **NA**. These NA values indicate there are some missing values. R always pads out the shorter samples using NA to produce a rectangulr object,called *data frame*.

R recognizes NA as a special kind of object. It is important to know when your data contains NA items and what to do when you encouter them.

There are many alternative commands, each for specific purpose having their own defaults. You can get help from R about them as:

    ?read.csv

    ?read.csv2

    ?read.delim

    ?read.table

**Data Types In R**
-------------------

Your data item can exist in one of two forms, R regards them as *numeric* or *character*. - Number Data - Text Items

### **Number Data**

-   Whole numbers : integer

-   Decimal numbers : numeric

-   But sample containing both integer & decimals, will be treated as numeric by R.

### **Text Items**

R recognizes two sorts of text data items: - **Character Values**: Denoted by quotes

``` r
text.data
```

    ## [1] "Monkey" "lion"   "Dog"    "cat"

-   **Factors**: They are not in quotes and R shows an additional line showing how many different things are there in the list.

``` r
head(n=30,menu.card$Category)
```

    ##  [1] Beverages     Hot Food      Hot Food      Hot Food      Beverages    
    ##  [6] Hot Food      Frozen Treats Beverages     Candy         Hot Food     
    ## [11] Beverages     Hot Food      Candy         Frozen Treats Hot Food     
    ## [16] Hot Food      Beverages     Beverages     Beverages     Hot Food     
    ## [21] Candy         Hot Food      Hot Food      Hot Food      Hot Food     
    ## [26] Frozen Treats Candy         Hot Food      Beverages     Frozen Treats
    ## Levels:  Beverages Candy Frozen Treats Hot Food

*Levels: Beverages Candy Frozen Treats Hot Food*

this indicates there are five different items in the list.

*We use $ after data frame to select specific coloumn...So menu.card $ Category*

i.e category column in this data frame was read as factor and not as character. So, to force R to read it as character we include *as.is=COL\_no* in the command *read.csv()*

``` r
menuCard.asItIs = read.csv(file = 'food.csv',as.is =c(2,1,3), header = TRUE )

head(menuCard.asItIs$Category)
```

    ## [1] "Beverages" "Hot Food"  "Hot Food"  "Hot Food"  "Beverages" "Hot Food"

Now note they are displayed in quotes.!! That means column category hass been read as character.

**Converting Between Number & Text Data**
-----------------------------------------

### **character to Factor**

``` r
head(as.factor(menuCard.asItIs$Category))
```

    ## [1] Beverages Hot Food  Hot Food  Hot Food  Beverages Hot Food 
    ## Levels:  Beverages Candy Frozen Treats Hot Food

### **Factor to character**

``` r
numbers.char = as.character(data1)

numbers.char
```

    ## [1] "2"  "45" "65" "78" "86" "48"

### **Integer to Numeric**

Once the decimal places are lost/not\_given, they can't be recovered. So, this case of converting has no effect.

``` r
as.numeric(data1)
```

    ## [1]  2 45 65 78 86 48

but it will make sense in following case

### **Character to Numeric**

THIS WORKS FINE ONLY IF TEXT IS SENSIBLE.

``` r
as.numeric(numbers.char)
```

    ## [1]  2 45 65 78 86 48

### **Character to Integer**

``` r
as.integer(numbers.char)
```

    ## [1]  2 45 65 78 86 48

### **Numeric to Integer**

CAUTION: DECIMAL PLACES WILL BE LOST FOREVER & CAN'T BE RECOVERED

``` r
as.integer(float.data)
```

    ## [1]  2 45 65 78 86 48 45 15

### **Factor to Numeric**

SURPRISING BUT POTENTIALLY USEFUL RESULT.

note the resulting numbers relate directly to different factors you have.!!

``` r
head(as.numeric(menu.card$Category))
```

    ## [1] 2 5 5 5 2 5

### **Misc**

**N.B**

If you try to convert something that really doesn't make sense, R will gives a warning and produces NA values

``` r
text.data
```

    ## [1] "Monkey" "lion"   "Dog"    "cat"

now lets try to convert from character to numeric

``` r
as.numeric(text.data )
```

    ## Warning: NAs introduced by coercion

    ## [1] NA NA NA NA

to get something useful

``` r
as.numeric(as.factor(text.data))
```

    ## [1] 4 3 2 1

**Data Structures of Items In R**
---------------------------------

Your data can exist as numerical or character data. However, these data items can also be constructed and put together in a variety of ways. This section looks at these different structures:

-   Vector
-   Data Frame
-   Matrix
-   List

### **Vector Items**

-   one dimensional objects.
-   Vector is same as term array in other programming languages.
-   It is smallest unit of data structure.

``` r
text.data
```

    ## [1] "Monkey" "lion"   "Dog"    "cat"

### **Data Frames**

-   Two Dimensional object.
-   It has coulumns & rows.
-   Each column can be separate type of data.
-   All data frames are rectangular.
-   So, R will pad out any short column with NA

``` r
head(menu.card, n=3)
```

    ##        Item  Category  Price Profit Actual.Profit Calories
    ## 1      Beer Beverages $4.00     50%        $2.00       200
    ## 2 Hamburger  Hot Food $3.00     67%        $2.00        NA
    ## 3   Popcorn  Hot Food $5.00     80%        $4.00        NA

### **Matrix Objects**

-   Matrix is also two dimensional object.
-   At first glance it looks like data frame
-   But all columns must be of same type i.e either numeric or character or factors etc.
-   In R for both data frames and matrix, duplicate row names are not allowed.

``` r
mat.object = as.matrix(read.csv(file = 'matrix.csv' , header = TRUE , row.names = 1))

head(mat.object, n=3)
```

    ##               hotel.1 hotel.2 Chalories hotel.3 lodge
    ## Beer              280     200       320     200   280
    ## Chocolate Bar     300     255       200     255   300
    ## Hamburger         560     320       265     320   560

``` r
class(mat.object)
```

    ## [1] "matrix"

### **List Objects**

-   A list is a series of items bundled together to form a single object.
-   when you look at it you see each vector listed separately along with its name, which is prefixed with a dollor sign.
-   The list is flexible object but also harder to deal with.
-   \*\*list objects are helpful where you have objects of varying length that you want to tie togrther\*

``` r
list.obj = as.list(read.csv(file = 'food2.csv',header= TRUE))
list.obj
```

    ## $Item
    ## [1] Beer      Hamburger Popcorn   Pizza     Pizza     Beer      Soda     
    ## [8] Beer      Hamburger
    ## Levels: Beer Hamburger Pizza Popcorn Soda
    ## 
    ## $Category
    ## [1] Beverages Hot Food  Hot Food  Hot Food  Hot Food  Beverages Beverages
    ## [8] Beverages Hot Food 
    ## Levels: Beverages Hot Food
    ## 
    ## $Price
    ## [1] $4.00  $3.00  $5.00  $2.00  $2.00  $4.00  $2.50  $4.00  $3.00 
    ## Levels: $2.00  $2.50  $3.00  $4.00  $5.00 
    ## 
    ## $no
    ## [1] 1 2 3 4 5 6 7 8 9

**Examining Data Structure**
----------------------------

-   To Examine Data Structure, you can use **str()** command.

``` r
str(list.obj)
```

    ## List of 4
    ##  $ Item    : Factor w/ 5 levels "Beer","Hamburger",..: 1 2 4 3 3 1 5 1 2
    ##  $ Category: Factor w/ 2 levels "Beverages","Hot Food": 1 2 2 2 2 1 1 1 2
    ##  $ Price   : Factor w/ 5 levels "$2.00 ","$2.50 ",..: 4 3 5 1 1 4 2 4 3
    ##  $ no      : int [1:9] 1 2 3 4 5 6 7 8 9

``` r
str(text.data)
```

    ##  chr [1:4] "Monkey" "lion" "Dog" "cat"

``` r
str(menu.card)
```

    ## 'data.frame':    199 obs. of  6 variables:
    ##  $ Item         : Factor w/ 13 levels "","Beer","Bottled Water",..: 2 7 12 11 3 8 5 13 4 7 ...
    ##  $ Category     : Factor w/ 5 levels "","Beverages",..: 2 5 5 5 2 5 4 2 3 5 ...
    ##  $ Price        : Factor w/ 7 levels "","$1.50 ","$2.00 ",..: 6 5 7 3 1 1 1 1 1 5 ...
    ##  $ Profit       : Factor w/ 7 levels "","25%","50%",..: 3 4 6 2 7 4 3 6 5 4 ...
    ##  $ Actual.Profit: Factor w/ 7 levels "","$0.50 ","$1.00 ",..: 5 5 7 2 6 3 4 5 4 5 ...
    ##  $ Calories     : int  200 NA NA NA NA NA NA NA 255 320 ...

-   **you can obtain only Type of object by using the class() command.**

``` r
class(list.obj)
```

    ## [1] "list"

``` r
class(text.data)
```

    ## [1] "character"

``` r
class(menu.card)
```

    ## [1] "data.frame"
