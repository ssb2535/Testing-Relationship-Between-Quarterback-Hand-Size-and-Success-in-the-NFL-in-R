Quarterback Success Based on Hand Size, Height, and Thrown Yards
================
Sarabnidhan Bains
3/22/2021

## Introduction

For this project, the hand size and height of a quarterback will be
evaluated to see if it affected the quarterback’s ability to succeed in
the NFL. Some of the information was gathered from the project I had
completed in SDS 328M. In addition, more data was combined with data
from a pro football stastics website. This dataset contains statistics
from the majority of all relevant quarterbacks from the past 20 years.
My final sample size is 60 quarterbacks, some of which had to be removed
due to injuries or other outlying factors that massively affected their
data. In the National Football League, a large emphasis is often placed
upon hand size and height of a quarterback when they are being evaluated
to be drafted to professional teams. The data collection was done
through a few websites that have the measurements for quarterback hand
size (inches) and height (inches) on record. The success they have
achieved in the league is being measured by yards thrown per game and
whether the quarterback has an appearance in the Pro Bowl (if the
quarterback makes an appearance in the Pro Bowl, he is usually one of
the five best quarterbacks in that year). My motivation for choosing
this topic is my passion for the sport of football. This data can be
used for informational purposes or could even be used to help gauge
future incoming quarterbacks if a correlation was found.

## Tidying and Merging

No tidying was needed for the data sets. To merge the data sets, I used
the right join function as it returns all the rows of the table on the
right side of the join and combines the rows for the matching variables
on the left side of data sets.

``` r
footballmeasurements <- read.csv("~/Desktop/footballmeasurements.csv")
footballyards <- read.csv("~/Desktop/footballyards.csv")
joinedfootball <- right_join(footballmeasurements, footballyards)
```

    ## Joining, by = "Player"

``` r
joinedfootball
```

    ##            Player   hand height yards Probowl
    ## 1         Bortles  9.375     77 226.3       0
    ## 2  Deshaun Watson  9.750     74 255.7       1
    ## 3      Josh Allen 10.125     77 184.4       1
    ## 4         Mariota  9.875     76 209.6       0
    ## 5           Wentz 10.000     77 253.4       1
    ## 6         Winston  9.375     76 274.1       1
    ## 7            Goff  9.000     76 263.3       1
    ## 8         Darnold  9.250     75 226.5       0
    ## 9      Derek Carr  9.125     75 242.5       1
    ## 10       Brissett  9.750     76 169.5       0
    ## 11   Dak Prescott 10.875     74 246.5       1
    ## 12   Paxton Lynch 10.375     79 158.4       0
    ## 13   Cody Kessler 10.250     73 130.3       0
    ## 14       Mayfield  9.875     73 251.7       0
    ## 15        Manziel  9.875     72 111.7       0
    ## 16        Siemian  9.875     75 210.7       0
    ## 17          Rosen  9.875     76 142.3       0
    ## 18          Kizer  9.875     76 171.2       0
    ## 19     Geno Smith  9.250     75 154.6       0
    ## 20         Savage  9.625     76 153.8       0
    ## 21       Trubisky  9.500     74 208.6       1
    ## 22  Lamar Jackson  9.500     74 139.6       1
    ## 23    CJ Beathard  9.375     74 206.3       0
    ## 24        Mahomes  9.250     75 303.6       1
    ## 25      Garoppolo  9.250     74 165.4       0
    ## 26    Bridgewater  9.250     74 173.9       1
    ## 27          Foles 10.625     78 205.2       1
    ## 28          Brees 10.250     72 281.5       1
    ## 29         Wilson 10.250     71 232.3       1
    ## 30   Tyrod Taylor 10.000     73 136.6       1
    ## 31       Stafford 10.000     75 275.3       1
    ## 32         Newton  9.875     77 232.3       1
    ## 33        Cousins  9.875     75 259.2       1
    ## 34         Flacco  9.625     78 234.3       0
    ## 35           Ryan  9.500     76 270.8       1
    ## 36         Dalton  9.500     74 237.5       1
    ## 37         Cutler  9.375     75 229.6       1
    ## 38          Brady  9.375     76 261.7       1
    ## 39 Roethlisberger  9.375     77 259.4       1
    ## 40         Rivers  9.250     77 260.0       1
    ## 41     Alex Smith  9.250     76 205.2       1
    ## 42    Case Keenum  9.125     73 214.4       0
    ## 43    Eli Manning  9.125     77 241.6       1
    ## 44    Josh Mccown  9.000     76 173.8       0
    ## 45        Rodgers 10.125     74 259.4       1
    ## 46         Palmer  9.875     77 254.1       1
    ## 47      Tannehill  9.000     76 231.8       1
    ## 48          Yates 10.250     76 126.5       0
    ## 49        Sanchez 10.500     74 194.4       0
    ## 50          Tebow 10.125     74 123.5       0
    ## 51           Luck 10.000     76 275.2       1
    ## 52    Fitzpatrick 10.750     74 210.8       0
    ## 53          Favre 10.375     74 237.9       1
    ## 54         Locker  9.625     74 165.6       0
    ## 55        Glennon  9.625     79 178.0       0
    ## 56     Kaepernick  9.125     76 177.8       0
    ## 57       Osweiler  9.875     79 151.4       0
    ## 58          McCoy  9.375     73 155.9       0
    ## 59       Griffin   9.500     74 177.5       1
    ## 60       Bradford  9.500     76 234.3       0

## Core dplyr Functions and Summary Statistics

The select function allowed me to focus in on the useful information in
the data set.

``` r
summary(select(joinedfootball, hand, height, yards, Probowl))
```

    ##       hand            height          yards          Probowl      
    ##  Min.   : 9.000   Min.   :71.00   Min.   :111.7   Min.   :0.0000  
    ##  1st Qu.: 9.375   1st Qu.:74.00   1st Qu.:170.8   1st Qu.:0.0000  
    ##  Median : 9.625   Median :75.00   Median :212.6   Median :1.0000  
    ##  Mean   : 9.708   Mean   :75.25   Mean   :210.0   Mean   :0.5333  
    ##  3rd Qu.:10.000   3rd Qu.:76.00   3rd Qu.:252.1   3rd Qu.:1.0000  
    ##  Max.   :10.875   Max.   :79.00   Max.   :303.6   Max.   :1.0000

The mean hand size of the data set is 9.708 inches. The mean height is
75.25 inches. The mean yards per game is 210 yards.The amount of Pro
Bowler quarterbacks is slightly more than non Pro Bowlers.

Using the filter function, 2 subsets were created based upon whether the
quarterback has larger or smaller hands compared to the average.

``` r
largehands <- filter(joinedfootball, hand > 9.7)
smallhands <- filter(joinedfootball, hand < 9.7)
lhnumeric <- select(largehands, hand, height, yards, Probowl)
shnumeric <- select(smallhands, hand, height, yards, Probowl)
summary(lhnumeric)
```

    ##       hand            height          yards          Probowl      
    ##  Min.   : 9.750   Min.   :71.00   Min.   :111.7   Min.   :0.0000  
    ##  1st Qu.: 9.875   1st Qu.:74.00   1st Qu.:158.4   1st Qu.:0.0000  
    ##  Median :10.000   Median :75.00   Median :210.7   Median :1.0000  
    ##  Mean   :10.108   Mean   :75.07   Mean   :205.2   Mean   :0.5172  
    ##  3rd Qu.:10.250   3rd Qu.:76.00   3rd Qu.:253.4   3rd Qu.:1.0000  
    ##  Max.   :10.875   Max.   :79.00   Max.   :281.5   Max.   :1.0000

In quarterbacks with hand size of more than 9.7 inches, the average
yards per game is 205.2 yards, with an almost even amount of Pro Bowlers
and non Pro Bowlers.

``` r
summary(shnumeric)
```

    ##       hand           height          yards          Probowl      
    ##  Min.   :9.000   Min.   :73.00   Min.   :139.6   Min.   :0.0000  
    ##  1st Qu.:9.250   1st Qu.:74.00   1st Qu.:175.7   1st Qu.:0.0000  
    ##  Median :9.375   Median :76.00   Median :226.3   Median :1.0000  
    ##  Mean   :9.335   Mean   :75.42   Mean   :214.4   Mean   :0.5484  
    ##  3rd Qu.:9.500   3rd Qu.:76.00   3rd Qu.:242.1   3rd Qu.:1.0000  
    ##  Max.   :9.625   Max.   :79.00   Max.   :303.6   Max.   :1.0000

In quarterbacks with hand size of less than 9.7 inches, the average
yards per game is 214.4 yards, an increase from quarterbacks with large
hands. In addition to that, there is a higher ratio of Pro Bowlers to
non Pro Bowlers.

Using the filter and select function, another 2 subsets were made, with
tall quarterbacks listed as above the mean height and short quarterbacks
below the mean.

``` r
tall <- filter(joinedfootball, height >= 75.25)
short <- filter(joinedfootball, height < 75.25)
tnumeric <- select(tall, hand, height, yards, Probowl)
snumeric <- select(short, hand, height, yards, Probowl)
summary(tnumeric)
```

    ##       hand            height          yards          Probowl      
    ##  Min.   : 9.000   Min.   :76.00   Min.   :126.5   Min.   :0.0000  
    ##  1st Qu.: 9.375   1st Qu.:76.00   1st Qu.:173.8   1st Qu.:0.0000  
    ##  Median : 9.625   Median :76.00   Median :226.3   Median :1.0000  
    ##  Mean   : 9.638   Mean   :76.72   Mean   :213.1   Mean   :0.5172  
    ##  3rd Qu.: 9.875   3rd Qu.:77.00   3rd Qu.:254.1   3rd Qu.:1.0000  
    ##  Max.   :10.625   Max.   :79.00   Max.   :275.2   Max.   :1.0000

In quarterbacks above 75.25 inches tall, the average yards per game is
213.1 yards, with an almost even amount of Pro Bowlers and non Pro
Bowlers.

``` r
summary(snumeric)
```

    ##       hand            height          yards          Probowl      
    ##  Min.   : 9.125   Min.   :71.00   Min.   :111.7   Min.   :0.0000  
    ##  1st Qu.: 9.375   1st Qu.:73.50   1st Qu.:165.5   1st Qu.:0.0000  
    ##  Median : 9.750   Median :74.00   Median :210.8   Median :1.0000  
    ##  Mean   : 9.774   Mean   :73.87   Mean   :207.1   Mean   :0.5484  
    ##  3rd Qu.:10.125   3rd Qu.:74.50   3rd Qu.:244.5   3rd Qu.:1.0000  
    ##  Max.   :10.875   Max.   :75.00   Max.   :303.6   Max.   :1.0000

In quarterbacks below 75.25 inches, the mean was 207.1 yards per game,
lower than tall quarterbacks. In addition to that, there is a higher
ratio of Pro Bowlers to non Pro Bowlers.

Using the arrange feature, a subset was created for the 20 quarterbacks
with the highest yards per game in a descending order.

``` r
x <- arrange(joinedfootball, desc(yards))
mostyards <- filter(x, yards >= 237.8)
summary(select(mostyards, hand, height, yards, Probowl))
```

    ##       hand            height          yards          Probowl    
    ##  Min.   : 9.000   Min.   :72.00   Min.   :237.9   Min.   :0.00  
    ##  1st Qu.: 9.344   1st Qu.:74.00   1st Qu.:253.0   1st Qu.:1.00  
    ##  Median : 9.812   Median :75.50   Median :259.4   Median :1.00  
    ##  Mean   : 9.719   Mean   :75.30   Mean   :261.3   Mean   :0.95  
    ##  3rd Qu.:10.000   3rd Qu.:76.25   3rd Qu.:271.6   3rd Qu.:1.00  
    ##  Max.   :10.875   Max.   :77.00   Max.   :303.6   Max.   :1.00

The mean of these quarterbacks had an average hand size of 9.719 inches
and average height of 75.3 inches, both only very slightly above the
averages. All but one of these quarterbacks were Pro Bowlers.

The group by and summarise functions were used to confirm the averages
of the quarterbacks’ hand size and heights, with it being 9.708 inches
and 75.25 inches respectively.

``` r
pro <- group_by(joinedfootball, Probowl)
probowl <- summarise(joinedfootball,
                     count = n(),
                     hand = mean(hand),
                     height = mean(height))
probowl
```

    ##   count     hand height
    ## 1    60 9.708333  75.25

The mutate function was used to make another variable to determine the
eye height of the quarterbacks. The eye height is a more accurate
measurement of the quarterback but is not readily available. However, an
average human adult male has 4 inches between the top of the head and
the eyes. The new variable contains all the heights of the quarterbacks
subtracted by 4 inches.

``` r
eyeheightfootball <- mutate(joinedfootball, 
       eyeheight = height - 4)
summary(select(eyeheightfootball, hand, eyeheight, height, yards, Probowl))
```

    ##       hand          eyeheight         height          yards      
    ##  Min.   : 9.000   Min.   :67.00   Min.   :71.00   Min.   :111.7  
    ##  1st Qu.: 9.375   1st Qu.:70.00   1st Qu.:74.00   1st Qu.:170.8  
    ##  Median : 9.625   Median :71.00   Median :75.00   Median :212.6  
    ##  Mean   : 9.708   Mean   :71.25   Mean   :75.25   Mean   :210.0  
    ##  3rd Qu.:10.000   3rd Qu.:72.00   3rd Qu.:76.00   3rd Qu.:252.1  
    ##  Max.   :10.875   Max.   :75.00   Max.   :79.00   Max.   :303.6  
    ##     Probowl      
    ##  Min.   :0.0000  
    ##  1st Qu.:0.0000  
    ##  Median :1.0000  
    ##  Mean   :0.5333  
    ##  3rd Qu.:1.0000  
    ##  Max.   :1.0000

The summary statistics will all remain the same as the original dataset.
The only exception is the eye height summary statistics, which are the
same as the height summary statistics except subtracted by 4 inches.

The filter function was used to separate the Pro Bowler and non Pro Bowl
quarterbacks.

``` r
yes <- filter(joinedfootball, Probowl == "y")
no <- filter(joinedfootball, Probowl == "n")
summary(select(yes, hand, height, yards, Probowl))
```

    ##       hand         height        yards        Probowl   
    ##  Min.   : NA   Min.   : NA   Min.   : NA   Min.   : NA  
    ##  1st Qu.: NA   1st Qu.: NA   1st Qu.: NA   1st Qu.: NA  
    ##  Median : NA   Median : NA   Median : NA   Median : NA  
    ##  Mean   :NaN   Mean   :NaN   Mean   :NaN   Mean   :NaN  
    ##  3rd Qu.: NA   3rd Qu.: NA   3rd Qu.: NA   3rd Qu.: NA  
    ##  Max.   : NA   Max.   : NA   Max.   : NA   Max.   : NA

For the Pro Bowler quarterbacks, the average hand size was 9.695 inches
and average height was 75.19 inches. Both figures surprisingly are below
the average for the entire dataset.

``` r
summary(select(no, hand, height, yards, Probowl))
```

    ##       hand         height        yards        Probowl   
    ##  Min.   : NA   Min.   : NA   Min.   : NA   Min.   : NA  
    ##  1st Qu.: NA   1st Qu.: NA   1st Qu.: NA   1st Qu.: NA  
    ##  Median : NA   Median : NA   Median : NA   Median : NA  
    ##  Mean   :NaN   Mean   :NaN   Mean   :NaN   Mean   :NaN  
    ##  3rd Qu.: NA   3rd Qu.: NA   3rd Qu.: NA   3rd Qu.: NA  
    ##  Max.   : NA   Max.   : NA   Max.   : NA   Max.   : NA

For the Pro Bowler quarterbacks, the average hand size was 9.723 inches
and average height was 75.32 inches. Both figures surprisingly are above
the average for the Pro Bowlers and the entire dataset.

## Correlation

A correlation test was run to view the correlation between numeric
variables in the dataset.

``` r
numeric <- select(joinedfootball, hand, height, yards)
cor(numeric)
```

    ##              hand      height       yards
    ## hand    1.0000000 -0.11873434 -0.10643548
    ## height -0.1187343  1.00000000  0.07990915
    ## yards  -0.1064355  0.07990915  1.00000000

The test showed no significant correlation between any of the variables,
with no value over 0.12 in the positive or negative direction.

## Visualization

A heat map was created using hand size and height as the two axis
variables and yards per game as the intensity of the color. Overall, the
heat map does not show any pattern or correlation that is discernible.

``` r
ggplot(data = numeric, mapping = aes(x = hand,
                                       y = height,
                                       fill = yards)) +
  geom_tile(color="red") +
  xlab(label = "hand size")
```

![](Part1_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

``` r
summary(select(numeric, hand, height, yards))
```

    ##       hand            height          yards      
    ##  Min.   : 9.000   Min.   :71.00   Min.   :111.7  
    ##  1st Qu.: 9.375   1st Qu.:74.00   1st Qu.:170.8  
    ##  Median : 9.625   Median :75.00   Median :212.6  
    ##  Mean   : 9.708   Mean   :75.25   Mean   :210.0  
    ##  3rd Qu.:10.000   3rd Qu.:76.00   3rd Qu.:252.1  
    ##  Max.   :10.875   Max.   :79.00   Max.   :303.6

A boxplot was created to compare the quarterbacks’ height against
whether or not they were a Pro Bowler. Again, no discernible pattern was
found and surprisingly, the non Pro Bowlers seemed to be slightly taller
overall than the Pro Bowlers.

``` r
ggplot(joinedfootball, 
       aes(x = Probowl, 
           y = height)) +
  geom_boxplot(color="blue") +
  labs(title = "Height Distribution Based on Pro Bowl Appearance")
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](Part1_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

``` r
summary(select(joinedfootball, height, yards))
```

    ##      height          yards      
    ##  Min.   :71.00   Min.   :111.7  
    ##  1st Qu.:74.00   1st Qu.:170.8  
    ##  Median :75.00   Median :212.6  
    ##  Mean   :75.25   Mean   :210.0  
    ##  3rd Qu.:76.00   3rd Qu.:252.1  
    ##  Max.   :79.00   Max.   :303.6

Another boxplot was created to compare the quarterbacks’ hand size
against whether or not they were a Pro Bowler. Again, no discernible
pattern was found.

``` r
ggplot(joinedfootball, 
       aes(x = Probowl, 
           y = hand)) +
  geom_boxplot(color="green") +
  labs(title = "Hand Size Distribution Based on Pro Bowl Appearance")
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](Part1_files/figure-gfm/unnamed-chunk-15-1.png)<!-- -->

``` r
summary(select(joinedfootball, hand, yards))
```

    ##       hand            yards      
    ##  Min.   : 9.000   Min.   :111.7  
    ##  1st Qu.: 9.375   1st Qu.:170.8  
    ##  Median : 9.625   Median :212.6  
    ##  Mean   : 9.708   Mean   :210.0  
    ##  3rd Qu.:10.000   3rd Qu.:252.1  
    ##  Max.   :10.875   Max.   :303.6

## Dimensionality Reduction

A k-means clustering was conducted on the data set containing the
numeric variables.

``` r
kmeans1 <- numeric %>% kmeans(2)
fviz_cluster(kmeans1, data = numeric,
              geom = "point",
              ellipse.type = "convex", 
              ggtheme = theme_bw()
)
```

![](Part1_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

``` r
kmeans1
```

    ## K-means clustering with 2 clusters of sizes 23, 37
    ## 
    ## Cluster means:
    ##       hand   height    yards
    ## 1 9.739130 75.21739 157.2217
    ## 2 9.689189 75.27027 242.7730
    ## 
    ## Clustering vector:
    ##  [1] 2 2 1 2 2 2 2 2 2 1 2 1 1 2 1 2 1 1 1 1 2 1 2 2 1 1 2 2 2 1 2 2 2 2 2 2 2 2
    ## [39] 2 2 2 2 2 1 2 2 2 1 1 1 2 2 2 1 1 1 1 1 1 2
    ## 
    ## Within cluster sum of squares by cluster:
    ## [1] 10405.34 22103.08
    ##  (between_SS / total_SS =  76.2 %)
    ## 
    ## Available components:
    ## 
    ## [1] "cluster"      "centers"      "totss"        "withinss"     "tot.withinss"
    ## [6] "betweenss"    "size"         "iter"         "ifault"
