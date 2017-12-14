## Visualizing Cycling Accidents in Berlin

> Biking is an integral part of a big city life and is generally quite safe. Commuting can be another story though. To do something about it, I have scraped data on cycling accidents in Berlin and visualized it to find the most dangerous spots in the city.


Anyone who's been to Berlin knows that while the city has much to offer, good cycling paths are not one of those things. Berliners cycle inspite of that: and while to some- a hobby, to many it is the preferred method of transportation. The popularity of bike sharing in Berlin is on the rise too.


But cycling is not all roses, as anyone who cycled in a big city can tell you, and can be dangerous. The most import thing a cyclist can do is to follow the rules and learn how to cycle safely. Knowing where the potentially dangerous areas are can help too.

In that light, I wanted to find a map about Berlin's dangerous areas for cycling. I wasn't able to find one, but I did manage to get yearly cycling accident reports by the Berlin Police. So while the city waits for the thirteen new bike "superhighways" to be constructed, I decided to use data to make my cycling easier and safer today.

First off, I created a python script to download all police reports. Python's `BeautifulSoup` and `requests` were more than enough.

Anyone who did table parsing from pdf files can tell that it's not much fun, to put it mildly. I've used [**Tabula**](http://tabula.technology/) to get the bulk of the data extracted to csv files. After that, it was good old Python scripting to clean the data into a more presentable form (all the code can be found on my github profile).

The data contained an address and a number of times an accident has been registered at that address. Having an address as an `str ` is not enough to map it. Here, I've used a library called `geopy` to get the latitude and longitude data points for each address. There are quite a few geocoding/reverse geocoding services available. Bing Maps Service not only offers a free API but also does street junction geocoding, which I needed for this data.

After this I decided to plot the data using `Bokeh`. The map below represents all registered Berlin bike accidents per given year. To change the year, just use the slider.  The bigger the bubble marker, the higher the number of accidents registered for that place. 

Take note, however, that for many accidents only the street name was available, and not the complete address. Because of this, we can only tell the most dangerous streets, but not the actual zones in any given street or road where cyclists should take notice. Some of the addresses were intersections; those are ploted more or less accurately.



{% include mainplot-berlin-bikes-01.html %}


This is the first part in this series. You can find the complete analysis with the data and all code [here](https://github.com/epistemicjanitor/) and [here](https://github.com/epistemicjanitor/).
