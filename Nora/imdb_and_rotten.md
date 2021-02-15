IMDb Rating and Rotten Tomatoes
================

``` r
getwd()
```

    ## [1] "/Users/Luna/Desktop/Movie/the-avocados-movies/Nora"

``` r
table <- read.csv("/Users/Luna/Desktop/Movie/the-avocados-movies/resources/MoviesOnStreamingPlatforms_updated.csv")
#table$Rotten.Tomatoes <- as.numeric(table$Rotten.Tomatoes) * 100
head(table, n = 20)
```

    ##     X ID                              Title Year Age IMDb Rotten.Tomatoes
    ## 1   0  1                          Inception 2010 13+  8.8             87%
    ## 2   1  2                         The Matrix 1999 18+  8.7             87%
    ## 3   2  3             Avengers: Infinity War 2018 13+  8.5             84%
    ## 4   3  4                 Back to the Future 1985  7+  8.5             96%
    ## 5   4  5     The Good, the Bad and the Ugly 1966 18+  8.8             97%
    ## 6   5  6  Spider-Man: Into the Spider-Verse 2018  7+  8.4             97%
    ## 7   6  7                        The Pianist 2002 18+  8.5             95%
    ## 8   7  8                   Django Unchained 2012 18+  8.4             87%
    ## 9   8  9            Raiders of the Lost Ark 1981  7+  8.4             95%
    ## 10  9 10               Inglourious Basterds 2009 18+  8.3             89%
    ## 11 10 11                        Taxi Driver 1976 18+  8.3             95%
    ## 12 11 12                           3 Idiots 2009 13+  8.4            100%
    ## 13 12 13                    Pan's Labyrinth 2006 18+  8.2             95%
    ## 14 13 14                               Room 2015 18+  8.1             93%
    ## 15 14 15    Monty Python and the Holy Grail 1975  7+  8.2             97%
    ## 16 15 16       Once Upon a Time in the West 1968 13+  8.5             95%
    ## 17 16 17 Indiana Jones and the Last Crusade 1989 13+  8.2             88%
    ## 18 17 18                      Groundhog Day 1993  7+  8.0             96%
    ## 19 18 19                  The King's Speech 2010 18+  8.0             95%
    ## 20 19 20                                Her 2013 18+  8.0             95%
    ##    Netflix Hulu Prime.Video Disney. Type
    ## 1        1    0           0       0    0
    ## 2        1    0           0       0    0
    ## 3        1    0           0       0    0
    ## 4        1    0           0       0    0
    ## 5        1    0           1       0    0
    ## 6        1    0           0       0    0
    ## 7        1    0           1       0    0
    ## 8        1    0           0       0    0
    ## 9        1    0           0       0    0
    ## 10       1    0           0       0    0
    ## 11       1    0           0       0    0
    ## 12       1    0           1       0    0
    ## 13       1    0           0       0    0
    ## 14       1    0           0       0    0
    ## 15       1    0           0       0    0
    ## 16       1    0           1       0    0
    ## 17       1    0           0       0    0
    ## 18       1    0           0       0    0
    ## 19       1    0           0       0    0
    ## 20       1    0           0       0    0
    ##                                      Directors
    ## 1                            Christopher Nolan
    ## 2               Lana Wachowski,Lilly Wachowski
    ## 3                      Anthony Russo,Joe Russo
    ## 4                              Robert Zemeckis
    ## 5                                 Sergio Leone
    ## 6  Bob Persichetti,Peter Ramsey,Rodney Rothman
    ## 7                               Roman Polanski
    ## 8                            Quentin Tarantino
    ## 9                             Steven Spielberg
    ## 10                           Quentin Tarantino
    ## 11                             Martin Scorsese
    ## 12                             Rajkumar Hirani
    ## 13                          Guillermo del Toro
    ## 14                            Lenny Abrahamson
    ## 15                   Terry Gilliam,Terry Jones
    ## 16                                Sergio Leone
    ## 17                            Steven Spielberg
    ## 18                                Harold Ramis
    ## 19                                  Tom Hooper
    ## 20                                 Spike Jonze
    ##                                      Genres
    ## 1          Action,Adventure,Sci-Fi,Thriller
    ## 2                             Action,Sci-Fi
    ## 3                   Action,Adventure,Sci-Fi
    ## 4                   Adventure,Comedy,Sci-Fi
    ## 5                                   Western
    ## 6  Animation,Action,Adventure,Family,Sci-Fi
    ## 7                 Biography,Drama,Music,War
    ## 8                             Drama,Western
    ## 9                          Action,Adventure
    ## 10                      Adventure,Drama,War
    ## 11                              Crime,Drama
    ## 12                             Comedy,Drama
    ## 13                        Drama,Fantasy,War
    ## 14                           Drama,Thriller
    ## 15                 Adventure,Comedy,Fantasy
    ## 16                                  Western
    ## 17                         Action,Adventure
    ## 18                   Comedy,Fantasy,Romance
    ## 19                  Biography,Drama,History
    ## 20                     Drama,Romance,Sci-Fi
    ##                                        Country
    ## 1                 United States,United Kingdom
    ## 2                                United States
    ## 3                                United States
    ## 4                                United States
    ## 5                     Italy,Spain,West Germany
    ## 6                                United States
    ## 7         United Kingdom,France,Poland,Germany
    ## 8                                United States
    ## 9                                United States
    ## 10                       Germany,United States
    ## 11                               United States
    ## 12                                       India
    ## 13                                Mexico,Spain
    ## 14 Ireland,Canada,United Kingdom,United States
    ## 15                              United Kingdom
    ## 16                         Italy,United States
    ## 17                               United States
    ## 18                               United States
    ## 19      United Kingdom,United States,Australia
    ## 20                               United States
    ##                                       Language Runtime
    ## 1                      English,Japanese,French     148
    ## 2                                      English     136
    ## 3                                      English     149
    ## 4                                      English     116
    ## 5                                      Italian     161
    ## 6                              English,Spanish     117
    ## 7                       English,German,Russian     150
    ## 8                English,German,French,Italian     165
    ## 9  English,German,Hebrew,Spanish,Arabic,Nepali     115
    ## 10               English,German,French,Italian     153
    ## 11                             English,Spanish     114
    ## 12                               Hindi,English     170
    ## 13                                     Spanish     118
    ## 14                                     English     118
    ## 15                        English,French,Latin      91
    ## 16                     Italian,English,Spanish     165
    ## 17                 English,German,Greek,Arabic     127
    ## 18                      English,French,Italian     101
    ## 19                                     English     118
    ## 20                                     English     126

``` r
head(table$Rotten.Tomatoes, n =20)
```

    ##  [1] 87%  87%  84%  96%  97%  97%  95%  87%  95%  89%  95%  100% 95%  93%  97% 
    ## [16] 95%  88%  96%  95%  95% 
    ## 100 Levels:  10% 100% 11% 12% 13% 14% 15% 16% 17% 18% 19% 2% 20% 21% 22% ... 99%

``` r
head(as.character(table$Rotten.Tomatoes), n = 20)
```

    ##  [1] "87%"  "87%"  "84%"  "96%"  "97%"  "97%"  "95%"  "87%"  "95%"  "89%" 
    ## [11] "95%"  "100%" "95%"  "93%"  "97%"  "95%"  "88%"  "96%"  "95%"  "95%"

``` r
head(unlist(strsplit(as.character(table$Rotten.Tomatoes), split = "%")), n = 20)
```

    ##  [1] "87"  "87"  "84"  "96"  "97"  "97"  "95"  "87"  "95"  "89"  "95"  "100"
    ## [13] "95"  "93"  "97"  "95"  "88"  "96"  "95"  "95"

``` r
rotten_ch <- as.character(table$Rotten.Tomatoes)
length(rotten_ch)
```

    ## [1] 16744

``` r
rotten_ch <- strsplit(rotten_ch, split = "%")
length(rotten_ch)
```

    ## [1] 16744

``` r
rotten_ch[1:3]
```

    ## [[1]]
    ## [1] "87"
    ## 
    ## [[2]]
    ## [1] "87"
    ## 
    ## [[3]]
    ## [1] "84"

``` r
rotten_temp <- numeric(0)

for (i in 1:16744) {
  if (length(rotten_ch[i]) == 0){
    rotten_temp <- c(rotten_temp, NA)
  } else {
    rotten_temp <- c(rotten_temp, rotten_ch[i])
  }
}

rotten_ch <- rotten_temp
length(rotten_temp)
```

    ## [1] 16744

``` r
rotten_ch <- as.numeric(rotten_ch) / 100
length(rotten_ch)
```

    ## [1] 16744

``` r
table$Rotten.Tomatoes <- rotten_ch
```

``` r
netflix <- table[table$Netflix == 1,]
hist(netflix$IMDb)
```

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
mean(netflix$IMDb, na.rm = TRUE)
```

    ## [1] 6.252963

``` r
mode(netflix$IMDb)
```

    ## [1] "numeric"

``` r
hulu <- table[table$Hulu == 1,]
hist(hulu$IMDb)
```

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
mean(hulu$IMDb, na.rm = TRUE)
```

    ## [1] 6.138117

``` r
mode(hulu$IMDb)
```

    ## [1] "numeric"

``` r
prime <- table[table$Prime.Video == 1,]
hist(prime$IMDb)
```

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

``` r
mean(prime$IMDb, na.rm = TRUE)
```

    ## [1] 5.77091

``` r
mode(prime$IMDb)
```

    ## [1] "numeric"

``` r
disney <- table[table$Disney. == 1,]
hist(disney$IMDb)
```

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
mean(disney$IMDb, na.rm = TRUE)
```

    ## [1] 6.441385

``` r
mode(disney$IMDb)
```

    ## [1] "numeric"

``` r
#par(mfrow = c(1, 4))
hist(netflix$IMDb, main = 'IMDb Rating', xlab = 'IMDb',
     prob = FALSE, density = 20, col = "red",
     ylim = c(0, 2000))
hist(hulu$IMDb, main = 'hulu', add = TRUE,
     prob = FALSE, density = 20, col = "blue",)
hist(prime$IMDb, main = 'prime', add = TRUE,
     prob = FALSE, density = 20, col = "green",)
hist(disney$IMDb, main = 'disney', add = TRUE,
     prob = FALSE, density = 20, col = "yellow",)

legend("topleft", c("Netflix", "Hulu", 'Prime', 'Disney+'), density = c(20, 20, 20, 20),
fill = c("red", "blue", "green", "yellow"), inset = 0.05)
```

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

``` r
# convert the rotten tomatoes from factor to numeric

hist(netflix$Rotten.Tomatoes, main = 'Rotten Tomatoes', xlab = 'Rotten Tomatoes',
     prob = FALSE, density = 20, col = "red",
     ylim = c(0, 2000))
hist(hulu$Rotten.Tomatoes, main = 'hulu', add = TRUE,
     prob = FALSE, density = 20, col = "blue",)
hist(prime$Rotten.Tomatoes, main = 'prime', add = TRUE,
     prob = FALSE, density = 20, col = "green",)
hist(disney$Rotten.Tomatoes, main = 'disney', add = TRUE,
     prob = FALSE, density = 20, col = "yellow",)

legend("topleft", c("Netflix", "Hulu", 'Prime', 'Disney+'), density = c(20, 20, 20, 20),
fill = c("red", "blue", "green", "yellow"), inset = 0.05)
```

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

``` r
par(mfrow = c(1, 4))
boxplot(netflix$IMDb)
boxplot(hulu$IMDb)
boxplot(prime$IMDb)
boxplot(prime$IMDb)
```

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

``` r
mode(netflix$IMDb)
```

    ## [1] "numeric"

``` r
library(ggplot2)
```

``` r
imbd <- data.frame("Platform" = c(), "IMDb" = c())
df_netflix <- data.frame("Platform" = "Netflix", "IMDb" = netflix$IMDb)
df_hulu <- data.frame("Platform" = "Hulu", "IMDb" = hulu$IMDb)
df_prime <- data.frame("Platform" = "Prime", "IMDb" = prime$IMDb)
df_disney <- data.frame("Platform" = "Disney+", "IMDb" = disney$IMDb)
imdb <- rbind(df_netflix, df_hulu, df_prime, df_disney)
```

``` r
p1 <- ggplot(imdb, aes(x=Platform, y=IMDb)) + 
  geom_boxplot()
p1 <- p1 + ggtitle("IMDB of movies on four platforms")
```

``` r
df_mean <- data.frame("Platform" = c("Netflix", "Hulu", "Prime", "Disney+"), "Mean" = c(mean(netflix$IMDb, na.rm = TRUE), mean(hulu$IMDb, na.rm = TRUE), mean(prime$IMDb, na.rm = TRUE), mean(disney$IMDb, na.rm = TRUE)))

p<-ggplot(data=df_mean, aes(x=Platform, y=Mean)) +
  geom_bar(stat="identity") + geom_text(aes(label=Mean), vjust=-0.3, size=3.5)
p
```

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

``` r
action <- factor(c('Action'))
table$Genres[1]
```

    ## [1] Action,Adventure,Sci-Fi,Thriller
    ## 1910 Levels:  Action Action,Adventure ... Western,War

``` r
'Action' %in% as.character(table$Genres[1])
```

    ## [1] FALSE

``` r
temp <- as.character(table$Genres[1])
temp <- unlist(strsplit(temp, split = ","))
temp[1]
```

    ## [1] "Action"

``` r
any("Action" == temp)
```

    ## [1] TRUE

``` r
haha <- table[1,]
```

``` r
# action movies
action_movies <- data.frame()
for (i in 1:16744){
  movie_to_test <- table[i,]
  genre <- as.character(movie_to_test$Genres)
  genre <- unlist(strsplit(genre, split = ","))
  if (any("Action" == genre)){
    action_movies <- rbind(action_movies, movie_to_test)
  }
}


action_netflix <- table[action_movies$Netflix == 1,]
action_hulu <- table[action_movies$Hulu == 1,]
action_prime <- table[action_movies$Prime.Video == 1,]
action_disney <- table[action_movies$Disney. == 1,]

df_action_imdb <- data.frame("Platform" = c(), "IMDb" = c())
df_action_netflix <- data.frame("Platform" = "Netflix", "IMDb" = action_netflix$IMDb)
df_action_hulu <- data.frame("Platform" = "Hulu", "IMDb" = action_hulu$IMDb)
df_action_prime <- data.frame("Platform" = "Prime", "IMDb" = action_prime$IMDb)
df_action_disney <- data.frame("Platform" = "Disney+", "IMDb" = action_disney$IMDb)
df_action_imdb <- rbind(df_action_netflix, df_action_hulu, df_action_prime, df_action_disney)

p2 <- ggplot(df_action_imdb, aes(x=Platform, y=IMDb)) + 
  geom_boxplot()
p2 <- p2 + ggtitle("IMDB of Action Movies")
p2
```

    ## Warning: Removed 586 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

``` r
# Sci-Fi movies
scifi_movies <- data.frame()
for (i in 1:16744){
  movie_to_test <- table[i,]
  genre <- as.character(movie_to_test$Genres)
  genre <- unlist(strsplit(genre, split = ","))
  if (any("Sci-Fi" == genre)){
    scifi_movies <- rbind(scifi_movies, movie_to_test)
  }
}


scifi_netflix <- table[scifi_movies$Netflix == 1,]
scifi_hulu <- table[scifi_movies$Hulu == 1,]
scifi_prime <- table[scifi_movies$Prime.Video == 1,]
scifi_disney <- table[scifi_movies$Disney. == 1,]

df_scifi_imdb <- data.frame("Platform" = c(), "IMDb" = c())
df_scifi_netflix <- data.frame("Platform" = "Netflix", "IMDb" = scifi_netflix$IMDb)
df_scifi_hulu <- data.frame("Platform" = "Hulu", "IMDb" = scifi_hulu$IMDb)
df_scifi_prime <- data.frame("Platform" = "Prime", "IMDb" = scifi_prime$IMDb)
df_scifi_disney <- data.frame("Platform" = "Disney+", "IMDb" = scifi_disney$IMDb)
df_scifi_imdb <- rbind(df_scifi_netflix, df_scifi_hulu, df_scifi_prime, df_scifi_disney)

p3 <- ggplot(df_scifi_imdb, aes(x=Platform, y=IMDb)) + 
  geom_boxplot()
p3 <- p3 + ggtitle("IMDB of Sci-Fi Movies")
p3
```

    ## Warning: Removed 608 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

``` r
# Comedy movies
comedy_movies <- data.frame()
for (i in 1:16744){
  movie_to_test <- table[i,]
  genre <- as.character(movie_to_test$Genres)
  genre <- unlist(strsplit(genre, split = ","))
  if (any("Comedy" == genre)){
    comedy_movies <- rbind(scifi_movies, movie_to_test)
  }
}


comedy_netflix <- table[comedy_movies$Netflix == 1,]
comedy_hulu <- table[comedy_movies$Hulu == 1,]
comedy_prime <- table[comedy_movies$Prime.Video == 1,]
comedy_disney <- table[comedy_movies$Disney. == 1,]

df_comedy_imdb <- data.frame("Platform" = c(), "IMDb" = c())
df_comedy_netflix <- data.frame("Platform" = "Netflix", "IMDb" = comedy_netflix$IMDb)
df_comedy_hulu <- data.frame("Platform" = "Hulu", "IMDb" = comedy_hulu$IMDb)
df_comedy_prime <- data.frame("Platform" = "Prime", "IMDb" = comedy_prime$IMDb)
df_comedy_disney <- data.frame("Platform" = "Disney+", "IMDb" = comedy_disney$IMDb)
df_comedy_imdb <- rbind(df_comedy_netflix, df_comedy_hulu, df_comedy_prime, df_comedy_disney)

p4 <- ggplot(df_comedy_imdb, aes(x=Platform, y=IMDb)) + 
  geom_boxplot()
p4 <- p4 + ggtitle("IMDB of Comedy Movies")
p4
```

    ## Warning: Removed 603 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

``` r
library(gridExtra)
grid.arrange(p1, p2, p3, p4, nrow = 2, ncol = 2)
```

    ## Warning: Removed 576 rows containing non-finite values (stat_boxplot).

    ## Warning: Removed 586 rows containing non-finite values (stat_boxplot).

    ## Warning: Removed 608 rows containing non-finite values (stat_boxplot).

    ## Warning: Removed 603 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->

rotten now

``` r
rotten <- data.frame("Platform" = c(), "Rotten" = c())
df_netflix_rotten <- data.frame("Platform" = "Netflix", "Rotten" = netflix$Rotten.Tomatoes)
df_hulu_rotten <- data.frame("Platform" = "Hulu", "Rotten" = hulu$Rotten.Tomatoes)
df_prime_rotten <- data.frame("Platform" = "Prime", "Rotten" = prime$Rotten.Tomatoes)
df_disney_rotten <- data.frame("Platform" = "Disney+", "Rotten" = disney$Rotten.Tomatoes)
rotten <- rbind(df_netflix_rotten, df_hulu_rotten, df_prime_rotten, df_disney_rotten)

r1 <- ggplot(rotten, aes(x=Platform, y=Rotten)) + 
  geom_boxplot()
r1 <- r1 + ggtitle("Rotten Tomatoes of movies on four platforms")
r1
```

    ## Warning: Removed 11895 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

``` r
# action movies

df_action_rotten <- data.frame("Platform" = c(), "Rotten" = c())

df_action_netflix_rotten <- data.frame("Platform" = "Netflix", "Rotten" = action_netflix$Rotten.Tomatoes)
df_action_hulu_rotten <- data.frame("Platform" = "Hulu", "Rotten" = action_hulu$Rotten.Tomatoes)
df_action_prime_rotten <- data.frame("Platform" = "Prime", "Rotten" = action_prime$Rotten.Tomatoes)
df_action_disney_rotten <- data.frame("Platform" = "Disney+", "Rotten" = action_disney$Rotten.Tomatoes)

df_action_rotten <- rbind(df_action_netflix_rotten,
                          df_action_hulu_rotten,
                          df_action_prime_rotten,
                          df_action_disney_rotten)

r2 <- ggplot(df_action_rotten, aes(x=Platform, y=Rotten)) + 
  geom_boxplot()
r2 <- r2 + ggtitle("Rotten Tomatoes of Action Movies")
r2
```

    ## Warning: Removed 12150 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->

``` r
# sci-fi movies

df_scifi_rotten <- data.frame("Platform" = c(), "Rotten" = c())

df_scifi_netflix_rotten <- data.frame("Platform" = "Netflix", "Rotten" = scifi_netflix$Rotten.Tomatoes)
df_scifi_hulu_rotten <- data.frame("Platform" = "Hulu", "Rotten" = scifi_hulu$Rotten.Tomatoes)
df_scifi_prime_rotten <- data.frame("Platform" = "Prime", "Rotten" = scifi_prime$Rotten.Tomatoes)
df_scifi_disney_rotten <- data.frame("Platform" = "Disney+", "Rotten" = scifi_disney$Rotten.Tomatoes)

df_scifi_rotten <- rbind(df_scifi_netflix_rotten,
                          df_scifi_hulu_rotten,
                          df_scifi_prime_rotten,
                          df_scifi_disney_rotten)

r3 <- ggplot(df_scifi_rotten, aes(x=Platform, y=Rotten)) + 
  geom_boxplot()
r3 <- r3 + ggtitle("Rotten Tomatoes of Sci-Fi Movies")
r3
```

    ## Warning: Removed 12011 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-22-1.png)<!-- -->

``` r
# comedy movies

df_comedy_rotten <- data.frame("Platform" = c(), "Rotten" = c())

df_comedy_netflix_rotten <- data.frame("Platform" = "Netflix", "Rotten" = comedy_netflix$Rotten.Tomatoes)
df_comedy_hulu_rotten <- data.frame("Platform" = "Hulu", "Rotten" = comedy_hulu$Rotten.Tomatoes)
df_comedy_prime_rotten <- data.frame("Platform" = "Prime", "Rotten" = comedy_prime$Rotten.Tomatoes)
df_comedy_disney_rotten <- data.frame("Platform" = "Disney+", "Rotten" = comedy_disney$Rotten.Tomatoes)

df_comedy_rotten <- rbind(df_comedy_netflix_rotten,
                          df_comedy_hulu_rotten,
                          df_comedy_prime_rotten,
                          df_comedy_disney_rotten)

r4 <- ggplot(df_comedy_rotten, aes(x=Platform, y=Rotten)) + 
  geom_boxplot()
r4 <- r4 + ggtitle("Rotten Tomatoes of Comedy Movies")
r4
```

    ## Warning: Removed 12014 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->

``` r
grid.arrange(r1, r2, r3, r4, nrow = 2, ncol = 2)
```

    ## Warning: Removed 11895 rows containing non-finite values (stat_boxplot).

    ## Warning: Removed 12150 rows containing non-finite values (stat_boxplot).

    ## Warning: Removed 12011 rows containing non-finite values (stat_boxplot).

    ## Warning: Removed 12014 rows containing non-finite values (stat_boxplot).

![](imdb_and_rotten_files/figure-gfm/unnamed-chunk-24-1.png)<!-- -->
