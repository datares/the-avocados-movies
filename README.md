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
## Data Sources
- #1: [Kaggle: Movies on Netflix, Prime Video, Hulu and Disney+](https://www.kaggle.com/ruchi798/movies-on-netflix-prime-video-hulu-and-disney)
- #2: [Kaggle: Movie Industry](https://www.kaggle.com/danielgrijalvas/movies)
- #3: [Kaggle: IMDb movies extensive dataset](https://www.kaggle.com/stefanoleone992/imdb-extensive-dataset)
- #4: [Kaggle: MovieLens 20M Dataset](https://www.kaggle.com/grouplens/movielens-20m-dataset?select=movie.csv)
- #5: [Kaggle: Netflix Movies and TV Shows](https://www.kaggle.com/shivamb/netflix-shows)
- #6: [IMDB DataSet] (https://www.imdb.com/interfaces/)

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

### Category #3: Amount of Content

### Category #4: Exclusive Content

## Overall Results & Conclusion



