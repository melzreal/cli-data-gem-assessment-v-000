Scraper building plan:

1. created the gem, auto generated file structure
2. created a basic cli and ensured file was executable

defining a story:
stories have
:title
:content

Scraper class. We'll be scraping "Wired awake" for the top news of the week
Scraper class:
 Scraper class uses nokogiri, scrapes link:
	https://www.wired.co.uk/topic/wired-awake

Story Class:
Calls on the scraper attributes (:title, :content)
	Each link has the date format as ddmmyy. So for the 12 of September 2018 - Wednesday - the link is https://www.wired.co.uk/article/wired-awake-120918
	wired-awake-110918
	wired-awake-100918 etc
  #today = Date.today.wday

  we can convert today to a weekname then collect story headlines that match that weekname
  ex weekday = today.toweekname (#returns "Tuesday") doco.collect{|a| a.includes?(weekday) : selected_stories = a }
   for us to give all 3 results that contain tuesday is it enough to collect or do we need to shove them into an array? Is it ok to create the stories, collect the headlines, then create a hash of stories with those titles?? Or is it over complicating??
  should that aggregation be done in an array or a hash if needed??
  to this point I have two arrays, one has all the headlines, the other all the links leading to those stories.
  I can map headlines to links so that when that particular day is selected the user is redirect to those stories

  ### LAST STEPS

  everytime we call scrape_url(given_day) we need to check if that day's content was not scraped already. Where to store this info to run the check against??
