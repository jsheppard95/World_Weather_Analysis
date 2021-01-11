# World_Weather_Analysis
Jupyter Notebook files to retrieve and collect weather data and create maps for vacation plans based on user specified weather paramaters
using OpenWeatherMap and Google Maps APIs.

## Weather_Database
[Weather_Database.ipynb](Weather_Database/Weather_Database.ipynb) generates the database of cities and weather information used for the
vacation search and route planning of this module. The notebook generates 2000 random coordinates from which the nearest city to each
is found using [`citipy`](https://github.com/wingchen/citipy). We then use the [`OpenWeatherMap`](https://openweathermap.org/current)
current weather data API call to obtain the current weather for each city, resulting in the database of cities and weather conditions
found in [WeatherPy_Database.csv](Weather_Database/WeatherPy_Database.csv).

## Vacation_Search
[Vacation_Search.ipynb](Vacation_Search/Vacation_Search.ipynb) reads the previously generated
[WeatherPy_Database.csv](Weather_Database/WeatherPy_Database.csv) file into a Pandas DataFrame which is then filtered to cities whose maximum
temperatures satisy a user-specified range. It then uses the Google Places API
[`Place Search`](https://developers.google.com/places/web-service/search#PlaceSearchRequests)
to return the first hotel found within 5000 m of each city. Finally, we write this filtered dataset with hotels to the output file 
[WeatherPy_vacation.csv](Vacation_Search/WeatherPy_vacation.csv) and use [`gmaps`](https://jupyter-gmaps.readthedocs.io/en/latest/tutorial.html)
to generate an interactive map with markers showing current weather information for each returned hotel. An example of this interactive map is shown in
[WeatherPy_vacation_map.png](Vacation_Search/WeatherPy_vacation_map.png) which includes hotels nearest to cities whose maximum temperature is between
40 and 85 &deg;F.

## Vacation_Itinerary
[Vacation_Itinerary.ipynb](Vacation_Itinerary/Vacation_Itinerary.ipynb) reads the previously generated
[WeatherPy_vacation.csv](Vacation_Search/WeatherPy_vacation.csv) file and creates a travel itinerary map for four user-specified cities in this dataset.
It uses the [gmaps directions layer](https://jupyter-gmaps.readthedocs.io/en/latest/tutorial.html#directions-layer) to draw a driving route between four
cities. An example route between the Turkish cities of Talas, Silop, Fethiye, and Bayir is shown in
[WeatherPy_travel_map.png](Vacation_Itinerary/WeatherPy_travel_map.png) along with an interactive map with weather information in
[WeatherPy_travel_map_markers.png](Vacation_Itinerary/WeatherPy_travel_map_markers.png)
