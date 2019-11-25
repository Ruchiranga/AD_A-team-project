# What makes a movie successful?

# Abstract
Nowadays, movies have become an integral part of entertainment in everyone’s life. Entertainment giants like Netflix and HBO are investing billions of dollars a year to produce high quality movies with the most popular actors and directors of the cinematographic industry for its audience. 

The goal of the project is to analyze the factors that contribute to the success of a movie through time. We intend to look into aspects including but not limited to the cast, the movie budget, writers and directors, time of first screening, genre and the IMDB rating of movies. The analysis can give us insights on the evolution of the interest of people towards movies with time. We will use datasets provided by IMDB and we will also use web scraping to obtain additional information required from imdb.com.

# Research questions
We intend to address the main research question "What are the factors that make a movie award winning?" Is it the actors? Is it the director? Is it the genre? or is it something else?. During the analysis we plan to investigate or compute the following

* A score will be calculated for every actor depending on the awards they have won, awards they have been nominated to and the significance of the awarding ceramony. Following award ceramonies are considered to be the most prestigious ones in the descending order of significant.
** Oscar 				
** Palme d'Or
** BAFTA Film Award
** Golden Berlin Bear
** Filmfare Award
** European Film Award
** Golden Leopard
** Grand Jury Prize
** Golden Globe
** Golden Lion 			
From Oscars to Golden Lion awards, each will be assigned a weight from 1 to 0.5 with Oscards having weight as 1 and Golden Lion having weight as 0.5. For all the award ceramonies not included in the above list, we will give a weight of 0.1. For a win a weight of 1 will be used and for a nomination a weight of 0.5 will be used. Final score for an actor will be the weighted sum of each of his/her nominations or awards (The weights could be subjected to change). We will then aggregate the scores of the stars in each movie and see if the movies with a higher aggregate value have won more awards.
* How does the geographical reach of a movie impact its success?
* Does the month of release have an impact on a movie's succees?
* Are high budget movies always successful?
* What is the impact of gender on the success of a movie
* Has there been any time in the history that movies in a certain genre became more successful than movies in other genres?



# Dataset
We intend to use datasets provided by IMDB: [https://datasets.imdbws.com/](https://datasets.imdbws.com/).

We will also scrape pages from [https://www.imdb.com/](https://www.imdb.com/) that refer to specific movies and actors to obtain information in addition to those available in the datasets.


# A list of internal milestones up until project milestone 2
### Data preparation (to be completed by 4th November)
* Inspect the datasets and determine the missing information that needs to be web scraped and the unnecessary information that needs to be ignored.
* Write code to scrape the required data from web and store them locally
* Prepare the final data sets by merging the scraped information with the existing datasets
### Data inspection and cleaning (to be completed by 8th November)
* Perform exploratory data analysis on the data to obtain a generic idea on the data as well as to identify any possible data issues
* Clean the data and prepare the dataset for analysis
### Data analysis and conclusions (to be completed by 25th November)
* Perform data analysis focussing on the mentioned research questions
* Draw relevant conclusions based on the analysis findings
* Clean up notebook and ensure all observations and conclusions have clear descriptions with proper visualizations


# Questions for TAa
Nothing for the moment
