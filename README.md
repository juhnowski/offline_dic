# 21-05-2017
Append Sanskrit-English Dictionaries

# 20-05-2017
Add index.html
# Initial version

## How to install
At first time and only once you need to open html with incapsulated javascript for creating dictionary.<br>
Now there is only one dictionary:
* wil.html - Wilson Sanskrit-English Dictionary

Please be patient. Filling of the database is low-priority asynchronous process for the browser.
Approximately it takes several minutes.
To be convinced that the database was successfully created click F12 and then go to the Application tab: Web SQL -> mydb -> DICT

## How to create dictionary
Dictionary html files with incapsulated javascript are converted by java app Xml2JS  from https://github.com/juhnowski/Xml2JS

## How to use
### Open <a href="fetching.html">fetching.html</a> print word in input box and press Enter.<br></h2>
Settings works only for online version.<br>
It was tested in Google Chrom 58.0.3029.110 (64-bit).<br>
If you want to use it in mobile browser there are two way:
* put files in public folder of webserver (for instance Apache, IIS, Nginx, Python Simple HTTP server ...), download, and open from local folder
* transfer it to mobile file system some way (by USB, or by e-mail) and then open it in chrome mobile browser</li>

### It's expected that it will be worked in browsers:
* Chromium
* Firefox

## TODO
* Create browser plugin for Google Chrome
* Investigate Safari and IE capabilities
* Convert all dictionaries from http://www.sanskrit-lexicon.uni-koeln.de/ - Cologne Digital Sanskrit Dictionaries




# 19-05-2017
Fork juhnowski/sanskrit-simple-search
File test_web_sql.html - template for working with WebSQL Database in Chrome.

# 18-05-2017
* Add sorting of output.
* Problems:
  * sometimes server block the request and incoming responses has 403 Forbidden Error. I think that this is a ddos protection of cologne http://www.sanskrit-lexicon.uni-koeln.de host server.
  * if you try test it on localhost please remember, that for correct work chrome plugin can be switched on, but for correct work others internet resources (youtube for instance) it can be switched off.    
* TODO:
  * manual test, or it will be batter write auto tests.
  * bug fixing


# 17-05-2017
* The settings.html page has been added. All properties now are stored in localStorage. It means that we may change it in one place and it will affect in all anothers one.
* Bugfix word.frequency null value. If the word is absence on the frequency table, then word value is set to null. But in this case we may order by length.
* TODO:
  * word list ordering by desc word.frequency. Now it's display in parentheses before word name.

# 14-05-2017
* Store word frequency usage to localStorage. It was implemented by word_frequency.js which is converted from text data file by java program. Once it prepared it may be used till time when frequency data will be changed. Java converter is in https://github.com/juhnowski/FreqWordList url.
* add server.js - this is node.js simple http server for testing. LocalStorage is working only with domains.When I opened fetching.html as file, localStorage was inaccessible.

* run local http server:
  * install node.js https://nodejs.org/en/
  * install http-server https://www.npmjs.com/package/http-server via npm:   npm install http-server -g
  * run server: node server.js
  * test url in CHROME: http://localhost:8080/fetching.html and don't forget switch on CORS plugin

* TODO:
  * word list ordering by desc word.frequency. Now it's display in parentheses before word name.
  * changes  test.filter = "roman";  test.noLit = "off";  test.transLit="slp1"; which are now hardcoded.

# 13-05-2017
Add fetching.html - yet another iteration of search UI component

Please pay attention:
1)It will work correct from http://www.sanskrit-lexicon.uni-koeln.de site.
2)For correct work in local browser it's needed to install Google chrome plugin:
https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi/related?hl=en-US

Previously we talk about getting data from server in JSON format, but I stay on parsing incoming html, becouse:
1) to keep the backward compatibility
2) not to spend time and forces on changes in a backend and then support two version of server responses: html and json
