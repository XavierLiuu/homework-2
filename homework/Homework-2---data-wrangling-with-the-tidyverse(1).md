-   [Homework 2 - data wrangling with the
    `tidyverse`](#homework-2---data-wrangling-with-the-tidyverse)
    -   [Which NBA player scored the most points in
        1991?](#which-nba-player-scored-the-most-points-in-1991)
    -   [Which player had the best free throw percentage from the year
        2000 to the most recent year in the
        data?](#which-player-had-the-best-free-throw-percentage-from-the-year-2000-to-the-most-recent-year-in-the-data)
    -   [Rename the variable `pos` to
        `position`.](#rename-the-variable-pos-to-position.)
    -   [Use this variable to create two variables that are called
        `first_position` and `second_position`. Hint: separate by
        splitting the position variable in
        two.](#use-this-variable-to-create-two-variables-that-are-called-first_position-and-second_position.-hint-separate-by-splitting-the-position-variable-in-two.)
    -   [Create two new datasets.](#create-two-new-datasets.)
        -   [a new dataset from the original dataset that includes all
            data except the age variable (be sure to give this dataset a
            new
            name).](#a-new-dataset-from-the-original-dataset-that-includes-all-data-except-the-age-variable-be-sure-to-give-this-dataset-a-new-name.)
        -   [a new dataset from the original dataset that includes the
            year, the player name, and
            age.](#a-new-dataset-from-the-original-dataset-that-includes-the-year-the-player-name-and-age.)
    -   [add a new column to both datasets called mergeid that includes
        a sequence of numbers beginning with a 1 in the first row of the
        data and ending with the total number of rows in the last row of
        the
        data](#add-a-new-column-to-both-datasets-called-mergeid-that-includes-a-sequence-of-numbers-beginning-with-a-1-in-the-first-row-of-the-data-and-ending-with-the-total-number-of-rows-in-the-last-row-of-the-data)
    -   [Join the two datasets from question (6) together to recreate
        the original dataset plus the new merge
        id.](#join-the-two-datasets-from-question-6-together-to-recreate-the-original-dataset-plus-the-new-merge-id.)
    -   [Subset the original dataset to 1995. Group the data by year and
        team name and then summarize the average number of points per
        team. Arrange from most to least
        points.](#subset-the-original-dataset-to-1995.-group-the-data-by-year-and-team-name-and-then-summarize-the-average-number-of-points-per-team.-arrange-from-most-to-least-points.)
    -   [Reshape the data in the previous question into a wide format
        using the tidyr package. Create a wide dataset that keeps year
        in a single column, but spreads team names to multiple
        individual columns with each column delineating points per team
        in
        1995.](#reshape-the-data-in-the-previous-question-into-a-wide-format-using-the-tidyr-package.-create-a-wide-dataset-that-keeps-year-in-a-single-column-but-spreads-team-names-to-multiple-individual-columns-with-each-column-delineating-points-per-team-in-1995.)
    -   [Now return the data to a long (tidy) format by moving teams
        back into a single column and points in a single
        column.](#now-return-the-data-to-a-long-tidy-format-by-moving-teams-back-into-a-single-column-and-points-in-a-single-column.)

# Homework 2 - data wrangling with the `tidyverse`

## Which NBA player scored the most points in 1991?

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.2     v dplyr   1.0.7
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   1.4.0     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

    ##            Player
    ## 1 Michael Jordan*

## Which player had the best free throw percentage from the year 2000 to the most recent year in the data?

    ##       Player
    ## 1 Drew Barry

## Rename the variable `pos` to `position`.

``` r
data %>% 
  rename(Position = Pos) %>% head(10)
```

    ##    Year          Player Position Age  Tm  G GS MP PER   TS. X3PAr   FTr ORB.
    ## 1  1950 Curly Armstrong      G-F  31 FTW 63 NA NA  NA 0.368    NA 0.467   NA
    ## 2  1950    Cliff Barker       SG  29 INO 49 NA NA  NA 0.435    NA 0.387   NA
    ## 3  1950   Leo Barnhorst       SF  25 CHS 67 NA NA  NA 0.394    NA 0.259   NA
    ## 4  1950      Ed Bartels        F  24 TOT 15 NA NA  NA 0.312    NA 0.395   NA
    ## 5  1950      Ed Bartels        F  24 DNN 13 NA NA  NA 0.308    NA 0.378   NA
    ## 6  1950      Ed Bartels        F  24 NYK  2 NA NA  NA 0.376    NA 0.750   NA
    ## 7  1950     Ralph Beard        G  22 INO 60 NA NA  NA 0.422    NA 0.301   NA
    ## 8  1950      Gene Berce      G-F  23 TRI  3 NA NA  NA 0.275    NA 0.313   NA
    ## 9  1950   Charlie Black      F-C  28 TOT 65 NA NA  NA 0.346    NA 0.395   NA
    ## 10 1950   Charlie Black      F-C  28 FTW 36 NA NA  NA 0.362    NA 0.480   NA
    ##    DRB. TRB. AST. STL. BLK. TOV. USG. blanl  OWS  DWS   WS WS.48 blank2 OBPM
    ## 1    NA   NA   NA   NA   NA   NA   NA    NA -0.1  3.6  3.5    NA     NA   NA
    ## 2    NA   NA   NA   NA   NA   NA   NA    NA  1.6  0.6  2.2    NA     NA   NA
    ## 3    NA   NA   NA   NA   NA   NA   NA    NA  0.9  2.8  3.6    NA     NA   NA
    ## 4    NA   NA   NA   NA   NA   NA   NA    NA -0.5 -0.1 -0.6    NA     NA   NA
    ## 5    NA   NA   NA   NA   NA   NA   NA    NA -0.5 -0.1 -0.6    NA     NA   NA
    ## 6    NA   NA   NA   NA   NA   NA   NA    NA  0.0  0.0  0.0    NA     NA   NA
    ## 7    NA   NA   NA   NA   NA   NA   NA    NA  3.6  1.2  4.8    NA     NA   NA
    ## 8    NA   NA   NA   NA   NA   NA   NA    NA -0.1  0.0 -0.1    NA     NA   NA
    ## 9    NA   NA   NA   NA   NA   NA   NA    NA -2.2  5.0  2.8    NA     NA   NA
    ## 10   NA   NA   NA   NA   NA   NA   NA    NA -0.7  2.2  1.5    NA     NA   NA
    ##    DBPM BPM VORP  FG FGA   FG. X3P X3PA X3P. X2P X2PA  X2P.  eFG.  FT FTA   FT.
    ## 1    NA  NA   NA 144 516 0.279  NA   NA   NA 144  516 0.279 0.279 170 241 0.705
    ## 2    NA  NA   NA 102 274 0.372  NA   NA   NA 102  274 0.372 0.372  75 106 0.708
    ## 3    NA  NA   NA 174 499 0.349  NA   NA   NA 174  499 0.349 0.349  90 129 0.698
    ## 4    NA  NA   NA  22  86 0.256  NA   NA   NA  22   86 0.256 0.256  19  34 0.559
    ## 5    NA  NA   NA  21  82 0.256  NA   NA   NA  21   82 0.256 0.256  17  31 0.548
    ## 6    NA  NA   NA   1   4 0.250  NA   NA   NA   1    4 0.250 0.250   2   3 0.667
    ## 7    NA  NA   NA 340 936 0.363  NA   NA   NA 340  936 0.363 0.363 215 282 0.762
    ## 8    NA  NA   NA   5  16 0.313  NA   NA   NA   5   16 0.313 0.313   0   5 0.000
    ## 9    NA  NA   NA 226 813 0.278  NA   NA   NA 226  813 0.278 0.278 209 321 0.651
    ## 10   NA  NA   NA 125 435 0.287  NA   NA   NA 125  435 0.287 0.287 132 209 0.632
    ##    ORB DRB TRB AST STL BLK TOV  PF PTS
    ## 1   NA  NA  NA 176  NA  NA  NA 217 458
    ## 2   NA  NA  NA 109  NA  NA  NA  99 279
    ## 3   NA  NA  NA 140  NA  NA  NA 192 438
    ## 4   NA  NA  NA  20  NA  NA  NA  29  63
    ## 5   NA  NA  NA  20  NA  NA  NA  27  59
    ## 6   NA  NA  NA   0  NA  NA  NA   2   4
    ## 7   NA  NA  NA 233  NA  NA  NA 132 895
    ## 8   NA  NA  NA   2  NA  NA  NA   6  10
    ## 9   NA  NA  NA 163  NA  NA  NA 273 661
    ## 10  NA  NA  NA  75  NA  NA  NA 140 382

## Use this variable to create two variables that are called `first_position` and `second_position`. Hint: separate by splitting the position variable in two.

``` r
data$first_position <- str_split(data$position, "-") %>% unlist %>% .[[1]]
data$second_position <- str_split(data$position, "-") %>% unlist %>% .[[2]]
```

## Create two new datasets.

### a new dataset from the original dataset that includes all data except the age variable (be sure to give this dataset a new name).

``` r
data %>% 
  select(-Age) -> data1
head(data1, 10)
```

    ##    Year          Player Pos  Tm  G GS MP PER   TS. X3PAr   FTr ORB. DRB. TRB.
    ## 1  1950 Curly Armstrong G-F FTW 63 NA NA  NA 0.368    NA 0.467   NA   NA   NA
    ## 2  1950    Cliff Barker  SG INO 49 NA NA  NA 0.435    NA 0.387   NA   NA   NA
    ## 3  1950   Leo Barnhorst  SF CHS 67 NA NA  NA 0.394    NA 0.259   NA   NA   NA
    ## 4  1950      Ed Bartels   F TOT 15 NA NA  NA 0.312    NA 0.395   NA   NA   NA
    ## 5  1950      Ed Bartels   F DNN 13 NA NA  NA 0.308    NA 0.378   NA   NA   NA
    ## 6  1950      Ed Bartels   F NYK  2 NA NA  NA 0.376    NA 0.750   NA   NA   NA
    ## 7  1950     Ralph Beard   G INO 60 NA NA  NA 0.422    NA 0.301   NA   NA   NA
    ## 8  1950      Gene Berce G-F TRI  3 NA NA  NA 0.275    NA 0.313   NA   NA   NA
    ## 9  1950   Charlie Black F-C TOT 65 NA NA  NA 0.346    NA 0.395   NA   NA   NA
    ## 10 1950   Charlie Black F-C FTW 36 NA NA  NA 0.362    NA 0.480   NA   NA   NA
    ##    AST. STL. BLK. TOV. USG. blanl  OWS  DWS   WS WS.48 blank2 OBPM DBPM BPM
    ## 1    NA   NA   NA   NA   NA    NA -0.1  3.6  3.5    NA     NA   NA   NA  NA
    ## 2    NA   NA   NA   NA   NA    NA  1.6  0.6  2.2    NA     NA   NA   NA  NA
    ## 3    NA   NA   NA   NA   NA    NA  0.9  2.8  3.6    NA     NA   NA   NA  NA
    ## 4    NA   NA   NA   NA   NA    NA -0.5 -0.1 -0.6    NA     NA   NA   NA  NA
    ## 5    NA   NA   NA   NA   NA    NA -0.5 -0.1 -0.6    NA     NA   NA   NA  NA
    ## 6    NA   NA   NA   NA   NA    NA  0.0  0.0  0.0    NA     NA   NA   NA  NA
    ## 7    NA   NA   NA   NA   NA    NA  3.6  1.2  4.8    NA     NA   NA   NA  NA
    ## 8    NA   NA   NA   NA   NA    NA -0.1  0.0 -0.1    NA     NA   NA   NA  NA
    ## 9    NA   NA   NA   NA   NA    NA -2.2  5.0  2.8    NA     NA   NA   NA  NA
    ## 10   NA   NA   NA   NA   NA    NA -0.7  2.2  1.5    NA     NA   NA   NA  NA
    ##    VORP  FG FGA   FG. X3P X3PA X3P. X2P X2PA  X2P.  eFG.  FT FTA   FT. ORB DRB
    ## 1    NA 144 516 0.279  NA   NA   NA 144  516 0.279 0.279 170 241 0.705  NA  NA
    ## 2    NA 102 274 0.372  NA   NA   NA 102  274 0.372 0.372  75 106 0.708  NA  NA
    ## 3    NA 174 499 0.349  NA   NA   NA 174  499 0.349 0.349  90 129 0.698  NA  NA
    ## 4    NA  22  86 0.256  NA   NA   NA  22   86 0.256 0.256  19  34 0.559  NA  NA
    ## 5    NA  21  82 0.256  NA   NA   NA  21   82 0.256 0.256  17  31 0.548  NA  NA
    ## 6    NA   1   4 0.250  NA   NA   NA   1    4 0.250 0.250   2   3 0.667  NA  NA
    ## 7    NA 340 936 0.363  NA   NA   NA 340  936 0.363 0.363 215 282 0.762  NA  NA
    ## 8    NA   5  16 0.313  NA   NA   NA   5   16 0.313 0.313   0   5 0.000  NA  NA
    ## 9    NA 226 813 0.278  NA   NA   NA 226  813 0.278 0.278 209 321 0.651  NA  NA
    ## 10   NA 125 435 0.287  NA   NA   NA 125  435 0.287 0.287 132 209 0.632  NA  NA
    ##    TRB AST STL BLK TOV  PF PTS
    ## 1   NA 176  NA  NA  NA 217 458
    ## 2   NA 109  NA  NA  NA  99 279
    ## 3   NA 140  NA  NA  NA 192 438
    ## 4   NA  20  NA  NA  NA  29  63
    ## 5   NA  20  NA  NA  NA  27  59
    ## 6   NA   0  NA  NA  NA   2   4
    ## 7   NA 233  NA  NA  NA 132 895
    ## 8   NA   2  NA  NA  NA   6  10
    ## 9   NA 163  NA  NA  NA 273 661
    ## 10  NA  75  NA  NA  NA 140 382

### a new dataset from the original dataset that includes the year, the player name, and age.

``` r
data %>% 
  select(Year, Player, Age) -> data2
head(data2, 10)
```

    ##    Year          Player Age
    ## 1  1950 Curly Armstrong  31
    ## 2  1950    Cliff Barker  29
    ## 3  1950   Leo Barnhorst  25
    ## 4  1950      Ed Bartels  24
    ## 5  1950      Ed Bartels  24
    ## 6  1950      Ed Bartels  24
    ## 7  1950     Ralph Beard  22
    ## 8  1950      Gene Berce  23
    ## 9  1950   Charlie Black  28
    ## 10 1950   Charlie Black  28

## add a new column to both datasets called mergeid that includes a sequence of numbers beginning with a 1 in the first row of the data and ending with the total number of rows in the last row of the data

``` r
data1$mergeid <- seq(1,nrow(data1),1)

data2$mergeid <- seq(1,nrow(data2),1)
```

## Join the two datasets from question (6) together to recreate the original dataset plus the new merge id.

``` r
new_data <- merge(data1, data2, by = "mergeid")
head(new_data, 10)
```

    ##    mergeid Year.x        Player.x Pos  Tm  G GS MP PER   TS. X3PAr   FTr ORB.
    ## 1        1   1950 Curly Armstrong G-F FTW 63 NA NA  NA 0.368    NA 0.467   NA
    ## 2        2   1950    Cliff Barker  SG INO 49 NA NA  NA 0.435    NA 0.387   NA
    ## 3        3   1950   Leo Barnhorst  SF CHS 67 NA NA  NA 0.394    NA 0.259   NA
    ## 4        4   1950      Ed Bartels   F TOT 15 NA NA  NA 0.312    NA 0.395   NA
    ## 5        5   1950      Ed Bartels   F DNN 13 NA NA  NA 0.308    NA 0.378   NA
    ## 6        6   1950      Ed Bartels   F NYK  2 NA NA  NA 0.376    NA 0.750   NA
    ## 7        7   1950     Ralph Beard   G INO 60 NA NA  NA 0.422    NA 0.301   NA
    ## 8        8   1950      Gene Berce G-F TRI  3 NA NA  NA 0.275    NA 0.313   NA
    ## 9        9   1950   Charlie Black F-C TOT 65 NA NA  NA 0.346    NA 0.395   NA
    ## 10      10   1950   Charlie Black F-C FTW 36 NA NA  NA 0.362    NA 0.480   NA
    ##    DRB. TRB. AST. STL. BLK. TOV. USG. blanl  OWS  DWS   WS WS.48 blank2 OBPM
    ## 1    NA   NA   NA   NA   NA   NA   NA    NA -0.1  3.6  3.5    NA     NA   NA
    ## 2    NA   NA   NA   NA   NA   NA   NA    NA  1.6  0.6  2.2    NA     NA   NA
    ## 3    NA   NA   NA   NA   NA   NA   NA    NA  0.9  2.8  3.6    NA     NA   NA
    ## 4    NA   NA   NA   NA   NA   NA   NA    NA -0.5 -0.1 -0.6    NA     NA   NA
    ## 5    NA   NA   NA   NA   NA   NA   NA    NA -0.5 -0.1 -0.6    NA     NA   NA
    ## 6    NA   NA   NA   NA   NA   NA   NA    NA  0.0  0.0  0.0    NA     NA   NA
    ## 7    NA   NA   NA   NA   NA   NA   NA    NA  3.6  1.2  4.8    NA     NA   NA
    ## 8    NA   NA   NA   NA   NA   NA   NA    NA -0.1  0.0 -0.1    NA     NA   NA
    ## 9    NA   NA   NA   NA   NA   NA   NA    NA -2.2  5.0  2.8    NA     NA   NA
    ## 10   NA   NA   NA   NA   NA   NA   NA    NA -0.7  2.2  1.5    NA     NA   NA
    ##    DBPM BPM VORP  FG FGA   FG. X3P X3PA X3P. X2P X2PA  X2P.  eFG.  FT FTA   FT.
    ## 1    NA  NA   NA 144 516 0.279  NA   NA   NA 144  516 0.279 0.279 170 241 0.705
    ## 2    NA  NA   NA 102 274 0.372  NA   NA   NA 102  274 0.372 0.372  75 106 0.708
    ## 3    NA  NA   NA 174 499 0.349  NA   NA   NA 174  499 0.349 0.349  90 129 0.698
    ## 4    NA  NA   NA  22  86 0.256  NA   NA   NA  22   86 0.256 0.256  19  34 0.559
    ## 5    NA  NA   NA  21  82 0.256  NA   NA   NA  21   82 0.256 0.256  17  31 0.548
    ## 6    NA  NA   NA   1   4 0.250  NA   NA   NA   1    4 0.250 0.250   2   3 0.667
    ## 7    NA  NA   NA 340 936 0.363  NA   NA   NA 340  936 0.363 0.363 215 282 0.762
    ## 8    NA  NA   NA   5  16 0.313  NA   NA   NA   5   16 0.313 0.313   0   5 0.000
    ## 9    NA  NA   NA 226 813 0.278  NA   NA   NA 226  813 0.278 0.278 209 321 0.651
    ## 10   NA  NA   NA 125 435 0.287  NA   NA   NA 125  435 0.287 0.287 132 209 0.632
    ##    ORB DRB TRB AST STL BLK TOV  PF PTS Year.y        Player.y Age
    ## 1   NA  NA  NA 176  NA  NA  NA 217 458   1950 Curly Armstrong  31
    ## 2   NA  NA  NA 109  NA  NA  NA  99 279   1950    Cliff Barker  29
    ## 3   NA  NA  NA 140  NA  NA  NA 192 438   1950   Leo Barnhorst  25
    ## 4   NA  NA  NA  20  NA  NA  NA  29  63   1950      Ed Bartels  24
    ## 5   NA  NA  NA  20  NA  NA  NA  27  59   1950      Ed Bartels  24
    ## 6   NA  NA  NA   0  NA  NA  NA   2   4   1950      Ed Bartels  24
    ## 7   NA  NA  NA 233  NA  NA  NA 132 895   1950     Ralph Beard  22
    ## 8   NA  NA  NA   2  NA  NA  NA   6  10   1950      Gene Berce  23
    ## 9   NA  NA  NA 163  NA  NA  NA 273 661   1950   Charlie Black  28
    ## 10  NA  NA  NA  75  NA  NA  NA 140 382   1950   Charlie Black  28

## Subset the original dataset to 1995. Group the data by year and team name and then summarize the average number of points per team. Arrange from most to least points.

``` r
data %>% filter(Year==1995) %>% group_by(Year, Tm) %>% summarize(avg_pts = mean(PTS)) %>% arrange(desc(avg_pts)) -> data3
```

    ## `summarise()` has grouped output by 'Year'. You can override using the `.groups` argument.

``` r
head(data3, 10)
```

    ## # A tibble: 10 x 3
    ## # Groups:   Year [1]
    ##     Year Tm    avg_pts
    ##    <int> <chr>   <dbl>
    ##  1  1995 SEA      647.
    ##  2  1995 ORL      606.
    ##  3  1995 PHO      605.
    ##  4  1995 DAL      604.
    ##  5  1995 MIL      582.
    ##  6  1995 UTA      582.
    ##  7  1995 MIA      553.
    ##  8  1995 SAS      546.
    ##  9  1995 IND      542.
    ## 10  1995 LAL      538.

## Reshape the data in the previous question into a wide format using the tidyr package. Create a wide dataset that keeps year in a single column, but spreads team names to multiple individual columns with each column delineating points per team in 1995.

``` r
data3 %>% spread(Tm, avg_pts) -> data4
head(data4, 10)
```

    ## # A tibble: 1 x 29
    ## # Groups:   Year [1]
    ##    Year   ATL   BOS   CHH   CHI   CLE   DAL   DEN   DET   GSW   HOU   IND   LAC
    ##   <int> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    ## 1  1995  440.  496.  516.  520.  494.  604.  489.  503.  482.  499.  542.  495.
    ## # ... with 16 more variables: LAL <dbl>, MIA <dbl>, MIL <dbl>, MIN <dbl>,
    ## #   NJN <dbl>, NYK <dbl>, ORL <dbl>, PHI <dbl>, PHO <dbl>, POR <dbl>,
    ## #   SAC <dbl>, SAS <dbl>, SEA <dbl>, TOT <dbl>, UTA <dbl>, WSB <dbl>

## Now return the data to a long (tidy) format by moving teams back into a single column and points in a single column.

``` r
data4 %>% gather(Tm, avg_pts, -Year) -> data5
head(data5, 10)
```

    ## # A tibble: 10 x 3
    ## # Groups:   Year [1]
    ##     Year Tm    avg_pts
    ##    <int> <chr>   <dbl>
    ##  1  1995 ATL      440.
    ##  2  1995 BOS      496.
    ##  3  1995 CHH      516.
    ##  4  1995 CHI      520.
    ##  5  1995 CLE      494.
    ##  6  1995 DAL      604.
    ##  7  1995 DEN      489.
    ##  8  1995 DET      503.
    ##  9  1995 GSW      482.
    ## 10  1995 HOU      499.
