pytrends
=========

### About

**Pseudo API for Google Trends**

* Allows simple interface for automating downloads of csv reports from Google Trends.
* Main feature is to help trick google into thinking the script is actually a browser.


* Only good until Google changes their backend again :-P

**Installation**

```pip install pytrends```

**Requirements**
* Written for both Python 2.7+ and Python 3.3+
* Requires a google account to use.
* Requires fake-useragent python library (installed automatically with pip)

## Connect to Google
**pyGTrends(google_username, google_password)**

**Parameters**
* google_username
  - a valid gmail address
* google_password
  - password for the gmail account

### Request a Report
**request_report(keywords, hl='en-US', cat=None, geo=None, date=None, use_topic=False)**

**Parameters**
* Keywords
  - the words to get data for
  - Example ```"Pizza"```
  - Up to five terms with a comma and space: ```"Pizza, Italian, Spaghetti, Breadsticks, Sausage"```
* Advanced Keywords
  - When using Google Trends dashboard Google may provide suggested narrowed search terms. 
  - For example "iron" will have a drop down of ```"Iron Chemical Element, Iron Cross, Iron Man, etc"```. 
  - To automate future downloads run it once manually to find the encoded topic. Find the encoded topic by inspecting the url. The topic starts after ```q=``` and ends before the next ```&```. 
  - For example: ```https://www.google.com/trends/explore#q=%2Fm%2F025rw19&cmpt=q```
  - ```"%2Fm%2F025rw19"``` is the topic "Iron Chemical Element" to use this with pytrends set use_topics=True
* hl
  - Language to narrow results
  - Two letter language abbreviation
  - For example English is ```"en"```
  - Defaults to english
* cat
  - Category to narrow results
  - Find available cateogies by inspecting the url when manually using Google Trends. The category starts after ```cat=``` and ends before the next ```&```
  - For example: ```"https://www.google.com/trends/explore#q=pizza&cat=0-71"```
  - ```"0-71"``` is the category
  - Defaults to no category
* geo
  - Two letter country abbreviation
  - For example United States is ```"US"```
  - Defaults to World
* date
  - Date to start from
  - Defaults to all available data, 2004 - present.
  - ```"MM/YYYY #m"``` where # is the number of months from that date to pull data for
  - For example: ``"10/2009 61m"`` would get data from October 2009 to October 2014
* use_topic
  - Used for Advanced Keywords
  - Set to ```True``` to avoid URLencoding the keywords

### Save a Report to file
**save_csv(path, trend_name)**

**Parameters**
* path
  - Output path
* trend_name
  - Human readable name for file

### Credits

* Connecting to google code heavily based off Sal Uryasev's pyGTrends

* With some ideas pulled from Matt Reid's Google Trends API
  - https://bitbucket.org/mattreid9956/google-trend-api/overview
