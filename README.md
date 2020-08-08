# web-scraping-challenge: Mission to Mars

## Background
In this assignment, the ask was to build a web application that scrapes various websites for data related to the Mission to Mars and display the information in a single HTML page. The following outlines the steps taken:

**Step 1: Scraping**

**Step 2 - MongoDB and Flask Application**

## Step 1: Scraping

Initial scraping of the following websites was completed using Jupyter Notebook, BeautifulSoup, Pandas, and Requests/Splinter:

* [NASA Mars News Site](https://mars.nasa.gov/news/): the latest news titles and paragraph texts were scraped and saved into variables.

* [JPL Featured Space Image](https://www.jpl.nasa.gov/spaceimages/?search=&category=Mars): the image url for the current Featured Mars Image was found and assigned to a variable called `featured_image_url`.

* [Mars Weather Twitter account](https://twitter.com/marswxreport?lang=en): the latest Mars weather tweet was scraped from this page and the text saved as a variable called `mars_weather`.

* [Mars Facts](https://space-facts.com/mars/): the table containing facts about the planet including Diameter, Mass, etc. was scraped and Pandas was used to convert the data to a HTML table string.

* [USGS Astrogeology](https://astrogeology.usgs.gov/search/results?q=hemisphere+enhanced&k1=target&v1=Mars): this website was used to obtain high resolution images for each of Mar's hemispheres by finding the image url to the full resolution image. These urls were saved along with the title with the hemisphere name in a dictionary.

## Step 2 - MongoDB and Flask Application

MongoDB with Flask templating was used to create a new HTML page that displays all of the information that was scraped from the URLs above. The following tasks were completed:

* The Jupyter notebook was converted into a Python script called `scrape_mars.py` with a function called `scrape` that executes all of the scraping code from above and returns one Python dictionary containing all of the scraped data.

* A route called `/scrape` was created, that will import the `scrape_mars.py` script and call the `scrape` function.

* The return value is stored in Mongo as a Python dictionary.

* A root route `/` was created, that queries the Mongo database and passes the Mars data into an HTML template for display.

* A template HTML file called `index.html` was created, that will take the Mars data dictionary and display all of the data in the appropriate HTML elements.
