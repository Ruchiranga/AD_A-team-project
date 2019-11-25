# What makes a movie successful?

# Abstract
Nowadays, movies have become an integral part of entertainment in everyone’s life. Entertainment giants like Netflix and HBO are investing billions of dollars a year to produce high quality movies with the most popular actors and directors of the cinematographic industry for its audience. 

The goal of the project is to analyze the factors that contribute to the success of a movie through time. We intend to look into aspects including but not limited to the cast, the movie budget, writers and directors, time of first screening, genre and the IMDB rating of movies. The analysis can give us insights on the evolution of the interest of people towards movies with time. We will use datasets provided by IMDB and we will also use web scraping to obtain additional information required from imdb.com.

# Research questions
We intend to address the main research question "What are the factors that make a movie award winning?" Is it the actors? Is it the director? Is it the genre? or is it something else? During the analysis we plan to investigate the following

## Actors

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

 
From Oscars to Golden Lion awards, each will be assigned a weight from 1 to 0.5 with Oscards having weight as 1 and Golden Lion having weight as 0.5. For all the award ceramonies not included in the above list, we will give a weight of 0.1. For a win a weight of 1 will be used and for a nomination a weight of 0.5 will be used. Final score for an actor will be the weighted sum of each of his/her nominations or awards (The weights could be subjected to change). We will then aggregate the scores of the stars in each movie and see if the movies with a higher aggregate value have won more awards.

## Geographical reach

With the help of the title.akas.tsv.gz dataset we can know an approximation of the geographical reach of a given movie by just computing the length of the list of alternative titles of that movie. 

## Month of release

We got the release dates of the movies from the scraping and we extracted the month from it. We can use it as a categorical variable.

## High budget

This feature is going to be complicated to use, most of the film do not have a budget and when they do, it is not necessarily in US dollars. In order to convert different currencies to actual US dollars, we have to keep up with the inflation and with the old exchange rates which is really hard for movies released before the year 2000 as we were not able find any information about those on the internet.

## Gender 

Each person in the name.basics.tsv.gz dataset has a list of primaryProfession, some of them might be actor or actress, this allows us to know the gender of each actor or actress. For each movie we have an array of actors and we know the gender of each of them which will allow us to compute an approximate ratio of gender representation in the movie cast which can be used as a feature.

In addition we also have access to the features of the title.basics.tsv.gz : 
* isAdult 
* runtimeMinutes
* Genres

## Additional question we
* Has there been any time in the history that movies in a certain genre became more successful than movies in other genres?



# Dataset
We use the datasets provided by IMDB: [https://datasets.imdbws.com/](https://datasets.imdbws.com/).

We will also scrape pages from [https://www.imdb.com/](https://www.imdb.com/) that refer to specific movies and actors to obtain information in addition to those available in the datasets.

#### Description of the data

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
* primaryTitle: English title, string
* originalTitle: Original title, string
* startYear: Year of release, integer
* runtimeMinutes: Runtime of the movie in minutes, string, scraped
* genres: genres the movie can be attributed to, string
* averageRating: Average rating of the movie given by imbd users, float
* numVotes: Number of users that have scored the movie, float