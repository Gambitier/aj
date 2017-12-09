-   [**Manipulating Vectors**](#manipulating-vectors)
    -   [**Selecting and displaying certain parts**](#selecting-and-displaying-certain-parts)
    -   [**Sorting and rearranging**](#sorting-and-rearranging)
        -   [**Sorting**](#sorting)
        -   [**Order**](#order)
        -   [**Rank**](#rank)
    -   [**Returning Logical Values**](#returning-logical-values)
-   [**Manipulating Matrix & Data Frame**](#manipulating-matrix-data-frame)
    -   [**Selecting & displyaing parts of matrix or data frame**](#selecting-displyaing-parts-of-matrix-or-data-frame)
        -   [**Selecting Parts Of Data Frame**](#selecting-parts-of-data-frame)
        -   [**Selecting Parts Of Matrix Object**](#selecting-parts-of-matrix-object)
    -   [**Sorting & rearranging parts of matrix or data frame**](#sorting-rearranging-parts-of-matrix-or-data-frame)
        -   [**1 Sorting & rearranging Matrix Objects**](#sorting-rearranging-matrix-objects)
        -   [**2 Sorting & rearranging data frames**](#sorting-rearranging-data-frames)
-   [**Manipulating Lists**](#manipulating-lists)
-   [**Viewing Objects within Objects**](#viewing-objects-within-objects)
    -   [**(I) Looking Inside Complicated Data Objects**](#i-looking-inside-complicated-data-objects)
    -   [**(II) Opening Complicated Data Objects**](#ii-opening-complicated-data-objects)
    -   [**(III) Quick Looks at Complicated Data Objects**](#iii-quick-looks-at-complicated-data-objects)
    -   [**(IV) Viewing and Setting Row & Column Names**](#iv-viewing-and-setting-row-column-names)
        -   [**Viewing row & column names**](#viewing-row-column-names)
        -   [**Setting row & column names**](#setting-row-column-names)
    -   [**(V) Rotating Data Tables**](#v-rotating-data-tables)

Data objects are the fundamental items that you work with in R. Carrying out analyses on your data and making sense of the results are the primary reasons you are using R.

When you collect data the first step is to get the data into R. After this you will want to look at your data, and perform summary statistics and other analyses on them. Although many analytical operations can be conducted on the data "as is," there will be many occasions when you will want to manipulate the data you have; you may want to reorder the data into a new and more informative manner,or you may want to extract certain parts of a complex data object for some further purpose.

**Manipulating Vectors**
------------------------

Vectors are essentially the building blocks of more complicated items. The main ways you can manipulate vectors are the following:

-   Selecting and displaying certain parts
-   Sorting and rearranging
-   Returning logical values

### **Selecting and displaying certain parts**

``` r
numbers = c(11,22,3,4,5,6,7,8,9,10,10,11)
```

-   **Shows the first to the third items.**

``` r
numbers[1:3]
```

    ## [1] 11 22  3

-   **showing all elements except first 4 elements**

``` r
numbers[-1:-4]
```

    ## [1]  5  6  7  8  9 10 10 11

-   **Shows the items listed in the c() part.**

``` r
numbers[c(1, 3, 4, 8)]
```

    ## [1] 11  3  4  8

-   **Shows items less than 5 or greater than 10.**

``` r
numbers[numbers < 5 | numbers > 10]
```

    ## [1] 11 22  3  4 11

-   **To see how many elements in the vector**

``` r
length(numbers)
```

    ## [1] 12

-   **you can use this, to get last six elements in vector**

``` r
numbers[(length(numbers)-5):length(numbers)]
```

    ## [1]  7  8  9 10 10 11

-   **To get maximum and minimum respectively**

``` r
max(numbers)
```

    ## [1] 22

``` r
min(numbers)
```

    ## [1] 3

-   **argument to 'which()' should be logical**

output gives index maximum number

``` r
which(numbers == max(numbers))
```

    ## [1] 2

-   **selecting elements with some specified interval, say 2, for that we use seq(start,end,interval) command**

``` r
seq(1,20,3)
```

    ## [1]  1  4  7 10 13 16 19

``` r
numbers[seq(1,length(numbers),2)]
```

    ## [1] 11  3  5  7  9 10

### **Sorting and rearranging**

``` r
numbers2 = scan(file = 'numbers2.txt', sep = ',')
numbers2
```

    ##  [1] 12 NA 14 56 NA 86 28 75 NA 19

#### **Sorting**

-   **sorting, NA items will be stripped out**

``` r
sort(numbers2) #na.last=NA is default
```

    ## [1] 12 14 19 28 56 75 86

**sorting in decending order**

``` r
sort(numbers2,decreasing = TRUE)
```

    ## [1] 86 75 56 28 19 14 12

-   **if you want to include NA items as well**

*puuting NA items to the end of list*

``` r
sort(numbers2,na.last = TRUE)
```

    ##  [1] 12 14 19 28 56 75 86 NA NA NA

*puuting NA items to the start of list*

``` r
sort(numbers2,na.last = FALSE)
```

    ##  [1] NA NA NA 12 14 19 28 56 75 86

#### **Order**

**You can get index/position using order command**

*if your data contains NA and you try to order the vector, you get weird output that makes no sense*

``` r
numbers2
```

    ##  [1] 12 NA 14 56 NA 86 28 75 NA 19

``` r
order(numbers2,na.last = TRUE) #na.last=true is default
```

    ##  [1]  1  3 10  7  4  8  6  2  5  9

*but if the data doesn't contain any NA values, suddenly ordering makes sense*

``` r
num = c(45,32,8,3,561,64)
num
```

    ## [1]  45  32   8   3 561  64

``` r
order(num)
```

    ## [1] 4 3 2 1 6 5

#### **Rank**

-   The rank() command is slightly different than order() command.
-   In the following example, the two 9 values are the 3rd and 4th largest value and by default they get shared rank of 3.5
-   The rank of NA values are last by default.(so,5.0 & 6.0)
-   ties.method = 'average' is default. other options include 'first' , 'max', 'random' etc.

``` r
numbers2 = scan(file = 'numbers2 - Copy.txt',sep = ',')
numbers2
```

    ## [1]  8  9  7 NA  9 NA

``` r
rank(numbers2,ties.method = 'average')
```

    ## [1] 2.0 3.5 1.0 5.0 3.5 6.0

**if you do not want NA items to get involved in ranking**

``` r
rank(numbers2,na.last = 'keep',ties.method = 'average')
```

    ## [1] 2.0 3.5 1.0  NA 3.5  NA

### **Returning Logical Values**

``` r
duplicated(numbers)
```

    ##  [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE
    ## [12]  TRUE

``` r
numbers>1 & numbers<8
```

    ##  [1] FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE
    ## [12] FALSE

``` r
numbers == 7
```

    ##  [1] FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE
    ## [12] FALSE

``` r
which.max(numbers)
```

    ## [1] 2

**Manipulating Matrix & Data Frame**
------------------------------------

### **Selecting & displyaing parts of matrix or data frame**

Like a vector, you can still use the square brackets when displaying a matrix or data frame, but now you need to specify two dimensions: object\[row, column\].

#### **Selecting Parts Of Data Frame**

``` r
df = read.csv(file = 'dataFrame.csv',header = TRUE)
head(df[,],n=3) #df[,] means all rows, all coumns
```

    ##   category length speed algae  no3 bod
    ## 1     cat1     20    12    40 2.25 200
    ## 2     cat2     21    13    45 2.15 180
    ## 3     cat3     22    14    50 1.75 160

``` r
df[3,3] # element @3rd row & 3rd column
```

    ## [1] 14

``` r
df[1,1:3] #first row, coulumns = 1 to 3
```

    ##   category length speed
    ## 1     cat1     20    12

``` r
df[1:2,1:3] #rows 1 to 2 & coulumns = 1 to 3 
```

    ##   category length speed
    ## 1     cat1     20    12
    ## 2     cat2     21    13

``` r
df[,1] #all rows in first column
```

    ## [1] cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9
    ## Levels: cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9

``` r
df[1,]  #all column in first rows
```

    ##   category length speed algae  no3 bod
    ## 1     cat1     20    12    40 2.25 200

``` r
df[c(1,2,5),-1] #elements from rows=(1,2,5), all col EXCEPT 1st
```

    ##   length speed algae  no3 bod
    ## 1     20    12    40 2.25 200
    ## 2     21    13    45 2.15 180
    ## 5     24    16    60 1.30 120

``` r
df[c(1,2,4),'no3'] #because columns have headers u can use it
```

    ## [1] 2.25 2.15 1.55

#### **Selecting Parts Of Matrix Object**

This works same as selecting parts from data frame.

``` r
matr = as.matrix(read.csv(file = 'dataFrame.csv',header = TRUE,row.names = 1))
head(matr,n=3)
```

    ##      length speed algae  no3 bod
    ## cat1     20    12    40 2.25 200
    ## cat2     21    13    45 2.15 180
    ## cat3     22    14    50 1.75 160

``` r
matr[2,]
```

    ## length  speed  algae    no3    bod 
    ##  21.00  13.00  45.00   2.15 180.00

``` r
matr[c('cat1','cat9','cat3'),]
```

    ##      length speed algae  no3 bod
    ## cat1     20    12    40 2.25 200
    ## cat9     28    20    80 0.30  40
    ## cat3     22    14    50 1.75 160

``` r
matr[1]
```

    ## [1] 20

### **Sorting & rearranging parts of matrix or data frame**

#### **1 Sorting & rearranging Matrix Objects**

You can use the sort(), order(), and rank() commands on your matrix.

*Remember that your matrix is essentially a single vector of data that contains information about how to split it up into rows and columns.*

-   **If you specify simply the matrix object you get results along the following lines:**

``` r
sort(matr)
```

    ##  [1]   0.30   0.55   0.80   1.05   1.30   1.55   1.75   2.15   2.25  12.00
    ## [11]  13.00  14.00  15.00  16.00  17.00  18.00  19.00  20.00  20.00  21.00
    ## [21]  22.00  23.00  24.00  25.00  26.00  27.00  28.00  40.00  40.00  45.00
    ## [31]  50.00  55.00  60.00  60.00  65.00  70.00  75.00  80.00  80.00 100.00
    ## [41] 120.00 140.00 160.00 180.00 200.00

``` r
order(matr)
```

    ##  [1] 36 35 34 33 32 31 30 29 28 10 11 12 13 14 15 16 17  1 18  2  3  4  5
    ## [24]  6  7  8  9 19 45 20 21 22 23 44 24 25 26 27 43 42 41 40 39 38 37

``` r
rank(matr)
```

    ##  [1] 18.5 20.0 21.0 22.0 23.0 24.0 25.0 26.0 27.0 10.0 11.0 12.0 13.0 14.0
    ## [15] 15.0 16.0 17.0 18.5 28.5 30.0 31.0 32.0 33.5 35.0 36.0 37.0 38.5  9.0
    ## [29]  8.0  7.0  6.0  5.0  4.0  3.0  2.0  1.0 45.0 44.0 43.0 42.0 41.0 40.0
    ## [43] 38.5 33.5 28.5

-   **If you want to sort, order, or rank rows or columns, you must specify them explicitly:**

``` r
sort(matr[,1])
```

    ## cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9 
    ##   20   21   22   23   24   25   26   27   28

``` r
order(matr[,1])
```

    ## [1] 1 2 3 4 5 6 7 8 9

``` r
rank(matr[,1])
```

    ## cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9 
    ##    1    2    3    4    5    6    7    8    9

#### **2 Sorting & rearranging data frames**

**You cannot perform a sort() command on an entire data frame, even if it is composed entirely of the same kind of data (that is, all numeric or all character).**

You simply get an error; the command needs to operate on a single vector. You can pick out a part of your data frame to run the sort() command.

``` r
sort(df[,'bod'])
```

    ## [1]  40  60  80 100 120 140 160 180 200

``` r
sort(df$bod)
```

    ## [1]  40  60  80 100 120 140 160 180 200

**Manipulating Lists**
----------------------

**The elements of a list need not all be vectors, so you should examine the structure of a list object carefully (use the str() command) before carrying out manipulations.**

``` r
list.obj = as.list(read.csv(file = 'dataFrame.csv',header = TRUE))
list.obj
```

    ## $category
    ## [1] cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9
    ## Levels: cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9
    ## 
    ## $length
    ## [1] 20 21 22 23 24 25 26 27 28
    ## 
    ## $speed
    ## [1] 12 13 14 15 16 17 18 19 20
    ## 
    ## $algae
    ## [1] 40 45 50 55 60 65 70 75 80
    ## 
    ## $no3
    ## [1] 2.25 2.15 1.75 1.55 1.30 1.05 0.80 0.55 0.30
    ## 
    ## $bod
    ## [1] 200 180 160 140 120 100  80  60  40

**When you have a list the square brackets give a different result compared to other data objects you have met.**

**The list is a onedimensional object, so you can use only a single value in the square brackets.**

``` r
list.obj[1]
```

    ## $category
    ## [1] cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9
    ## Levels: cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9

**You must use the $ in the name. This is the only way you can utilize the sort(), order(), or rank() commands on list items.**

``` r
sort(list.obj$bod)
```

    ## [1]  40  60  80 100 120 140 160 180 200

**Viewing Objects within Objects**
----------------------------------

When you create a list, matrix, or data frame you are bundling together several items. In matrix and data frame objects the items are all the same length (resulting in the rectangular object), but in a list object the items can be different lengths.

*Each of these objects can contain several items, but you may have noticed that these do not appear when you use the ls() command.*

-   Looking Inside Complicated Data Objects
-   Opening Complicated Data Objects
-   Quick Looks at Complicated Data Objects
-   Viewing and Setting Names
-   Rotating Data Tables

### **(I) Looking Inside Complicated Data Objects**

To look at specific column,you use $ after object name to select what you want.

**Works With All Data Objects Except Matrix**

``` r
df$category
```

    ## [1] cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9
    ## Levels: cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9

``` r
list.obj$bod[1:4]
```

    ## [1] 200 180 160 140

**If you try this with a matrix, however, you get a Error:**

     matr$length

    ## Error in matr$length : $ operator is invalid for atomic vectors

**This is because a matrix is essentially a single data item that has been displayed in rows and columns**

You can still extract parts of a matrix using the names of the columns, but you need a slightly different approach. You can use the column name in the square brackets like so:

``` r
matr[,'length']
```

    ## cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9 
    ##   20   21   22   23   24   25   26   27   28

### **(II) Opening Complicated Data Objects**

To see which items are available to R by using search()

``` r
head(search(),n=3)
```

    ## [1] ".GlobalEnv"       "package:stats"    "package:graphics"

To see list of objects available use ls()

``` r
head(ls())
```

    ## [1] "df"       "list.obj" "matr"     "num"      "numbers"  "numbers2"

**You can temporarily make the items within a data object available for R to "see" using the attach() command.**

``` r
attach(df)
```

so, lets see if it really worked or not

``` r
df$category
```

    ## [1] cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9
    ## Levels: cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9

after attaching it will be available to R(i.e you will beable to see object in the list when you fire search() command)

``` r
head(search(),n=3)
```

    ## [1] ".GlobalEnv"    "df"            "package:stats"

But it doesn't mean the entities inside objects(i.e rows or columns) will be considered as separate objects (e.g df$category will not be considered as separate object). You can see it using ls()

``` r
head(ls())
```

    ## [1] "df"       "list.obj" "matr"     "num"      "numbers"  "numbers2"

**once you are done with data object you should detach() it. It will remove object from list of available items to R**

``` r
detach(df)
```

**attach() only works for lists, data frames and environments**

    attach(matr)

    Error in attach(matr) : 
      'attach' only works for lists, data frames and environments

You can also use a with() command that attaches the data only for short period, while you perform a single command.

For fairly short commands the $ is generally useful, but when you encounter long and more complicated commands, using with() can save quite a bit of typing.

``` r
with(df,length)
```

    ## [1] 20 21 22 23 24 25 26 27 28

``` r
with(list.obj,sum(length))
```

    ## [1] 216

### **(III) Quick Looks at Complicated Data Objects**

It is useful to see what a data object consists of so that you can decide which columns or rows to utilize. You can simply type the name of an object, of course. However, this might produce a lot of output.

The list of command useful for this are: - str() :- to see what an object is comprised of - head() :- To see first few entries, default is n=5 - tail() :- To see last few entries, default is n=5 - summary() :- To look at some simple statistics about data.

We have already met these commands earlier except summary().

**The output you get depends on the type of object you have. **

-   **If you have a data frame, you can see some summary statistics like so:**

``` r
summary(df)
```

    ##     category     length       speed        algae         no3      
    ##  cat1   :1   Min.   :20   Min.   :12   Min.   :40   Min.   :0.30  
    ##  cat2   :1   1st Qu.:22   1st Qu.:14   1st Qu.:50   1st Qu.:0.80  
    ##  cat3   :1   Median :24   Median :16   Median :60   Median :1.30  
    ##  cat4   :1   Mean   :24   Mean   :16   Mean   :60   Mean   :1.30  
    ##  cat5   :1   3rd Qu.:26   3rd Qu.:18   3rd Qu.:70   3rd Qu.:1.75  
    ##  cat6   :1   Max.   :28   Max.   :20   Max.   :80   Max.   :2.25  
    ##  (Other):3                                                        
    ##       bod     
    ##  Min.   : 40  
    ##  1st Qu.: 80  
    ##  Median :120  
    ##  Mean   :120  
    ##  3rd Qu.:160  
    ##  Max.   :200  
    ## 

-   **summary() also works with matrix objects**

``` r
summary(matr)
```

    ##      length       speed        algae         no3            bod     
    ##  Min.   :20   Min.   :12   Min.   :40   Min.   :0.30   Min.   : 40  
    ##  1st Qu.:22   1st Qu.:14   1st Qu.:50   1st Qu.:0.80   1st Qu.: 80  
    ##  Median :24   Median :16   Median :60   Median :1.30   Median :120  
    ##  Mean   :24   Mean   :16   Mean   :60   Mean   :1.30   Mean   :120  
    ##  3rd Qu.:26   3rd Qu.:18   3rd Qu.:70   3rd Qu.:1.75   3rd Qu.:160  
    ##  Max.   :28   Max.   :20   Max.   :80   Max.   :2.25   Max.   :200

-   **If the object you are examining is a list, you are presented with a slightly simpler summary output:**

``` r
summary(list.obj)
```

    ##          Length Class  Mode   
    ## category 9      factor numeric
    ## length   9      -none- numeric
    ## speed    9      -none- numeric
    ## algae    9      -none- numeric
    ## no3      9      -none- numeric
    ## bod      9      -none- numeric

-   \*\*If the data are a simple vector, the output you get depends on the type of item. The following examples show the results for numeric data followed by character data & factor <data:**>

``` r
summary(df$length)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##      20      22      24      24      26      28

``` r
summary(as.character(df$category))
```

    ##    Length     Class      Mode 
    ##         9 character character

``` r
summary(df$category)
```

    ## cat1 cat2 cat3 cat4 cat5 cat6 cat7 cat8 cat9 
    ##    1    1    1    1    1    1    1    1    1

### **(IV) Viewing and Setting Row & Column Names**

**NOTE:** *of course, setting & viewing row names for list object doesn't make sense. So when it comes to commands related to row, they won't work with list objects.*

#### **Viewing row & column names**

**(1) names(NameOfObject)**

-   shows names of columns
-   works with list & data frame
-   doesn't work with matrix

**(2) colnames(NameOfObject) & rownames(NameOfObject) & row.names(NameOfObject)**

-   shows names of columns & rows & rows respectively
-   works with matrix & data frame
-   doesn't work with list

**(3) dimnames(NameOfObject)**

-   shows names of both rows& columns
-   works with matrix & data frame
-   doesn't work with list

*note double brackets \[\[1\]\] ,\[\[2\]\] shown in output are used to differentiate between row & column names respectively*

``` r
dimnames(df) 
```

    ## [[1]]
    ## [1] "1" "2" "3" "4" "5" "6" "7" "8" "9"
    ## 
    ## [[2]]
    ## [1] "category" "length"   "speed"    "algae"    "no3"      "bod"

#### **Setting row & column names**

Same command mentioned earlier can be used to set names as well. Here are some examples.

\*\*Remember names() doen't work for matrix

``` r
my.row.names = c('catg1','catg2','catg3','catg4','catg5','catg6','catg7','catg8','catg9')

my.col.names = c('col1','col2','col3','col4','col5')

row.names(matr) = my.row.names #alternative: rownames() & works with data frames as well

colnames(matr) = my.col.names #alternative: colnames() & works with data frames,list as well
```

**Alternatively you can set names for both rows and columns at the same time using dimnames()**

note how list() command is used to make list of row & column names.

``` r
dimnames(matr) = list(my.row.names,my.col.names) #setting names

dimnames(matr) #showing result
```

    ## [[1]]
    ## [1] "catg1" "catg2" "catg3" "catg4" "catg5" "catg6" "catg7" "catg8" "catg9"
    ## 
    ## [[2]]
    ## [1] "col1" "col2" "col3" "col4" "col5"

### **(V) Rotating Data Tables**

You can easily rotate a frame or a matrix so that the rows become the columns and the columns become the rows. To do this you use the t() command; think of it as short for transpose.

**works with every object type list, vector, data frame, marix.**

``` r
t(matr)
```

    ##       catg1  catg2  catg3  catg4 catg5  catg6 catg7 catg8 catg9
    ## col1  20.00  21.00  22.00  23.00  24.0  25.00  26.0 27.00  28.0
    ## col2  12.00  13.00  14.00  15.00  16.0  17.00  18.0 19.00  20.0
    ## col3  40.00  45.00  50.00  55.00  60.0  65.00  70.0 75.00  80.0
    ## col4   2.25   2.15   1.75   1.55   1.3   1.05   0.8  0.55   0.3
    ## col5 200.00 180.00 160.00 140.00 120.0 100.00  80.0 60.00  40.0
