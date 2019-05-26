# animated-winter
## Webscrapping BoardGameGeek - top 10 000 boardgames. Done on BeautifulSoup and Selenium.

### BoardGameGeek: https://boardgamegeek.com

----------------------------------------

## Main Information

Purpose of this project was our WebScraping Classes. The aim was to scrape information about 10 000 board games from BoardGameGeek - one of the biggest wikipedia like, platform for board games. 

We wanted to gather information about basic features of every scraped board game, i.e : title, rating, ranking, number of players voted,players, fans, number of owners etc. 

We organized this data in a form of a data frame.

In the end we made some basic explanatory data analysis to check how the features look like on the graphs.

During this scraping process, we had to use both, standard webscraping tools, which uses html and xpath locators, and also selenium webdriver, to overcome difficulties with handling dynamically generated part of the website in JavaScript.

---------------------------------------

## Implementation Process and Results

The steps are explained below:

1.  First, we did simple scraping of the main page, i.e: title, average rating, geek rating, ranking, number of voters and a link to subpage of each boardgame
  * Scrapping the top list was fast because we were able to work using requests.get(). Scrapping the individual board games has proven more difficult. The website uses javascript to dynamically load the important part of the page, so using the simple requests.get() wasn't a success.

2. We've used this links to iterate through, to gather more information about each board game, and append to the new data frame, yet it supposed to be difficult challenge due to the fact that each subpage was generated dynamically using JavaScript
  * To overcome this challenge, we needed to use a emulated browser to execute the JS code. We chose Selenium, because we had some experience with it during the previous semester. Since this process is much slower, we decided to scrap only 100 individual pages. We also didn't want to burden the server, but since BGG is a very popular website, the additional 1 000 visits probably wouldn’t make a difference anyway.

3. We exported the results to separate files, and proceeded to basic EDA
  * During analysis we've found out that most of the games are of 3 out of 4 difficulty level, and that most of the variables are highly correlated, due to the possession bias (we are more likely to rate and review the boardgame we own, than one we just played once)
  
4. In the end we came up with 2 interesting results:
  * Does the Ranking of the game depend on it's popularity?
      **  For the top 100 thankfully no. BoardGameGeek does a good job of representing the good, but more niche titles.
      **  For the top 10 000, there seem to be a much stronger relationship. It seems that BGG put a stronger emphasis on the         number of votes.

  * Does the complexity of the game influence it's rating?
      **  Turns out that yes, it does. Users seem to prefer more complex games (3 and 4). They particularly dislike the very simple 'party' games (complexity = 1).
      
