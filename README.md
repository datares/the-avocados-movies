# [INSERT BLOG TITLE] 
By: Team The Avocados 🥑🥑🥑🥑🥑🥑🥑 <br />
## Contributors

### Project	Lead
Zachary Chang, @zachang890

### Team
Kevin Xu, @KevinXu264 <br />
Nora Liu, @yanxiliu230 <br />
Eleanor Pae, @epae0402 <br />
Annie Li, @JL03-Yue <br />

## Project Description & Motivation (Available On MEDIUM)
The video streaming services industry is everywhere, and it’s one that consumers use daily especially in quarantine. What would we do without some light binge-watching of Disney movies, classic sitcoms like “Friends”, and new content every other week? With over 2,000 streaming businesses in the streaming industry, 4 key players, and continuously booming growth due to the variety of content produced, it can be difficult to narrow down which sites are necessary for personal leisure and entertainment. If you’ve ever had difficulty choosing which subscription to give in to, you’re not alone.

Team Avocados had the same dilemma and aimed to find the best streaming service for entertainment consumers. When checking out services like Netflix, Hulu, Disney+, and Amazon Prime, the pros and cons can be confusing and overwhelming. 

Using Kaggle datasets of TV shows and movies offered on these 4 streaming platforms as well as IMDb datasets of movie ratings, we discovered which service outshined the rest for certain metrics. By looking at the amount of content, diversity and variety in the selection offered, popular and highly-rated movies, and exclusive or original streaming content, our team hoped to alleviate some of these concerns to narrow down the best service. 



## Tech Used
- Jupyter Notebooks
- RStudio
- Matplotlib, ggplot, highcharter
- MySQL Workbench

## Data Sources
- #1: [Kaggle: Movies on Netflix, Prime Video, Hulu and Disney+](https://www.kaggle.com/ruchi798/movies-on-netflix-prime-video-hulu-and-disney)
- #2 [Kaggle: TV Shows on Netflix, Primve Video, Hulu and Disney+](https://www.kaggle.com/ruchi798/tv-shows-on-netflix-prime-video-hulu-and-disney)
- #3: [Kaggle: Movie Industry](https://www.kaggle.com/danielgrijalvas/movies)
- #4: [Kaggle: IMDb movies extensive dataset](https://www.kaggle.com/stefanoleone992/imdb-extensive-dataset)
- #5: [Kaggle: MovieLens 20M Dataset](https://www.kaggle.com/grouplens/movielens-20m-dataset?select=movie.csv)
- #6: [Kaggle: Netflix Movies and TV Shows](https://www.kaggle.com/shivamb/netflix-shows)
- #7: [Kaggle: Netflix Top TV Shows](https://www.kaggle.com/ritesh2000/trending-tv-shows-on-netflix)
- #8: [IMDB DataSet](https://www.imdb.com/interfaces/)

## Ranking Categories
### Category #1: Diversity
Datasets used: #1, #2
Objective: Quantify and rank the diversity of films available on each streaming platform, where greater diversity is considered more favorable

The challenge of ranking the streaming services by diversity is that diversity is inherently a rather abstract category. In ecology, scientists have developed a mathematical methodology for quantifying biodiversity by taking into account the *number of species* as well as the *abundance of each species*. Through further research, it was concluded that this is the best mathematical representation of diversity to be found that can be extrapolated to cover *number categories of metrics* and the *abundance of instances of those categories of metrics*. (ex. categories of metrics = [1984, 1926, 1926] abuncance = {1984: 1, 1926: 2}) 

In Python, the mathematical formula is as follows:
```python
def simpson_index(year_count):
    total_count = 0
    for key in year_count:
        total_count += year_count[key]
    denom = total_count * (total_count - 1)
    
    numer = 0
    for key in year_count:
        numer = numer + (year_count[key] * (year_count[key] - 1))
    return 1 - (numer/denom)
```
where __numer__ is ∑n(n-1) where __n__ is the number of instances of a certain metric (ex. in this example, year of production)
and where __denom__ is N(N-1) where __n__ is the number of films considered in this metric.

A similar formula/procedure was applied across the board for six unique metrics including: production year, country, genre, language, age rating, and runtime. The results for this category for diversity are as follows:
| Placing | Production Year | Country | Genre | Language | Age Rating | Runtime (difference too small to count in overall ranking) | Overall |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| *1st Place*  | Disney+  | Netflix | Hulu | Netflix | Hulu | *Netflix* | __Hulu__ 🎉 🟩|
| *2nd Place*  | Prime Video  | Hulu | Prime Video | Hulu | Netflix | *Disney+* | __Netflix__ 🟥|
| *3rd Place*  | Hulu  | Prime Video | Netflix | Prime Video | Disney+ | *Prime Video* | __Prime Video__ 🟧|
| *4th Place*  | Netflix  | Disney+ | Disney+ | Disney+ | Prime Video | *Hulu* | __Disney+__ 🟦|

### Category #2: Ratings
Datasets used: #1

Objective: What is the average and typical IMDb ratings of movies on each streaming service? What percentage do those generally recognized good movies hold among all the movies each service offers?

Customers usually hope that the streaming service they choose actually worth their money. And what we mean by worth it? One important thing we consider is the quality of movies we will get. We definitely do not want to log onto the service and just find that most of the movies don't worth us sitting their for two hours.

### Category #3: Amount of Content

### Category #4: Exclusive Content
Datasets used: #1,6,4,6,7,8
Objective: What differentiates their top 10 list? How popular are the top movies? And what percentage of their views go towards exclusive platform content?

It was inherently difficult to find data that was available on consumer watch data since that is not publicly available information, and thus the next best thing was to solely base exclusive content based on what shows and movies each subscription service offered and ranking them based on the number of IMDb user votes. We felt that that was a more accurate measure of audience popularity and consumption as compared to purely IMDB rating, since that is a performance of how well the movie was according to only a certain number of people, and can be biased to movies/TV shows that have low number of reviewers. 

To generate the data for this comparison, we first split and subset the datasets on Kaggle that distinguished which subscription service offered which TV shows and movies, and then combined that with IMBDb rating and user votes data to generate a combined data frame. 

While IMDb movie scores was widely available on Kaggle, we couldn't find any IMDb ratings for TV shows, so we created our own by extracting the open source IMDb data on their website, filtering for only TV shows, and then combining them using SQL queries due to the massive size of the data. In SQL, the query used was

```SQL
CREATE TABLE (
	SELECT movie_names.titleType, movie_names.primaryTitle, movie_ratings.averageRating, movie_ratings.numVotes, 
	movie_names.startYear, movie_names.runTimeMinutes, movie_names.genres
	FROM movie_names
	INNER JOIN movie_ratings
	ON movie_ratings.tconst = movie_names.tconst
)

```

After collecting all the movies and TV shows that each subscription service offers, we then sorted and collected data for the top 100 Movies and TV shows based on the num of user submitted votes on IMDb and we compared the distribution of release dates, IMDb votes, and IMDb ratings across all four subscription services. We then determined the winners in each category. It was difficult to come up with a clear overall winner, because even though Disney was outleading in the movies categories, it severely underperformed compared to every other service in the TV shows category. Below is just an example of what the data frames looked like that we used to graph. More data is included within our data and graphs section in our repo! 

#### This is an example of the top 15 Disney Movies
|    | Title                                                  | Year | IMDb | imdb_votes | service |
| -- | ------------------------------------------------------ | ---- | ---- | ---------- | ------- |
| 1  | The Avengers                                           | 2012 | 8    | 1225316    | Disney  |
| 2  | Star Wars: Episode IV - A New Hope                     | 1977 | 8.6  | 1188658    | Disney  |
| 3  | Star Wars: Episode V - The Empire Strikes Back         | 1980 | 8.7  | 1109656    | Disney  |
| 4  | Avatar                                                 | 2009 | 7.8  | 1086714    | Disney  |
| 5  | Guardians of the Galaxy                                | 2014 | 8    | 1007917    | Disney  |
| 6  | Pirates of the Caribbean: The Curse of the Black Pearl | 2003 | 8    | 992127     | Disney  |
| 7  | WALL·E                                                 | 2008 | 8.4  | 955757     | Disney  |
| 8  | Star Wars: Episode VI - Return of the Jedi             | 1983 | 8.3  | 912250     | Disney  |
| 9  | Finding Nemo                                           | 2003 | 8.1  | 911647     | Disney  |
| 10 | Iron Man                                               | 2008 | 7.9  | 910300     | Disney  |
| 11 | The Lion King                                          | 1994 | 8.5  | 901362     | Disney  |
| 12 | Up                                                     | 2009 | 8.2  | 895906     | Disney  |
| 13 | Toy Story                                              | 1995 | 8.3  | 846332     | Disney  |
| 14 | Star Wars: Episode VII - The Force Awakens             | 2015 | 7.9  | 833706     | Disney  |
| 15 | Monsters, Inc.                                         | 2001 | 8    | 779728     | Disney  |

#### This is an exameple of the top 15 Netflix TV Shows
|    | Title            | Year | IMDb | imdb_votes | service |
| -- | ---------------- | ---- | ---- | ---------- | ------- |
| 1  | Breaking Bad     | 2008 | 9.5  | 1467953    | Netflix |
| 2  | The Walking Dead | 2010 | 8.2  | 854372     | Netflix |
| 3  | Stranger Things  | 2016 | 8.8  | 824251     | Netflix |
| 4  | Sherlock         | 2010 | 9.1  | 808347     | Netflix |
| 5  | Dexter           | 2006 | 8.6  | 646903     | Netflix |
| 6  | House of Cards   | 2013 | 8.7  | 467258     | Netflix |
| 7  | Black Mirror     | 2011 | 8.8  | 445446     | Netflix |
| 8  | Arrow            | 2012 | 7.6  | 407822     | Netflix |
| 9  | Supernatural     | 2005 | 8.4  | 393006     | Netflix |
| 10 | Narcos           | 2015 | 8.8  | 358250     | Netflix |
| 11 | Peaky Blinders   | 2013 | 8.8  | 350120     | Netflix |
| 12 | Better Call Saul | 2015 | 8.7  | 324611     | Netflix |
| 13 | The Flash        | 2014 | 7.7  | 305509     | Netflix |
| 14 | Family Guy       | 1999 | 8.1  | 304819     | Netflix |
| 15 | The Witcher      | 2019 | 8.3  | 300996     | Netflix |
|    |

## Overall Results & Conclusion



