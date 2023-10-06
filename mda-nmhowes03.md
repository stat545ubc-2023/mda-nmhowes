mda-nmhowes
================
Nicole
2023-10-02

# Welcome to your (maybe) first-ever data analysis project!

# 

And hopefully the first of many. Let’s get started:

1.  Install the [`datateachr`](https://github.com/UBC-MDS/datateachr)
    package by typing the following into your **R terminal**:

<!-- -->

``` r
#install.packages("devtools")

#devtools::install_github("UBC-MDS/datateachr")
```

    #install.packages("devtools")
    #devtools::install_github("UBC-MDS/datateachr")

2.  Load the packages below.

``` r
library(datateachr)
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

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

3.  Make a repository in the <https://github.com/stat545ubc-2023>
    Organization. You can do this by following the steps found on canvas
    in the entry called [MDA: Create a
    repository](https://canvas.ubc.ca/courses/126199/pages/mda-create-a-repository).
    One completed, your repository should automatically be listed as
    part of the stat545ubc-2023 Organization.

# Instructions

## For Both Milestones

- Each milestone has explicit tasks. Tasks that are more challenging
  will often be allocated more points.

- Each milestone will be also graded for reproducibility, cleanliness,
  and coherence of the overall Github submission.

- While the two milestones will be submitted as independent
  deliverables, the analysis itself is a continuum - think of it as two
  chapters to a story. Each chapter, or in this case, portion of your
  analysis, should be easily followed through by someone unfamiliar with
  the content.
  [Here](https://swcarpentry.github.io/r-novice-inflammation/06-best-practices-R/)
  is a good resource for what constitutes “good code”. Learning good
  coding practices early in your career will save you hassle later on!

- The milestones will be equally weighted.

## For Milestone 1

**To complete this milestone**, edit [this very `.Rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-1.Rmd)
directly. Fill in the sections that are tagged with
`<!--- start your work below --->`.

**To submit this milestone**, make sure to knit this `.Rmd` file to an
`.md` file by changing the YAML output settings from
`output: html_document` to `output: github_document`. Commit and push
all of your work to the mini-analysis GitHub repository you made
earlier, and tag a release on GitHub. Then, submit a link to your tagged
release on canvas.

**Points**: This milestone is worth 36 points: 30 for your analysis, and
6 for overall reproducibility, cleanliness, and coherence of the Github
submission.

# Learning Objectives

By the end of this milestone, you should:

- Become familiar with your dataset of choosing
- Select 4 questions that you would like to answer with your data
- Generate a reproducible and clear report using R Markdown
- Become familiar with manipulating and summarizing your data in tibbles
  using `dplyr`, with a research question in mind.

# Task 1: Choose your favorite dataset

The `datateachr` package by Hayley Boyce and Jordan Bourak currently
composed of 7 semi-tidy datasets for educational purposes. Here is a
brief description of each dataset:

- *apt_buildings*: Acquired courtesy of The City of Toronto’s Open Data
  Portal. It currently has 3455 rows and 37 columns.

- *building_permits*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 20680 rows and 14 columns.

- *cancer_sample*: Acquired courtesy of UCI Machine Learning Repository.
  It currently has 569 rows and 32 columns.

- *flow_sample*: Acquired courtesy of The Government of Canada’s
  Historical Hydrometric Database. It currently has 218 rows and 7
  columns.

- *parking_meters*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 10032 rows and 22 columns.

- *steam_games*: Acquired courtesy of Kaggle. It currently has 40833
  rows and 21 columns.

- *vancouver_trees*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 146611 rows and 20 columns.

**Things to keep in mind**

- We hope that this project will serve as practice for carrying our your
  own *independent* data analysis. Remember to comment your code, be
  explicit about what you are doing, and write notes in this markdown
  document when you feel that context is required. As you advance in the
  project, prompts and hints to do this will be diminished - it’ll be up
  to you!

- Before choosing a dataset, you should always keep in mind **your
  goal**, or in other ways, *what you wish to achieve with this data*.
  This mini data-analysis project focuses on *data wrangling*,
  *tidying*, and *visualization*. In short, it’s a way for you to get
  your feet wet with exploring data on your own.

And that is exactly the first thing that you will do!

1.1 **(1 point)** Out of the 7 datasets available in the `datateachr`
package, choose **4** that appeal to you based on their description.
Write your choices below:

**Note**: We encourage you to use the ones in the `datateachr` package,
but if you have a dataset that you’d really like to use, you can include
it here. But, please check with a member of the teaching team to see
whether the dataset is of appropriate complexity. Also, include a
**brief** description of the dataset here to help the teaching team
understand your data.

<!-------------------------- Start your work below ---------------------------->

1: vancouver_trees 2: cancer_sample 3: building_permits 4: apt_buildings

<!----------------------------------------------------------------------------->

1.2 **(6 points)** One way to narrowing down your selection is to
*explore* the datasets. Use your knowledge of dplyr to find out at least
*3* attributes about each of these datasets (an attribute is something
such as number of rows, variables, class type…). The goal here is to
have an idea of *what the data looks like*.

*Hint:* This is one of those times when you should think about the
cleanliness of your analysis. I added a single code chunk for you below,
but do you want to use more than one? Would you like to write more
comments outside of the code chunk?

<!-------------------------- Start your work below ---------------------------->

# Exploring vancouver_trees data set

``` r
#I want to know the class type of this dataset 
class (vancouver_trees)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
#This is a tibble
```

``` r
#I want to know if the dataset is a vector, list, matrix, data frame or factors
typeof (vancouver_trees)
```

    ## [1] "list"

``` r
#I now know the dataset is a list
```

``` r
#I want to know the number of rows and columns (dimentions)
glimpse (vancouver_trees)
```

    ## Rows: 146,611
    ## Columns: 20
    ## $ tree_id            <dbl> 149556, 149563, 149579, 149590, 149604, 149616, 149…
    ## $ civic_number       <dbl> 494, 450, 4994, 858, 5032, 585, 4909, 4925, 4969, 7…
    ## $ std_street         <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ genus_name         <chr> "ULMUS", "ZELKOVA", "STYRAX", "FRAXINUS", "ACER", "…
    ## $ species_name       <chr> "AMERICANA", "SERRATA", "JAPONICA", "AMERICANA", "C…
    ## $ cultivar_name      <chr> "BRANDON", NA, NA, "AUTUMN APPLAUSE", NA, "CHANTICL…
    ## $ common_name        <chr> "BRANDON ELM", "JAPANESE ZELKOVA", "JAPANESE SNOWBE…
    ## $ assigned           <chr> "N", "N", "N", "Y", "N", "N", "N", "N", "N", "N", "…
    ## $ root_barrier       <chr> "N", "N", "N", "N", "N", "N", "N", "N", "N", "N", "…
    ## $ plant_area         <chr> "N", "N", "4", "4", "4", "B", "6", "6", "3", "3", "…
    ## $ on_street_block    <dbl> 400, 400, 4900, 800, 5000, 500, 4900, 4900, 4900, 7…
    ## $ on_street          <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ neighbourhood_name <chr> "MARPOLE", "MARPOLE", "KENSINGTON-CEDAR COTTAGE", "…
    ## $ street_side_name   <chr> "EVEN", "EVEN", "EVEN", "EVEN", "EVEN", "ODD", "ODD…
    ## $ height_range_id    <dbl> 2, 4, 3, 4, 2, 2, 3, 3, 2, 2, 2, 5, 3, 2, 2, 2, 2, …
    ## $ diameter           <dbl> 10.00, 10.00, 4.00, 18.00, 9.00, 5.00, 15.00, 14.00…
    ## $ curb               <chr> "N", "N", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "…
    ## $ date_planted       <date> 1999-01-13, 1996-05-31, 1993-11-22, 1996-04-29, 19…
    ## $ longitude          <dbl> -123.1161, -123.1147, -123.0846, -123.0870, -123.08…
    ## $ latitude           <dbl> 49.21776, 49.21776, 49.23938, 49.23469, 49.23894, 4…

``` r
#There are 146,611 rows and 20 columns
```

``` r
#I want to know how many trees there are with a diameter above 5.00
print (filter (vancouver_trees, diameter > 5.00))
```

    ## # A tibble: 95,692 × 20
    ##    tree_id civic_number std_street    genus_name species_name cultivar_name  
    ##      <dbl>        <dbl> <chr>         <chr>      <chr>        <chr>          
    ##  1  149556          494 W 58TH AV     ULMUS      AMERICANA    BRANDON        
    ##  2  149563          450 W 58TH AV     ZELKOVA    SERRATA      <NA>           
    ##  3  149590          858 E 39TH AV     FRAXINUS   AMERICANA    AUTUMN APPLAUSE
    ##  4  149604         5032 WINDSOR ST    ACER       CAMPESTRE    <NA>           
    ##  5  149617         4909 SHERBROOKE ST ACER       PLATANOIDES  COLUMNARE      
    ##  6  149618         4925 SHERBROOKE ST ACER       PLATANOIDES  COLUMNARE      
    ##  7  149619         4969 SHERBROOKE ST ACER       PLATANOIDES  COLUMNARE      
    ##  8  149625          720 E 39TH AV     FRAXINUS   AMERICANA    AUTUMN APPLAUSE
    ##  9  149626          736 E 39TH AV     TILIA      EUCHLORA   X <NA>           
    ## 10  149636          812 E 39TH AV     TILIA      EUCHLORA   X <NA>           
    ## # ℹ 95,682 more rows
    ## # ℹ 14 more variables: common_name <chr>, assigned <chr>, root_barrier <chr>,
    ## #   plant_area <chr>, on_street_block <dbl>, on_street <chr>,
    ## #   neighbourhood_name <chr>, street_side_name <chr>, height_range_id <dbl>,
    ## #   diameter <dbl>, curb <chr>, date_planted <date>, longitude <dbl>,
    ## #   latitude <dbl>

``` r
#There are 95, 692 trees that have a diameter larger than 5.00
```

# Exploring cancer_sample data set

``` r
#I want to know the class type of data 
class (cancer_sample)
```

    ## [1] "spec_tbl_df" "tbl_df"      "tbl"         "data.frame"

``` r
#This is a tibble
```

``` r
#I want to know if the dataset is a vector, list, matrix, data frame or factors
typeof (cancer_sample)
```

    ## [1] "list"

``` r
#I now know the dataset is a list
```

``` r
#I want to know the number of rows and columns (dimentions)
glimpse (cancer_sample)
```

    ## Rows: 569
    ## Columns: 32
    ## $ ID                      <dbl> 842302, 842517, 84300903, 84348301, 84358402, …
    ## $ diagnosis               <chr> "M", "M", "M", "M", "M", "M", "M", "M", "M", "…
    ## $ radius_mean             <dbl> 17.990, 20.570, 19.690, 11.420, 20.290, 12.450…
    ## $ texture_mean            <dbl> 10.38, 17.77, 21.25, 20.38, 14.34, 15.70, 19.9…
    ## $ perimeter_mean          <dbl> 122.80, 132.90, 130.00, 77.58, 135.10, 82.57, …
    ## $ area_mean               <dbl> 1001.0, 1326.0, 1203.0, 386.1, 1297.0, 477.1, …
    ## $ smoothness_mean         <dbl> 0.11840, 0.08474, 0.10960, 0.14250, 0.10030, 0…
    ## $ compactness_mean        <dbl> 0.27760, 0.07864, 0.15990, 0.28390, 0.13280, 0…
    ## $ concavity_mean          <dbl> 0.30010, 0.08690, 0.19740, 0.24140, 0.19800, 0…
    ## $ concave_points_mean     <dbl> 0.14710, 0.07017, 0.12790, 0.10520, 0.10430, 0…
    ## $ symmetry_mean           <dbl> 0.2419, 0.1812, 0.2069, 0.2597, 0.1809, 0.2087…
    ## $ fractal_dimension_mean  <dbl> 0.07871, 0.05667, 0.05999, 0.09744, 0.05883, 0…
    ## $ radius_se               <dbl> 1.0950, 0.5435, 0.7456, 0.4956, 0.7572, 0.3345…
    ## $ texture_se              <dbl> 0.9053, 0.7339, 0.7869, 1.1560, 0.7813, 0.8902…
    ## $ perimeter_se            <dbl> 8.589, 3.398, 4.585, 3.445, 5.438, 2.217, 3.18…
    ## $ area_se                 <dbl> 153.40, 74.08, 94.03, 27.23, 94.44, 27.19, 53.…
    ## $ smoothness_se           <dbl> 0.006399, 0.005225, 0.006150, 0.009110, 0.0114…
    ## $ compactness_se          <dbl> 0.049040, 0.013080, 0.040060, 0.074580, 0.0246…
    ## $ concavity_se            <dbl> 0.05373, 0.01860, 0.03832, 0.05661, 0.05688, 0…
    ## $ concave_points_se       <dbl> 0.015870, 0.013400, 0.020580, 0.018670, 0.0188…
    ## $ symmetry_se             <dbl> 0.03003, 0.01389, 0.02250, 0.05963, 0.01756, 0…
    ## $ fractal_dimension_se    <dbl> 0.006193, 0.003532, 0.004571, 0.009208, 0.0051…
    ## $ radius_worst            <dbl> 25.38, 24.99, 23.57, 14.91, 22.54, 15.47, 22.8…
    ## $ texture_worst           <dbl> 17.33, 23.41, 25.53, 26.50, 16.67, 23.75, 27.6…
    ## $ perimeter_worst         <dbl> 184.60, 158.80, 152.50, 98.87, 152.20, 103.40,…
    ## $ area_worst              <dbl> 2019.0, 1956.0, 1709.0, 567.7, 1575.0, 741.6, …
    ## $ smoothness_worst        <dbl> 0.1622, 0.1238, 0.1444, 0.2098, 0.1374, 0.1791…
    ## $ compactness_worst       <dbl> 0.6656, 0.1866, 0.4245, 0.8663, 0.2050, 0.5249…
    ## $ concavity_worst         <dbl> 0.71190, 0.24160, 0.45040, 0.68690, 0.40000, 0…
    ## $ concave_points_worst    <dbl> 0.26540, 0.18600, 0.24300, 0.25750, 0.16250, 0…
    ## $ symmetry_worst          <dbl> 0.4601, 0.2750, 0.3613, 0.6638, 0.2364, 0.3985…
    ## $ fractal_dimension_worst <dbl> 0.11890, 0.08902, 0.08758, 0.17300, 0.07678, 0…

``` r
#There are 569 rows and 32 columns
```

``` r
#I want to know how many patients have a tumor area mean above 1000
print (filter (cancer_sample, area_mean > 1000))
```

    ## # A tibble: 92 × 32
    ##          ID diagnosis radius_mean texture_mean perimeter_mean area_mean
    ##       <dbl> <chr>           <dbl>        <dbl>          <dbl>     <dbl>
    ##  1   842302 M                18.0         10.4           123.      1001
    ##  2   842517 M                20.6         17.8           133.      1326
    ##  3 84300903 M                19.7         21.2           130       1203
    ##  4 84358402 M                20.3         14.3           135.      1297
    ##  5   844359 M                18.2         20.0           120.      1040
    ##  6   846226 M                19.2         24.8           132.      1123
    ##  7   849014 M                19.8         22.2           130       1260
    ##  8   851509 M                21.2         23.0           137.      1404
    ##  9   852781 M                18.6         20.2           122.      1094
    ## 10   853401 M                18.6         25.1           125.      1088
    ## # ℹ 82 more rows
    ## # ℹ 26 more variables: smoothness_mean <dbl>, compactness_mean <dbl>,
    ## #   concavity_mean <dbl>, concave_points_mean <dbl>, symmetry_mean <dbl>,
    ## #   fractal_dimension_mean <dbl>, radius_se <dbl>, texture_se <dbl>,
    ## #   perimeter_se <dbl>, area_se <dbl>, smoothness_se <dbl>,
    ## #   compactness_se <dbl>, concavity_se <dbl>, concave_points_se <dbl>,
    ## #   symmetry_se <dbl>, fractal_dimension_se <dbl>, radius_worst <dbl>, …

``` r
#There are 92 patients with a tumor area mean above 1000
```

# Exploring building_permits data set

``` r
#I want to know the class type of data 
class (building_permits)
```

    ## [1] "spec_tbl_df" "tbl_df"      "tbl"         "data.frame"

``` r
#This is a tibble
```

``` r
#I want to know if the dataset is a vector, list, matrix, data frame or factors
typeof (building_permits)
```

    ## [1] "list"

``` r
#I now know the dataset is a list
```

``` r
#I want to know the number of rows and columns (dimentions)
glimpse (building_permits)
```

    ## Rows: 20,680
    ## Columns: 14
    ## $ permit_number               <chr> "BP-2016-02248", "BU468090", "DB-2016-0445…
    ## $ issue_date                  <date> 2017-02-01, 2017-02-01, 2017-02-01, 2017-…
    ## $ project_value               <dbl> 0, 0, 35000, 15000, 181178, 0, 15000, 0, 6…
    ## $ type_of_work                <chr> "Salvage and Abatement", "New Building", "…
    ## $ address                     <chr> "4378 W 9TH AVENUE, Vancouver, BC V6R 2C7"…
    ## $ project_description         <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ building_contractor         <chr> NA, NA, NA, "Mercury Contracting Ltd", "08…
    ## $ building_contractor_address <chr> NA, NA, NA, "88 W PENDER ST  \r\nUnit 2069…
    ## $ applicant                   <chr> "Raffaele & Associates DBA: Raffaele and A…
    ## $ applicant_address           <chr> "2642 East Hastings\r\nVancouver, BC  V5K …
    ## $ property_use                <chr> "Dwelling Uses", "Dwelling Uses", "Dwellin…
    ## $ specific_use_category       <chr> "One-Family Dwelling", "Multiple Dwelling"…
    ## $ year                        <dbl> 2017, 2017, 2017, 2017, 2017, 2017, 2017, …
    ## $ bi_id                       <dbl> 524, 535, 539, 541, 543, 546, 547, 548, 54…

``` r
#There are 20,680 rows and 14 columns
```

``` r
#I want to know how many building permits were made after 2017
print (filter (building_permits, year > 2017))
```

    ## # A tibble: 13,946 × 14
    ##    permit_number issue_date project_value type_of_work                address   
    ##    <chr>         <date>             <dbl> <chr>                       <chr>     
    ##  1 DB-2019-02732 2020-03-04       1403360 New Building                4636 W 3R…
    ##  2 DB-2019-02736 2020-03-04        229420 New Building                4632 W 3R…
    ##  3 DB-2019-04755 2020-03-04        997565 New Building                2251 BONN…
    ##  4 DB-2019-04756 2020-03-04         15000 Demolition / Deconstruction 2253 BONN…
    ##  5 BP-2019-05726 2020-03-05             0 Salvage and Abatement       2259 W 18…
    ##  6 BP-2020-00177 2020-03-05        300000 Addition / Alteration       1090 W GE…
    ##  7 BP-2020-00222 2020-03-05         15000 Addition / Alteration       200 BURRA…
    ##  8 BP-2020-00233 2020-03-05          8000 Addition / Alteration       870 W 7TH…
    ##  9 BP-2020-00335 2020-03-05          8000 Addition / Alteration       151 E 2ND…
    ## 10 DB-2019-04904 2020-03-05        678520 New Building                250 E 54T…
    ## # ℹ 13,936 more rows
    ## # ℹ 9 more variables: project_description <chr>, building_contractor <chr>,
    ## #   building_contractor_address <chr>, applicant <chr>,
    ## #   applicant_address <chr>, property_use <chr>, specific_use_category <chr>,
    ## #   year <dbl>, bi_id <dbl>

``` r
#There are 13,946 building permits made after 2017
```

# Exploring apt_buildings data set

``` r
#I want to know the class type of data 
class (apt_buildings)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
#This is a tibble
```

``` r
#I want to know if the dataset is a vector, list, matrix, data frame or factors
typeof (apt_buildings)
```

    ## [1] "list"

``` r
#I now know the dataset is a list
```

``` r
#I want to know the number of rows and columns (dimentions)
glimpse (apt_buildings)
```

    ## Rows: 3,455
    ## Columns: 37
    ## $ id                               <dbl> 10359, 10360, 10361, 10362, 10363, 10…
    ## $ air_conditioning                 <chr> "NONE", "NONE", "NONE", "NONE", "NONE…
    ## $ amenities                        <chr> "Outdoor rec facilities", "Outdoor po…
    ## $ balconies                        <chr> "YES", "YES", "YES", "YES", "NO", "NO…
    ## $ barrier_free_accessibilty_entr   <chr> "YES", "NO", "NO", "YES", "NO", "NO",…
    ## $ bike_parking                     <chr> "0 indoor parking spots and 10 outdoo…
    ## $ exterior_fire_escape             <chr> "NO", "NO", "NO", "YES", "NO", NA, "N…
    ## $ fire_alarm                       <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ garbage_chutes                   <chr> "YES", "YES", "NO", "NO", "NO", "NO",…
    ## $ heating_type                     <chr> "HOT WATER", "HOT WATER", "HOT WATER"…
    ## $ intercom                         <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ laundry_room                     <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ locker_or_storage_room           <chr> "NO", "YES", "YES", "YES", "NO", "YES…
    ## $ no_of_elevators                  <dbl> 3, 3, 0, 1, 0, 0, 0, 2, 4, 2, 0, 2, 2…
    ## $ parking_type                     <chr> "Underground Garage , Garage accessib…
    ## $ pets_allowed                     <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ prop_management_company_name     <chr> NA, "SCHICKEDANZ BROS. PROPERTIES", N…
    ## $ property_type                    <chr> "PRIVATE", "PRIVATE", "PRIVATE", "PRI…
    ## $ rsn                              <dbl> 4154812, 4154815, 4155295, 4155309, 4…
    ## $ separate_gas_meters              <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ separate_hydro_meters            <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ separate_water_meters            <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ site_address                     <chr> "65  FOREST MANOR RD", "70  CLIPPER R…
    ## $ sprinkler_system                 <chr> "YES", "YES", "NO", "YES", "NO", "NO"…
    ## $ visitor_parking                  <chr> "PAID", "FREE", "UNAVAILABLE", "UNAVA…
    ## $ ward                             <chr> "17", "17", "03", "03", "02", "02", "…
    ## $ window_type                      <chr> "DOUBLE PANE", "DOUBLE PANE", "DOUBLE…
    ## $ year_built                       <dbl> 1967, 1970, 1927, 1959, 1943, 1952, 1…
    ## $ year_registered                  <dbl> 2017, 2017, 2017, 2017, 2017, NA, 201…
    ## $ no_of_storeys                    <dbl> 17, 14, 4, 5, 4, 4, 4, 7, 32, 4, 4, 7…
    ## $ emergency_power                  <chr> "NO", "YES", "NO", "NO", "NO", "NO", …
    ## $ `non-smoking_building`           <chr> "YES", "NO", "YES", "YES", "YES", "NO…
    ## $ no_of_units                      <dbl> 218, 206, 34, 42, 25, 34, 14, 105, 57…
    ## $ no_of_accessible_parking_spaces  <dbl> 8, 10, 20, 42, 12, 0, 5, 1, 1, 6, 12,…
    ## $ facilities_available             <chr> "Recycling bins", "Green Bin / Organi…
    ## $ cooling_room                     <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ no_barrier_free_accessible_units <dbl> 2, 0, 0, 42, 0, NA, 14, 0, 0, 1, 25, …

``` r
#There are 3,455 rows and 37 columns
```

``` r
#I want to know how many building have balconies
print (filter (apt_buildings, balconies == "YES"))
```

    ## # A tibble: 2,361 × 37
    ##       id air_conditioning amenities             balconies barrier_free_accessi…¹
    ##    <dbl> <chr>            <chr>                 <chr>     <chr>                 
    ##  1 10359 NONE             Outdoor rec faciliti… YES       YES                   
    ##  2 10360 NONE             Outdoor pool          YES       NO                    
    ##  3 10361 NONE             <NA>                  YES       NO                    
    ##  4 10362 NONE             <NA>                  YES       YES                   
    ##  5 10366 CENTRAL AIR      Indoor pool , Indoor… YES       NO                    
    ##  6 10367 NONE             <NA>                  YES       YES                   
    ##  7 10368 NONE             Indoor recreation ro… YES       YES                   
    ##  8 10370 NONE             <NA>                  YES       NO                    
    ##  9 10371 NONE             <NA>                  YES       YES                   
    ## 10 10372 NONE             <NA>                  YES       NO                    
    ## # ℹ 2,351 more rows
    ## # ℹ abbreviated name: ¹​barrier_free_accessibilty_entr
    ## # ℹ 32 more variables: bike_parking <chr>, exterior_fire_escape <chr>,
    ## #   fire_alarm <chr>, garbage_chutes <chr>, heating_type <chr>, intercom <chr>,
    ## #   laundry_room <chr>, locker_or_storage_room <chr>, no_of_elevators <dbl>,
    ## #   parking_type <chr>, pets_allowed <chr>, prop_management_company_name <chr>,
    ## #   property_type <chr>, rsn <dbl>, separate_gas_meters <chr>, …

``` r
#there are 2,361 buildings with balconies
```

<!----------------------------------------------------------------------------->

1.3 **(1 point)** Now that you’ve explored the 4 datasets that you were
initially most interested in, let’s narrow it down to 1. What lead you
to choose this one? Briefly explain your choice below.

<!-------------------------- Start your work below ---------------------------->

\#I chose the Vancouver trees dataset, personally this dataset was the
most interesting to me as I would like to investigate the relationship
between tree species, location and dimention of the trees. It was also
be interesting to look at trees that I could potentially see in my
neighborhood and if they could ge easy to spot based on their location
and size.

<!----------------------------------------------------------------------------->

1.4 **(2 points)** Time for a final decision! Going back to the
beginning, it’s important to have an *end goal* in mind. For example, if
I had chosen the `titanic` dataset for my project, I might’ve wanted to
explore the relationship between survival and other variables. Try to
think of 1 research question that you would want to answer with your
dataset. Note it down below.

<!-------------------------- Start your work below ---------------------------->

\#I would want to look at the relationship between the tree species in
relation to the diameter, height range and where it can commonly be
found to ultimately find the biggest and most common tree species in
Kitsilano.

# Important note

Read Tasks 2 and 3 *fully* before starting to complete either of them.
Probably also a good point to grab a coffee to get ready for the fun
part!

This project is semi-guided, but meant to be *independent*. For this
reason, you will complete tasks 2 and 3 below (under the **START HERE**
mark) as if you were writing your own exploratory data analysis report,
and this guidance never existed! Feel free to add a brief introduction
section to your project, format the document with markdown syntax as you
deem appropriate, and structure the analysis as you deem appropriate. If
you feel lost, you can find a sample data analysis
[here](https://www.kaggle.com/headsortails/tidy-titarnic) to have a
better idea. However, bear in mind that it is **just an example** and
you will not be required to have that level of complexity in your
project.

# Task 2: Exploring your dataset

If we rewind and go back to the learning objectives, you’ll see that by
the end of this deliverable, you should have formulated *4* research
questions about your data that you may want to answer during your
project. However, it may be handy to do some more exploration on your
dataset of choice before creating these questions - by looking at the
data, you may get more ideas. **Before you start this task, read all
instructions carefully until you reach START HERE under Task 3**.

2.1 **(12 points)** Complete *4 out of the following 8 exercises* to
dive deeper into your data. All datasets are different and therefore,
not all of these tasks may make sense for your data - which is why you
should only answer *4*.

Make sure that you’re using dplyr and ggplot2 rather than base R for
this task. Outside of this project, you may find that you prefer using
base R functions for certain tasks, and that’s just fine! But part of
this project is for you to practice the tools we learned in class, which
is dplyr and ggplot2.

1.  Plot the distribution of a numeric variable.
2.  Create a new variable based on other variables in your data (only if
    it makes sense)
3.  Investigate how many missing values there are per variable. Can you
    find a way to plot this?
4.  Explore the relationship between 2 variables in a plot.
5.  Filter observations in your data according to your own criteria.
    Think of what you’d like to explore - again, if this was the
    `titanic` dataset, I may want to narrow my search down to passengers
    born in a particular year…
6.  Use a boxplot to look at the frequency of different observations
    within a single variable. You can do this for more than one variable
    if you wish!
7.  Make a new tibble with a subset of your data, with variables and
    observations that you are interested in exploring.
8.  Use a density plot to explore any of your variables (that are
    suitable for this type of plot).

2.2 **(4 points)** For each of the 4 exercises that you complete,
provide a *brief explanation* of why you chose that exercise in relation
to your data (in other words, why does it make sense to do that?), and
sufficient comments for a reader to understand your reasoning and code.

<!-------------------------- Start your work below ---------------------------->

# First I wanted find the average diameter of the trees to get a sense of how big they were by looking at the diameter distribution and what the most common diameter is across all the trees (Plot the distribution of a numeric variable (#1))

``` r
ggplot(vancouver_trees, aes(x = diameter)) + 
  geom_histogram(binwidth=5.5) +
  labs(title= "Tree Diameter", x = "Diameter (m)", y = "Number of trees") %>% 
  print()
```

    ## $x
    ## [1] "Diameter (m)"
    ## 
    ## $y
    ## [1] "Number of trees"
    ## 
    ## $title
    ## [1] "Tree Diameter"
    ## 
    ## attr(,"class")
    ## [1] "labels"

![](mda-nmhowes03_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->

``` r
#This shows me that most of the diameters are under 50 with majority being around 10.So if I needed to cut some trees I could filter for diameters just under 25 as that is where I would find the majority of them. For this plot I used the diameter for the x axis to view the counts in a histogram using ggplot to look at the distribution. 
```

# I also want to look at trees in my own neighbourhood to see what tree’s I could look at during an everyday walk in Kitsilano (Filter observations in your data according to your own criteria \#5)

``` r
print (filter (vancouver_trees, neighbourhood_name == "KITSILANO"))
```

    ## # A tibble: 8,115 × 20
    ##    tree_id civic_number std_street genus_name species_name  cultivar_name   
    ##      <dbl>        <dbl> <chr>      <chr>      <chr>         <chr>           
    ##  1  155373         1900 CYPRESS ST PRUNUS     CERASIFERA    NIGRA           
    ##  2  155413         2485 W BROADWAY ULMUS      AMERICANA     BRANDON         
    ##  3  155445         2408 W 13TH AV  ACER       FREEMANI   X  SCARLET SENTINEL
    ##  4  155446         2246 W 15TH AV  ACER       RUBRUM        KARPICK         
    ##  5  155566         2995 W 10TH AV  CATALPA    BIGNONIOIDES  <NA>            
    ##  6  156222         2688 VINE ST    QUERCUS    ROBUR         <NA>            
    ##  7  156380         2983 YEW ST     FRAXINUS   PENNSYLVANICA PATMORE         
    ##  8  156382         2983 YEW ST     FRAXINUS   PENNSYLVANICA PATMORE         
    ##  9  156390         2375 W 10TH AV  ACER       CAMPESTRE     <NA>            
    ## 10  156413         2835 YEW ST     FRAXINUS   AMERICANA     AUTUMN APPLAUSE 
    ## # ℹ 8,105 more rows
    ## # ℹ 14 more variables: common_name <chr>, assigned <chr>, root_barrier <chr>,
    ## #   plant_area <chr>, on_street_block <dbl>, on_street <chr>,
    ## #   neighbourhood_name <chr>, street_side_name <chr>, height_range_id <dbl>,
    ## #   diameter <dbl>, curb <chr>, date_planted <date>, longitude <dbl>,
    ## #   latitude <dbl>

``` r
#This shows me that there are 8115 documented trees in the kitsilano neighbourhood that I can walk to and see as the filter function helped me cater my search to just trees near my house. 

vancouver_trees %>%
  group_by(neighbourhood_name = "KITSILANO") %>%
    top_n(1, species_name)
```

    ## # A tibble: 1,613 × 20
    ## # Groups:   neighbourhood_name [1]
    ##    tree_id civic_number std_street       genus_name species_name cultivar_name
    ##      <dbl>        <dbl> <chr>            <chr>      <chr>        <chr>        
    ##  1  156588         2306 KITCHENER ST     MALUS      ZUMI         CALOCARPA    
    ##  2  157159         4089 SELKIRK ST       MALUS      ZUMI         CALOCARPA    
    ##  3  157816          515 SALSBURY DRIVE   MALUS      ZUMI         CALOCARPA    
    ##  4  157818          520 SALSBURY DRIVE   MALUS      ZUMI         CALOCARPA    
    ##  5  158748         1037 W KING EDWARD AV MALUS      ZUMI         CALOCARPA    
    ##  6  158750         1063 W KING EDWARD AV MALUS      ZUMI         CALOCARPA    
    ##  7  158751         4050 OSLER ST         MALUS      ZUMI         CALOCARPA    
    ##  8  159644         3793 W 18TH AV        MALUS      ZUMI         CALOCARPA    
    ##  9  159645         6049 DUNBAR ST        MALUS      ZUMI         CALOCARPA    
    ## 10  159698         1808 E 2ND AV         MALUS      ZUMI         CALOCARPA    
    ## # ℹ 1,603 more rows
    ## # ℹ 14 more variables: common_name <chr>, assigned <chr>, root_barrier <chr>,
    ## #   plant_area <chr>, on_street_block <dbl>, on_street <chr>,
    ## #   neighbourhood_name <chr>, street_side_name <chr>, height_range_id <dbl>,
    ## #   diameter <dbl>, curb <chr>, date_planted <date>, longitude <dbl>,
    ## #   latitude <dbl>

``` r
#I also wanted to know the most common species located in Kitsilano so I used the top_n function and found the most common species to be "Zumi".
```

# I wanted to also look at the relationship between 2 variables in a plot being the diameter and neighbourhood to get a sense of where the widest trees were (#4)

``` r
ggplot(vancouver_trees, aes(x = diameter, y = neighbourhood_name)) +
     geom_point(size = 0.5, alpha = 0.5) +
    labs(title= "Diameters among trees in various neighbourhoods", x = "Diameter (m)", y = "Neighbourhood Name") %>% 
  print()
```

    ## $x
    ## [1] "Diameter (m)"
    ## 
    ## $y
    ## [1] "Neighbourhood Name"
    ## 
    ## $title
    ## [1] "Diameters among trees in various neighbourhoods"
    ## 
    ## attr(,"class")
    ## [1] "labels"

![](mda-nmhowes03_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->

``` r
#This shows me that among all the neighbourhoods the diameters of trees are relatively the same with the largest being in kitsilano, dunbar and hastings.By creating a plot I can easily see that the outliar points indicating the largest trees are in the neighbourhoods previously listed. 
```

# I wanted to additionally look at the relationship between 2 variables in a plot (#4) being the diameter and species in Kitsilano and what species had the largest diameter.

``` r
vancouver_trees %>%
  filter(neighbourhood_name == "KITSILANO", diameter > 40.00 ) %>%
  ggplot(aes(x = diameter, y = common_name)) +
  geom_point() +
  labs(title= "Diameters among trees in Kitsilano", x = "Diameter (m)", y = "Common Tree Name") %>% 
  print()
```

    ## $x
    ## [1] "Diameter (m)"
    ## 
    ## $y
    ## [1] "Common Tree Name"
    ## 
    ## $title
    ## [1] "Diameters among trees in Kitsilano"
    ## 
    ## attr(,"class")
    ## [1] "labels"

![](mda-nmhowes03_files/figure-gfm/unnamed-chunk-22-1.png)<!-- -->

``` r
#This shows me the exact species that I can find in Kitsilano that are large with a diameter above 40, this plot also shows the largest tree species in diameter in Kitsilano being a Maple species. To build this plot I first filtered for the neighbourhood as the there are too many tree species in the dataset to show on a single graph, I also had to filter for a diameter above 40. I was then able to view diameters above 40 and tree species easily. 
```

# Lastly I wanted to look at the height of these trees to also see how large they were and if they were located on the curb in a density plot (#8) so I would be able to see them easier on a walk.

``` r
ggplot(vancouver_trees, aes(x = height_range_id, colour = curb)) +
   geom_density(alpha=0.4) +
  labs(title= "Height range density plot", x = "Height Range ID", y = "Density") %>% 
  print()
```

    ## $x
    ## [1] "Height Range ID"
    ## 
    ## $y
    ## [1] "Density"
    ## 
    ## $title
    ## [1] "Height range density plot"
    ## 
    ## attr(,"class")
    ## [1] "labels"

![](mda-nmhowes03_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->

``` r
#This shows me most of the trees were in the ID = 2 range meaning they were around 20-25 ft as they were in the 20-30 range and that the same trend is seen for trees both on and off the curb that the trees decrease in density the taller they get and most trees on the curb are around 20 ft. This was easily seen by making a density plot of the height range id and using colour the differentiate between trees located on and off the curb. 
```

# Task 3: Choose research questions

**(4 points)** So far, you have chosen a dataset and gotten familiar
with it through exploring the data. You have also brainstormed one
research question that interested you (Task 1.4). Now it’s time to pick
4 research questions that you would like to explore in Milestone 2!
Write the 4 questions and any additional comments below.

<!--- *****START HERE***** --->

\#Through my data analysis I’ve found that I wanted to further
investigate height/diameter of trees in relation to trees in Kitsilano
and the amount of trees in certain nieghbourhoods.

\#1: Are larger trees (diameter) in Kitsilano typically seen on the
curb?

\#2: What tree species in Kitsilano have the largest diameter and
height?

\#3: Do most trees that are larger in diameter mean they are also
taller?

\#4: What neighborhood has the lowest amount of trees? What species is
most common there?

# Overall reproducibility/Cleanliness/Coherence Checklist

## Coherence (0.5 points)

The document should read sensibly from top to bottom, with no major
continuity errors. An example of a major continuity error is having a
data set listed for Task 3 that is not part of one of the data sets
listed in Task 1.

## Error-free code (3 points)

For full marks, all code in the document should run without error. 1
point deduction if most code runs without error, and 2 points deduction
if more than 50% of the code throws an error.

## Main README (1 point)

There should be a file named `README.md` at the top level of your
repository. Its contents should automatically appear when you visit the
repository on GitHub.

Minimum contents of the README file:

- In a sentence or two, explains what this repository is, so that
  future-you or someone else stumbling on your repository can be
  oriented to the repository.
- In a sentence or two (or more??), briefly explains how to engage with
  the repository. You can assume the person reading knows the material
  from STAT 545A. Basically, if a visitor to your repository wants to
  explore your project, what should they know?

Once you get in the habit of making README files, and seeing more README
files in other projects, you’ll wonder how you ever got by without them!
They are tremendously helpful.

## Output (1 point)

All output is readable, recent and relevant:

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

(0.5 point deduction if any of the above criteria are not met. 1 point
deduction if most or all of the above criteria are not met.)

Our recommendation: right before submission, delete all output files,
and re-knit each milestone’s Rmd file, so that everything is up to date
and relevant. Then, after your final commit and push to Github, CHECK on
Github to make sure that everything looks the way you intended!

## Tagged release (0.5 points)

You’ve tagged a release for Milestone 1.

### Attribution

Thanks to Icíar Fernández Boyano for mostly putting this together, and
Vincenzo Coia for launching.
