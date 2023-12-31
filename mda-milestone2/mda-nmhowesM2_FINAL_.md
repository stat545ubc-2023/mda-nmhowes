Mini Data Analysis Milestone 2
================

*To complete this milestone, you can either edit [this `.rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-2.Rmd)
directly. Fill in the sections that are commented out with
`<!--- start your work here--->`. When you are done, make sure to knit
to an `.md` file by changing the output in the YAML header to
`github_document`, before submitting a tagged release on canvas.*

# Welcome to the rest of your mini data analysis project!

In Milestone 1, you explored your data. and came up with research
questions. This time, we will finish up our mini data analysis and
obtain results for your data by:

- Making summary tables and graphs
- Manipulating special data types in R: factors and/or dates and times.
- Fitting a model object to your data, and extract a result.
- Reading and writing data as separate files.

We will also explore more in depth the concept of *tidy data.*

**NOTE**: The main purpose of the mini data analysis is to integrate
what you learn in class in an analysis. Although each milestone provides
a framework for you to conduct your analysis, it’s possible that you
might find the instructions too rigid for your data set. If this is the
case, you may deviate from the instructions – just make sure you’re
demonstrating a wide range of tools and techniques taught in this class.

# Instructions

**To complete this milestone**, edit [this very `.Rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-2.Rmd)
directly. Fill in the sections that are tagged with
`<!--- start your work here--->`.

**To submit this milestone**, make sure to knit this `.Rmd` file to an
`.md` file by changing the YAML output settings from
`output: html_document` to `output: github_document`. Commit and push
all of your work to your mini-analysis GitHub repository, and tag a
release on GitHub. Then, submit a link to your tagged release on canvas.

**Points**: This milestone is worth 50 points: 45 for your analysis, and
5 for overall reproducibility, cleanliness, and coherence of the Github
submission.

**Research Questions**: In Milestone 1, you chose two research questions
to focus on. Wherever realistic, your work in this milestone should
relate to these research questions whenever we ask for justification
behind your work. In the case that some tasks in this milestone don’t
align well with one of your research questions, feel free to discuss
your results in the context of a different research question.

# Learning Objectives

By the end of this milestone, you should:

- Understand what *tidy* data is, and how to create it using `tidyr`.
- Generate a reproducible and clear report using R Markdown.
- Manipulating special data types in R: factors and/or dates and times.
- Fitting a model object to your data, and extract a result.
- Reading and writing data as separate files.

# Setup

Begin by loading your data and the tidyverse package below:

``` r
library(datateachr) # <- might contain the data you picked!
library(tidyverse)
```

    ## Warning: package 'tidyverse' was built under R version 4.2.3

    ## Warning: package 'ggplot2' was built under R version 4.2.3

    ## Warning: package 'tibble' was built under R version 4.2.3

    ## Warning: package 'tidyr' was built under R version 4.2.3

    ## Warning: package 'readr' was built under R version 4.2.3

    ## Warning: package 'purrr' was built under R version 4.2.3

    ## Warning: package 'dplyr' was built under R version 4.2.3

    ## Warning: package 'stringr' was built under R version 4.2.3

    ## Warning: package 'forcats' was built under R version 4.2.3

    ## Warning: package 'lubridate' was built under R version 4.2.3

# Task 1: Process and summarize your data

From milestone 1, you should have an idea of the basic structure of your
dataset (e.g. number of rows and columns, class types, etc.). Here, we
will start investigating your data more in-depth using various data
manipulation functions.

### 1.1 (1 point)

First, write out the 4 research questions you defined in milestone 1
were. This will guide your work through milestone 2:

<!-------------------------- Start your work below ---------------------------->

1.  Are larger trees (diameter) in Kitsilano typically seen on the
    curb?\*
2.  Across the various neighbourhoods are the widest trees all the same
    species?
3.  Do most trees that are larger in diameter mean they are also taller?
4.  What neighborhood has the highest amount of tall trees?
    <!----------------------------------------------------------------------------->

Here, we will investigate your data using various data manipulation and
graphing functions.

### 1.2 (8 points)

Now, for each of your four research questions, choose one task from
options 1-4 (summarizing), and one other task from 4-8 (graphing). You
should have 2 tasks done for each research question (8 total). Make sure
it makes sense to do them! (e.g. don’t use a numerical variables for a
task that needs a categorical variable.). Comment on why each task helps
(or doesn’t!) answer the corresponding research question.

Ensure that the output of each operation is printed!

Also make sure that you’re using dplyr and ggplot2 rather than base R.
Outside of this project, you may find that you prefer using base R
functions for certain tasks, and that’s just fine! But part of this
project is for you to practice the tools we learned in class, which is
dplyr and ggplot2.

**Summarizing:**

1.  Compute the *range*, *mean*, and *two other * of **one numerical
    variable** across the groups of **one categorical variable** from
    your data.
2.  Compute the number of observations for at least one of your
    categorical variables. Do not use the function `table()`!
3.  Create a categorical variable with 3 or more groups from an existing
    numerical variable. You can use this new variable in the other
    tasks! *An example: age in years into “child, teen, adult, senior”.*
4.  Compute the proportion and counts in each category of one
    categorical variable across the groups of another categorical
    variable from your data. Do not use the function `table()`!

**Graphing:**

6.  Create a graph of your choosing, make one of the axes logarithmic,
    and format the axes labels so that they are “pretty” or easier to
    read.
7.  Make a graph where it makes sense to customize the alpha
    transparency.

Using variables and/or tables you made in one of the “Summarizing”
tasks:

8.  Create a graph that has at least two geom layers.
9.  Create 3 histograms, with each histogram having different sized
    bins. Pick the “best” one and explain why it is the best.

Make sure it’s clear what research question you are doing each operation
for!

# Tasks for “Are larger trees (diameter) in Kitsilano typically seen on the curb?”

# Summarizing Task

``` r
#Compute the number of observations for at least one of your categorical variables (curb)
#I would like to know how many trees are seen on the curb 
vancouver_trees %>%
  group_by(curb) %>%
  summarise(count = n())
```

    ## # A tibble: 2 × 2
    ##   curb   count
    ##   <chr>  <int>
    ## 1 N      12804
    ## 2 Y     133807

``` r
#This task found that there are 133, 807 trees that are seen on the curb and then I can further use a filter function to filter for large trees to finally solve my question. This information also tells me there are alot more trees on the curb oppose to not so I think in general the larger trees will be seen on the curb due to having initial unequal distributions of the trees. 
```

# Graphing Task

``` r
#Create a graph of your choosing, make one of the axes logarithmic, and format the axes labels so that they are "pretty" or easier to read
#I would like to roughly see where the largest trees are located 
library(ggplot2)
ggplot(vancouver_trees, aes(x = diameter, y = curb)) + 
  scale_x_continuous(trans = 'log10') +
  geom_point(size = 0.8, alpha = 0.5) + 
  labs(title= "Diameters of Trees on/off the Curb", x = "Diameter (m)", y = "Tree location on/off curb")
```

    ## Warning: Transformation introduced infinite values in continuous x-axis

![](mda-nmhowesM2_FINAL__files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
#This graph allows me to compare the diameters of the trees to where they are located either on/off the curb and from this graph I can see that the top couple largest trees are located on the curb. However due to the large amount of trees I can't determine where the highest density of trees are for both on and off the curb. 
```

# Tasks for “Across the various neighbourhoods are the widest trees all the same species?”

# Summarizing Task

``` r
#Compute the *range*, *mean*, and *two other * of **one numerical variable** across the groups of **one categorical variable** from your data.
#I would like to know the mean, median and range etc of the diameters of trees to help filter out trees if needed since there is so many and I just want to look for the largest trees in tree species
vancouver_trees %>% 
 group_by(species_name) %>%
 summarize(Mean = mean(diameter, na.rm=TRUE),
           Max = max(diameter, na.rm=TRUE),
           Range = (max(diameter)- min(diameter)),
           Median = median(diameter, na.rm=TRUE))
```

    ## # A tibble: 283 × 5
    ##    species_name    Mean   Max Range Median
    ##    <chr>          <dbl> <dbl> <dbl>  <dbl>
    ##  1 ABIES          12.9   35    33     12  
    ##  2 ACERIFOLIA   X 20.8   57    55     19  
    ##  3 ACUMINATA      10.9   28    26      7  
    ##  4 ACUTISSIMA      8.87  36    34      8.5
    ##  5 AILANTHIFOLIA  32     40    16     34  
    ##  6 ALBA           19.4   40    38.5   20.2
    ##  7 ALBA-SINENSIS   8.67  10     3      9  
    ##  8 ALNIFOLIA       5.23  20.2  18.2    5  
    ##  9 ALPINUM         8      8     0      8  
    ## 10 ALTISSIMA      15.9   21.5  18.5   19.5
    ## # ℹ 273 more rows

``` r
Mode <- function(x) {
  ux <- unique(x)
  ux[which.max(tabulate(match(x, ux)))]}


data <- vancouver_trees %>% 
        group_by(species_name) %>%
        summarize(Mode(diameter)) %>%
        print()
```

    ## # A tibble: 283 × 2
    ##    species_name   `Mode(diameter)`
    ##    <chr>                     <dbl>
    ##  1 ABIES                         3
    ##  2 ACERIFOLIA   X                3
    ##  3 ACUMINATA                     2
    ##  4 ACUTISSIMA                    3
    ##  5 AILANTHIFOLIA                27
    ##  6 ALBA                          3
    ##  7 ALBA-SINENSIS                 9
    ##  8 ALNIFOLIA                     3
    ##  9 ALPINUM                       8
    ## 10 ALTISSIMA                    19
    ## # ℹ 273 more rows

``` r
#These results allowed me to better understand the variety of tree heights there were and what the majority of trees looked like. However only finding these values makes it hard to find the species with the largest diameters and doesn't tell me where to find them. 
```

# Graphing Task

``` r
#Create a graph that has at least two geom layers.
#I want to find the species of the widest trees across different neighborhoods
outlier <- filter(vancouver_trees,diameter > 170)

ggplot(vancouver_trees, aes(x = diameter, y = neighbourhood_name)) +
     geom_point(size = 0.5, alpha = 0.5) +
     geom_text(data = outlier, aes(label = species_name)) +
    labs(title= "Diameters of trees across different neighbourhoods", x = "Diameter (m)", y = "Tree location")
```

![](mda-nmhowesM2_FINAL__files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
#This task allowed me to find the different species with the widest diameters and I found that they are all different species which was unexpected.
```

# Tasks for “Do most trees that are larger in diameter mean they are also taller?”

# Summarizing Task

``` r
#Create a categorical variable with 3 or more groups from an existing numerical variable. You can use this new variable in the other tasks! *An example: age in years into "child, teen, adult, senior".*
#I wanted to make a variable to make it easier to see what trees were considered having a high width
ST <- vancouver_trees%>%
  mutate(Tree_Width = case_when(diameter < 10 ~ 'low',diameter < 20 ~ 'med', diameter > 20 ~ 'high')) 

ST %>%
  select("tree_id", "diameter","Tree_Width")
```

    ## # A tibble: 146,611 × 3
    ##    tree_id diameter Tree_Width
    ##      <dbl>    <dbl> <chr>     
    ##  1  149556     10   med       
    ##  2  149563     10   med       
    ##  3  149579      4   low       
    ##  4  149590     18   med       
    ##  5  149604      9   low       
    ##  6  149616      5   low       
    ##  7  149617     15   med       
    ##  8  149618     14   med       
    ##  9  149619     16   med       
    ## 10  149625      7.5 low       
    ## # ℹ 146,601 more rows

``` r
#This task allows me to know which trees have a wide diameter however it doesn't tell me which trees are also taller and how they are related - I also selected for a few columns so the new column can be seen easier.
```

# Graphing Task

``` r
#Create a graph of your choosing, make one of the axes logarithmic, and format the axes labels so that they are "pretty" or easier to read
#I want to make a graph to see the relationship between the diameter and heights of trees
library(ggplot2)
ggplot(vancouver_trees, aes(x = diameter, y = height_range_id)) + 
  geom_point(size = 0.8, alpha = 0.5) + 
  scale_x_continuous(trans = 'log10') +
  labs(title= "Diameters and Heights of Trees", x = "Diameter (m)", y = "Height Range ID")  
```

    ## Warning: Transformation introduced infinite values in continuous x-axis

![](mda-nmhowesM2_FINAL__files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

``` r
#This graph makes it clear the tallest trees are not the largest in diameter however they are larger in diameter compared to the median diameter. However since there are so many trees it is not visible the number of trees at each height range. 
```

# Tasks for “What neighborhood has the highest amount of tall trees?

# Summarizing Task

``` r
#Compute the number of observations for at least one of your categorical variables. Do not use the function `table()`!
#I want to see what neighborhood has the highest amount of trees 
vancouver_trees %>%
  group_by(neighbourhood_name) %>%
  summarise(count = n())
```

    ## # A tibble: 22 × 2
    ##    neighbourhood_name       count
    ##    <chr>                    <int>
    ##  1 ARBUTUS-RIDGE             5169
    ##  2 DOWNTOWN                  5159
    ##  3 DUNBAR-SOUTHLANDS         9415
    ##  4 FAIRVIEW                  4002
    ##  5 GRANDVIEW-WOODLAND        6703
    ##  6 HASTINGS-SUNRISE         10547
    ##  7 KENSINGTON-CEDAR COTTAGE 11042
    ##  8 KERRISDALE                6936
    ##  9 KILLARNEY                 6148
    ## 10 KITSILANO                 8115
    ## # ℹ 12 more rows

``` r
#I found that the RENFREW-COLLINGWOOD neighborhood has the highest amount of trees being 1645778546 trees which helps solve part of my question, I would then just need to filter for the size of trees. 
```

# Graphing Task

``` r
#Create a graph that has at least two geom layers.
#I want to find some of the top neighborhoods with the highest amount of trees
trees <- as_tibble(vancouver_trees) %>% 
  count(neighbourhood_name, wt = tree_id)
  

ggplot(vancouver_trees, aes(x = neighbourhood_name, y = height_range_id)) +
  geom_violin()+
  geom_boxplot(width = 0.2) +
  scale_y_log10()+
  coord_flip() +
  theme_classic() +
  labs(title= "Heights of Trees across various neighbourhoods", x = "Neighbourhood Name", y = "Height Range ID") 
```

    ## Warning: Transformation introduced infinite values in continuous y-axis
    ## Transformation introduced infinite values in continuous y-axis

    ## Warning: Removed 214 rows containing non-finite values (`stat_ydensity()`).

    ## Warning: Removed 214 rows containing non-finite values (`stat_boxplot()`).

![](mda-nmhowesM2_FINAL__files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

``` r
#I found that there were multiple neighborhoods that contain trees with a height id of 10 being the highest however the graph doesn't make it clear the neighborhood with the the highest number of trees. 
```

### 1.3 (2 points)

Based on the operations that you’ve completed, how much closer are you
to answering your research questions? Think about what aspects of your
research questions remain unclear. Can your research questions be
refined, now that you’ve investigated your data a bit more? Which
research questions are yielding interesting results?

\#I think for most of my questions I either answered my research
question or would only need one more step to filter for a specific
neighbourhood for example to answer it. Thus, I think my questions could
be more refined for example looking at a specific neighbourhood or
looking at the age of the trees by the date they were planted and
investigating that relationship more. The question regarding if the
trees that are larger in diameter mean they are also taller was an
interesting question to investigate and judging by the graph I made to
look at the question it was seen that the top tallest and widest trees
also were not the widest and tallest respectively which was not
predicted. This would also make me wonder what the most common
diameter/height pair is the most common.

# Task 2: Tidy your data

In this task, we will do several exercises to reshape our data. The goal
here is to understand how to do this reshaping with the `tidyr` package.

A reminder of the definition of *tidy* data:

- Each row is an **observation**
- Each column is a **variable**
- Each cell is a **value**

### 2.1 (2 points)

Based on the definition above, can you identify if your data is tidy or
untidy? Go through all your columns, or if you have \>8 variables, just
pick 8, and explain whether the data is untidy or tidy.

\#Yes, my data is tidy as all my columns correspond to a variable, and
my rows are observations and each cell contains one value with little/no
“NA” values. Looking at the first 8 variables the columns display the
variables being tree id,
civic_number,std_street,genus_name,height_range_id and curb. Along with
the rows indicating an individual tree with each cell having a variable,
thus making this data tidy.

### 2.2 (4 points)

Now, if your data is tidy, untidy it! Then, tidy it back to it’s
original state.

If your data is untidy, then tidy it! Then, untidy it back to it’s
original state.

Be sure to explain your reasoning for this task. Show us the “before”
and “after”.

``` r
#I am just going to make the variables of "neighborhood names and diameter" untidy with the addition of 4 other variables 

newdata <- vancouver_trees[c(1:4,13, 15:17)]
newdata
```

    ## # A tibble: 146,611 × 8
    ##    tree_id civic_number std_street genus_name neighbourhood_name height_range_id
    ##      <dbl>        <dbl> <chr>      <chr>      <chr>                        <dbl>
    ##  1  149556          494 W 58TH AV  ULMUS      MARPOLE                          2
    ##  2  149563          450 W 58TH AV  ZELKOVA    MARPOLE                          4
    ##  3  149579         4994 WINDSOR ST STYRAX     KENSINGTON-CEDAR …               3
    ##  4  149590          858 E 39TH AV  FRAXINUS   KENSINGTON-CEDAR …               4
    ##  5  149604         5032 WINDSOR ST ACER       KENSINGTON-CEDAR …               2
    ##  6  149616          585 W 61ST AV  PYRUS      MARPOLE                          2
    ##  7  149617         4909 SHERBROOK… ACER       KENSINGTON-CEDAR …               3
    ##  8  149618         4925 SHERBROOK… ACER       KENSINGTON-CEDAR …               3
    ##  9  149619         4969 SHERBROOK… ACER       KENSINGTON-CEDAR …               2
    ## 10  149625          720 E 39TH AV  FRAXINUS   KENSINGTON-CEDAR …               2
    ## # ℹ 146,601 more rows
    ## # ℹ 2 more variables: diameter <dbl>, curb <chr>

``` r
newdata%>% pivot_wider(names_from = neighbourhood_name, values_from  = diameter) 
```

    ## # A tibble: 146,611 × 28
    ##    tree_id civic_number std_street    genus_name height_range_id curb  MARPOLE
    ##      <dbl>        <dbl> <chr>         <chr>                <dbl> <chr>   <dbl>
    ##  1  149556          494 W 58TH AV     ULMUS                    2 N          10
    ##  2  149563          450 W 58TH AV     ZELKOVA                  4 N          10
    ##  3  149579         4994 WINDSOR ST    STYRAX                   3 Y          NA
    ##  4  149590          858 E 39TH AV     FRAXINUS                 4 Y          NA
    ##  5  149604         5032 WINDSOR ST    ACER                     2 Y          NA
    ##  6  149616          585 W 61ST AV     PYRUS                    2 Y           5
    ##  7  149617         4909 SHERBROOKE ST ACER                     3 Y          NA
    ##  8  149618         4925 SHERBROOKE ST ACER                     3 Y          NA
    ##  9  149619         4969 SHERBROOKE ST ACER                     2 Y          NA
    ## 10  149625          720 E 39TH AV     FRAXINUS                 2 Y          NA
    ## # ℹ 146,601 more rows
    ## # ℹ 21 more variables: `KENSINGTON-CEDAR COTTAGE` <dbl>, OAKRIDGE <dbl>,
    ## #   `MOUNT PLEASANT` <dbl>, `RENFREW-COLLINGWOOD` <dbl>, `RILEY PARK` <dbl>,
    ## #   DOWNTOWN <dbl>, SUNSET <dbl>, `ARBUTUS-RIDGE` <dbl>,
    ## #   `GRANDVIEW-WOODLAND` <dbl>, KITSILANO <dbl>, `WEST END` <dbl>,
    ## #   SHAUGHNESSY <dbl>, `HASTINGS-SUNRISE` <dbl>, KERRISDALE <dbl>,
    ## #   `WEST POINT GREY` <dbl>, KILLARNEY <dbl>, STRATHCONA <dbl>, …

``` r
#Now the data is "untidy" since  the data is so sparce with all the NA values since I made the neighborhoods their own columns with diameters as their values. This creates alot of NA values since each tree id only belongs to one nieghbourhood and has only one diameter 
```

``` r
#To tidy my data now I have to revert the changes I made using pivot longer 

newdata <- vancouver_trees[c(1:4,13, 15:17)]
newdata
```

    ## # A tibble: 146,611 × 8
    ##    tree_id civic_number std_street genus_name neighbourhood_name height_range_id
    ##      <dbl>        <dbl> <chr>      <chr>      <chr>                        <dbl>
    ##  1  149556          494 W 58TH AV  ULMUS      MARPOLE                          2
    ##  2  149563          450 W 58TH AV  ZELKOVA    MARPOLE                          4
    ##  3  149579         4994 WINDSOR ST STYRAX     KENSINGTON-CEDAR …               3
    ##  4  149590          858 E 39TH AV  FRAXINUS   KENSINGTON-CEDAR …               4
    ##  5  149604         5032 WINDSOR ST ACER       KENSINGTON-CEDAR …               2
    ##  6  149616          585 W 61ST AV  PYRUS      MARPOLE                          2
    ##  7  149617         4909 SHERBROOK… ACER       KENSINGTON-CEDAR …               3
    ##  8  149618         4925 SHERBROOK… ACER       KENSINGTON-CEDAR …               3
    ##  9  149619         4969 SHERBROOK… ACER       KENSINGTON-CEDAR …               2
    ## 10  149625          720 E 39TH AV  FRAXINUS   KENSINGTON-CEDAR …               2
    ## # ℹ 146,601 more rows
    ## # ℹ 2 more variables: diameter <dbl>, curb <chr>

``` r
UNTIDY <- newdata %>% 
            pivot_wider(names_from = neighbourhood_name, values_from  = diameter)
            
#This is untidy data since the data is so sparce with all the NA values. 

UNTIDY
```

    ## # A tibble: 146,611 × 28
    ##    tree_id civic_number std_street    genus_name height_range_id curb  MARPOLE
    ##      <dbl>        <dbl> <chr>         <chr>                <dbl> <chr>   <dbl>
    ##  1  149556          494 W 58TH AV     ULMUS                    2 N          10
    ##  2  149563          450 W 58TH AV     ZELKOVA                  4 N          10
    ##  3  149579         4994 WINDSOR ST    STYRAX                   3 Y          NA
    ##  4  149590          858 E 39TH AV     FRAXINUS                 4 Y          NA
    ##  5  149604         5032 WINDSOR ST    ACER                     2 Y          NA
    ##  6  149616          585 W 61ST AV     PYRUS                    2 Y           5
    ##  7  149617         4909 SHERBROOKE ST ACER                     3 Y          NA
    ##  8  149618         4925 SHERBROOKE ST ACER                     3 Y          NA
    ##  9  149619         4969 SHERBROOKE ST ACER                     2 Y          NA
    ## 10  149625          720 E 39TH AV     FRAXINUS                 2 Y          NA
    ## # ℹ 146,601 more rows
    ## # ℹ 21 more variables: `KENSINGTON-CEDAR COTTAGE` <dbl>, OAKRIDGE <dbl>,
    ## #   `MOUNT PLEASANT` <dbl>, `RENFREW-COLLINGWOOD` <dbl>, `RILEY PARK` <dbl>,
    ## #   DOWNTOWN <dbl>, SUNSET <dbl>, `ARBUTUS-RIDGE` <dbl>,
    ## #   `GRANDVIEW-WOODLAND` <dbl>, KITSILANO <dbl>, `WEST END` <dbl>,
    ## #   SHAUGHNESSY <dbl>, `HASTINGS-SUNRISE` <dbl>, KERRISDALE <dbl>,
    ## #   `WEST POINT GREY` <dbl>, KILLARNEY <dbl>, STRATHCONA <dbl>, …

``` r
#To tidy the data I am going to drop the NA values and use pivot longer 

TIDY <- UNTIDY %>% 
        pivot_longer(cols = c("MARPOLE":"SOUTH CAMBIE"),
                    names_to = "neighbourhood_name",
                    values_to = "diameter",
                    values_drop_na = TRUE)

TIDY
```

    ## # A tibble: 146,611 × 8
    ##    tree_id civic_number std_street    genus_name height_range_id curb 
    ##      <dbl>        <dbl> <chr>         <chr>                <dbl> <chr>
    ##  1  149556          494 W 58TH AV     ULMUS                    2 N    
    ##  2  149563          450 W 58TH AV     ZELKOVA                  4 N    
    ##  3  149579         4994 WINDSOR ST    STYRAX                   3 Y    
    ##  4  149590          858 E 39TH AV     FRAXINUS                 4 Y    
    ##  5  149604         5032 WINDSOR ST    ACER                     2 Y    
    ##  6  149616          585 W 61ST AV     PYRUS                    2 Y    
    ##  7  149617         4909 SHERBROOKE ST ACER                     3 Y    
    ##  8  149618         4925 SHERBROOKE ST ACER                     3 Y    
    ##  9  149619         4969 SHERBROOKE ST ACER                     2 Y    
    ## 10  149625          720 E 39TH AV     FRAXINUS                 2 Y    
    ## # ℹ 146,601 more rows
    ## # ℹ 2 more variables: neighbourhood_name <chr>, diameter <dbl>

``` r
#Now mt data is back to it's original state with all columns correspond to a variable, and rows are observations and each cell contains one value with little/no "NA" values 
```

### 2.3 (4 points)

Now, you should be more familiar with your data, and also have made
progress in answering your research questions. Based on your interest,
and your analyses, pick 2 of the 4 research questions to continue your
analysis in the remaining tasks:

<!-------------------------- Start your work below ---------------------------->

1.  Do most trees that are larger in diameter mean they are also taller?
2.  Across the various neighborhoods are the widest trees all the same
    species?

<!----------------------------------------------------------------------------->

Explain your decision for choosing the above two research questions.

\#These 2 research questions are very interesting as for the first
question I would like to know the relationship between height and width
as I would think that this would have a positive relationship as if the
tree is very tall it would need a large diameter to support it however
this doesnt account for how large the branches are etc. For the second
question I think it would be interesting to investigate this further as
I would infer that the widest trees are the same species across all the
nieghbourhoods since the location of this dataset is only in Vancouver
however many tree species may have the same max diameters.

Now, try to choose a version of your data that you think will be
appropriate to answer these 2 questions. Use between 4 and 8 functions
that we’ve covered so far (i.e. by filtering, cleaning, tidy’ing,
dropping irrelevant columns, etc.).

(If it makes more sense, then you can make/pick two versions of your
data, one for each research question.)

``` r
#1I think to help answer these questions I would like to drop some columns such as street side name as that is irrelevant (select)
#2I would also like to combine the species and genus name to see even if 2 trees are different species they may be closely related and be the same genus (mutate)
#3I would like to arrange the rows so the highest diameter can be seen first (arrange)
#4I think moving some of the more useful variables to the front would also be useful (relocate)
#5I am also going to filter just for trees with a diameter larger than 10 as we are only looking for the widest trees for both questions. 


new <-vancouver_trees %>%
      select(tree_id, genus_name, species_name, neighbourhood_name, diameter, 
      height_range_id) %>%
      arrange(desc(diameter)) %>%
      relocate(tree_id, diameter, height_range_id) %>%
      filter(diameter > 10) %>%
      mutate(genus_species_name = paste(genus_name,species_name, sep="-"))
  
new
```

    ## # A tibble: 65,658 × 7
    ##    tree_id diameter height_range_id genus_name   species_name neighbourhood_name
    ##      <dbl>    <dbl>           <dbl> <chr>        <chr>        <chr>             
    ##  1  199599      435               2 STYRAX       JAPONICA     HASTINGS-SUNRISE  
    ##  2  149285      317               4 ACER         SPECIES      KITSILANO         
    ##  3  184211      305               2 QUERCUS      PHELLOS      DUNBAR-SOUTHLANDS 
    ##  4   51001      182               4 ACER         SACCHARINUM  MARPOLE           
    ##  5   84751      161               4 ACER         PLATANOIDES  MARPOLE           
    ##  6   54498      156               4 ACER         PLATANOIDES  KERRISDALE        
    ##  7   78588      151               4 ACER         RUBRUM       DOWNTOWN          
    ##  8  182674      144               4 ULMUS        AMERICANA    VICTORIA-FRASERVI…
    ##  9   23759      141               3 PRUNUS       SERRULATA    SOUTH CAMBIE      
    ## 10  117345      131               4 CERCIDIPHYL… JAPONICUM    VICTORIA-FRASERVI…
    ## # ℹ 65,648 more rows
    ## # ℹ 1 more variable: genus_species_name <chr>

# Task 3: Modelling

## 3.0 (no points)

Pick a research question from 1.2, and pick a variable of interest
(we’ll call it “Y”) that’s relevant to the research question. Indicate
these.

<!-------------------------- Start your work below ---------------------------->

**Research Question**: Do most trees that are larger in diameter mean
they are also taller

**Variable of interest**: Diameter

<!----------------------------------------------------------------------------->

## 3.1 (3 points)

Fit a model or run a hypothesis test that provides insight on this
variable with respect to the research question. Store the model object
as a variable, and print its output to screen. We’ll omit having to
justify your choice, because we don’t expect you to know about model
specifics in STAT 545.

- **Note**: It’s OK if you don’t know how these models/tests work. Here
  are some examples of things you can do here, but the sky’s the limit.

  - You could fit a model that makes predictions on Y using another
    variable, by using the `lm()` function.
  - You could test whether the mean of Y equals 0 using `t.test()`, or
    maybe the mean across two groups are different using `t.test()`, or
    maybe the mean across multiple groups are different using `anova()`
    (you may have to pivot your data for the latter two).
  - You could use `lm()` to test for significance of regression
    coefficients.

``` r
#I chose use the lm() function that provides insight on the significance between the 2 variables being height and diameter.
plot(diameter ~ height_range_id, data=vancouver_trees)
```

![](mda-nmhowesM2_FINAL__files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

``` r
diameter.height.lm <- lm(diameter ~ height_range_id, data = vancouver_trees)

summary(diameter.height.lm)
```

    ## 
    ## Call:
    ## lm(formula = diameter ~ height_range_id, data = vancouver_trees)
    ## 
    ## Residuals:
    ##    Min     1Q Median     3Q    Max 
    ## -41.82  -3.18  -1.13   2.09 426.34 
    ## 
    ## Coefficients:
    ##                 Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)     -0.38587    0.03102  -12.44   <2e-16 ***
    ## height_range_id  4.52082    0.01018  444.04   <2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 6.015 on 146609 degrees of freedom
    ## Multiple R-squared:  0.5735, Adjusted R-squared:  0.5735 
    ## F-statistic: 1.972e+05 on 1 and 146609 DF,  p-value: < 2.2e-16

``` r
#Since the P value is so low this indicates there is a significant relationship between height and diameter among the trees which helps answer my question as I know they are correlated.
```


    ## 3.2 (3 points)

    Produce something relevant from your fitted model: either predictions on Y, or a single value like a regression coefficient or a p-value.

    -   Be sure to indicate in writing what you chose to produce.
    -   Your code should either output a tibble (in which case you should indicate the column that contains the thing you're looking for), or the thing you're looking for itself.
    -   Obtain your results using the `broom` package if possible. If your model is not compatible with the broom function you're needing, then you can obtain your results by some other means, but first indicate which broom function is not compatible.






    ```r
    plot(diameter ~ height_range_id, data=vancouver_trees)

![](mda-nmhowesM2_FINAL__files/figure-gfm/unnamed-chunk-15-1.png)<!-- -->

``` r
diameter.height.lm <- lm(diameter ~ height_range_id, data = vancouver_trees)

broom::tidy(diameter.height.lm)
```

    ## # A tibble: 2 × 5
    ##   term            estimate std.error statistic  p.value
    ##   <chr>              <dbl>     <dbl>     <dbl>    <dbl>
    ## 1 (Intercept)       -0.386    0.0310     -12.4 1.65e-35
    ## 2 height_range_id    4.52     0.0102     444.  0

``` r
#I chose to reproduce the p value. Since the P value is so low this indicates there is a significant relationship between height and diameter among the trees which helps answer my question as I know changes in the x's value are related to changes in the y variable (diameter and height).
```






    # Task 4: Reading and writing data

    Get set up for this exercise by making a folder called `output` in the top level of your project folder / repository. You'll be saving things there.

    ## 4.1 (3 points)

    Take a summary table that you made from Task 1, and write it as a csv file in your `output` folder. Use the `here::here()` function.

    -   **Robustness criteria**: You should be able to move your Mini Project repository / project folder to some other location on your computer, or move this very Rmd file to another location within your project repository / folder, and your code should still work.
    -   **Reproducibility criteria**: You should be able to delete the csv file, and remake it simply by knitting this Rmd file.



    ```r
    ds <-vancouver_trees %>%
            group_by(curb) %>%
            summarise(count = n())

    write_csv(ds, here::here("Output/Task4.csv"))

    #A summary table from Task 1 is now in the output folder on my computer 

## 4.2 (3 points)

Write your model object from Task 3 to an R binary file (an RDS), and
load it again. Be sure to save the binary file in your `output` folder.
Use the functions `saveRDS()` and `readRDS()`.

- The same robustness and reproducibility criteria as in 4.1 apply here.

``` r
fit <- lm(diameter ~ height_range_id, data = vancouver_trees)


saveRDS(fit, file = "Output/my_fit.rds")


readRDS(fit, file = "Output/my_fit.rds")
```

    ## 
    ## Call:
    ## lm(formula = diameter ~ height_range_id, data = vancouver_trees)
    ## 
    ## Coefficients:
    ##     (Intercept)  height_range_id  
    ##         -0.3859           4.5208

``` r
fit
```

    ## 
    ## Call:
    ## lm(formula = diameter ~ height_range_id, data = vancouver_trees)
    ## 
    ## Coefficients:
    ##     (Intercept)  height_range_id  
    ##         -0.3859           4.5208

``` r
#My fit from Task 3 is now in the output folder on my computer
```

# Overall Reproducibility/Cleanliness/Coherence Checklist

Here are the criteria we’re looking for.

## Coherence (0.5 points)

The document should read sensibly from top to bottom, with no major
continuity errors.

The README file should still satisfy the criteria from the last
milestone, i.e. it has been updated to match the changes to the
repository made in this milestone.

## File and folder structure (1 points)

You should have at least three folders in the top level of your
repository: one for each milestone, and one output folder. If there are
any other folders, these are explained in the main README.

Each milestone document is contained in its respective folder, and
nowhere else.

Every level-1 folder (that is, the ones stored in the top level, like
“Milestone1” and “output”) has a `README` file, explaining in a sentence
or two what is in the folder, in plain language (it’s enough to say
something like “This folder contains the source for Milestone 1”).

## Output (1 point)

All output is recent and relevant:

- All Rmd files have been `knit`ted to their output md files.
- All knitted md files are viewable without errors on Github. Examples
  of errors: Missing plots, “Sorry about that, but we can’t show files
  that are this big right now” messages, error messages from broken R
  code
- All of these output files are up-to-date – that is, they haven’t
  fallen behind after the source (Rmd) files have been updated.
- There should be no relic output files. For example, if you were
  knitting an Rmd to html, but then changed the output to be only a
  markdown file, then the html file is a relic and should be deleted.

Our recommendation: delete all output files, and re-knit each
milestone’s Rmd file, so that everything is up to date and relevant.

## Tagged release (0.5 point)

You’ve tagged a release for Milestone 2.

### Attribution

Thanks to Victor Yuan for mostly putting this together.
