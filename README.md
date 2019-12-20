Link for the website : https://ruchiranga.github.io/

Contribution of the members of the group (roughly) :

Analysis of the features

Laurent : Geographical reach, budget
Ruchiranga : Gender, IsAdult
Souhail : Director score, releaseDate
Stanislas : Age, Runtime, Genres

The scraping code was done by Ruchiranga

# What makes a movie successful?

## Abstract
Nowadays, movies have become an integral part of entertainment in everyone’s life. Entertainment giants like Netflix and HBO are investing billions of dollars a year to produce high quality movies with the most popular actors and directors of the cinematographic industry for its audience. 

The goal of the project is to analyze the factors that contribute to the success of a movie through time. We intend to look into aspects including but not limited to the cast, the movie budget, writers and directors, time of first screening, genre and the IMDB rating of movies. The analysis can give us insights on the evolution of the interest of people towards movies with time. We will use datasets provided by IMDB and we will also use web scraping to obtain additional information required from imdb.com.

## Research Questions
We intend to address the main research question "What are the factors that make a movie award winning?". We analyzed or plan to analyze the following aspects.

## Success metrics

### Recognition score

Obtained by an aggregation of the number of oscars win, the number of awards win, and the number of nomination for an award.

### Number of IMDB Voters

The title.ratings.tsv.gz dataset contains the field numVotes that gives the number of votes made on each movie. This number can be an indicator of the popularity of a movie. This is only indicator of the popularity of a movie and is useful to analyze the impact a movies popluarity has on the number of awards it wins.

### Revenue

The revenue in US dollars

### Metacritic Score

The metacritic score obtained from scraing the IMDB web page of movies can be used to see if a high metacritic score corelates with award winning movies.

## Features

### Actors

A score will be calculated for every actor depending on the awards they have won, awards they have been nominated to and the significance of the awarding ceramony. Following award ceramonies are considered to be the most prestigious ones in the descending order of significance.
* Oscar 				
* Palme d'Or
* BAFTA Film Award
* Golden Berlin Bear
* Filmfare Award
* European Film Award
* Golden Leopard
* Grand Jury Prize
* Golden Globe
* Golden Lion 

### Geographical Reach

With the help of the title.akas.tsv.gz dataset we can know an approximation of the geographical reach of a given movie by just computing the length of the list of alternative titles of that movie. 

### Month of Release

We got the release dates of the movies from the scraping and we extracted the month from it. We can use it as a categorical variable.

### Budget

This feature is going to be complicated to use, most of the film do not have a budget and when they do, it is not necessarily in US dollars. In order to convert different currencies to actual US dollars, we have to keep up with the inflation and with the old exchange rates which is really hard for movies released before the year 2000 as we were not able find any information about those on the internet.

### Gender 

Each person in the name.basics.tsv.gz dataset has a list of primaryProfession, some of them might be actor or actress, this allows us to know the gender of each actor or actress. For each movie we have an array of actors and we know the gender of each of them which will allow us to compute an approximate ratio of gender representation in the movie cast which can be used as a feature.

### isAdult

isAdult contains 18+ movies, we can if it influences the various metrics

### runtimeMinutes

The length of the movie can be a factor for its success.

### Genres

Each movie has a list of genres, there is 25 of them and they can be very useful.

### Age of Cast

For each actor or actress in the name.basics.tsv.gz dataset, we can find their birthYear. This can be used to compute the median for every movie considering the age of the cast by the time the movie was released. We can see if actors being young or old can impact whether a movie would win an award or not.

### Release Date

The year and the month of the release date 


## Dataset
We use the datasets provided by IMDB: [https://datasets.imdbws.com/](https://datasets.imdbws.com/). Schemas and descriptions of the features of the datasets used are as follows.

### Persons

name.basics.tsv  
 |_nconst : IMDB Id of the person  
 |_primaryName : Last name and first name  
 |_birthYear : For computing the age of actors/actresses  
 |_primaryProfession : list of professions  

### Movies

title.basics.tsv.gz  
 |_tconst : IMDB Id of the movie  
 |_titleType : Used To filter only movies  
 |_primaryTitle : English title  
 |_originalTitle : Original title  
 |_isAdult : Useful to analyse whether a movie being adult can make a movie successful  
 |_startYear : gives time of first screening  
 |_runtimeMinutes : totla runtime of the movie  
 |_genres : genres the movie belongs to  

### Alternative Movie Names

title.akas.tsv.gz  
 |_tconst : Id of the movie (not unique since a film can have more than one region)  
 |_ordering : A number to uniquely identify rows for a given titleId  
 |_region : Abbreviation of the name of the region the alternative name belongs to  
 |_language : Abbreviation of the name of the language  

### User Ratings

title.ratings.tsv.gz  
 |_tconst : Id of the movie  
 |_averageRating : Weighted average of all the individual user ratings  
 |_numVotes : Number of votes the title has received (Can be used as an indicator of movie popularity)  


We also scrape pages from [https://www.imdb.com/](https://www.imdb.com/) that refer to specific movies and actors to obtain information in addition to those available in the datasets. Schemas and descriptions of the data that is scraped are as follows.

### Movies

* tconst: Unique imdb identifier of each movie, given as string
* stars: Three main actors playing in the movie , given as list of strings, scraped 
* oscarWins: Number of Oscars awarded to the movie, given as float, scraped 
* nominations: Number of general award nominations, given as float, scraped
* wins: Number of awards won, given as integer, scraped
* releaseDate: Date release of the movie, given as DateTime, scraped
* releaseCountry: Country of release, given as string, scraped
* plotKeywords: Keywords describing the plot of the movie, given as list of strings, scraped
* budget: production budget of the movie, given as string, scraped
* worldwideGross: Wordlwide revenue, given as string, scrapped
* metascore: Scores are assigned to movie's reviews of large group of the world's most respected critics, and weighted average are applied to summarize their opinions range, given as float, scraped
* musicProducer: Producer of the music in the movie, string, scraped

### Actor Awards and Nominations

* nconst: Unique IMDB IDs of actors
* year: Year of award or nominaion
* category : Award ceramony
* w_n : Winner or Nominee
* description: Description of the award
* movie: Name of the movie in which the actor played on
* tconst: Unique IMDB Id of movie in which the actor played on