# Python Geocoder - Modules, Packages, and APIs: Part 2

## Learning Objectives: 
- Sending HTTP requests with the `requests` library
- Reading documentation for modules and APIs.

For part two of this activity, you will be continuing the work done in the previous portion and writing code in the `main.py` file.

## Part 1 Overview:

You already have the solution to this section from the previous homework. As a reminder, you put several destinations into a list of strings called `destinations`. Then, you imported the the [geocoder module](https://geocoder.readthedocs.io/providers/ArcGIS.html#geocoding) and used it to translate each landmark into latitude-longitude coordinates. You looped through the list and printed each location's latitude and longitude, then used `arcgis` to translate the places to coordinates.

Your code should currently have this functionality:

```
Space Needle is located at (47.6205, -122.3493)
Crater Lake is located at (42.8684, -122.1685)
Golden Gate Bridge is located at (37.8199, -122.4783)
Yosemite National Park is located at (37.8651, -119.5383)
Las Vegas, Nevada is located at (36.1699, -115.1398)
Grand Canyon National Park is located at (36.1070, -112.1130)
Aspen, Colorado is located at (39.1911, -106.8175)
Mount Rushmore is located at (43.8791, -103.4591)
Yellowstone National Park is located at (44.4280, -110.5885)
Sandpoint, Idaho is located at (48.2766, -116.5535)
Banff National Park is located at (51.4968, -115.9281)
Capilano Suspension Bridge is located at (49.3429, -123.1149)
```

## Part 2: Heather Weather

Cody is satisfied by geolocating his landmarks, but Heather wants to take it one step further and get the current weather at each location. Help Heather with some code that calls an API to get current weather based on the latitude-longitude coordinates you already have. Take Cody's code from Problem 1 and add an API call to [OpenWeather](https://home.openweathermap.org/users/sign_up).

> Note: You will need to register an email address to get an API key, but it is free to use.

#### Directions for OpenWeather API

When you first log in to the OpenWeather API site, you will need to access your API keys through the link in the Navbar.

Now find the API Docs. (Currently the API link in the very top navbar will bring you to their many APIs. You want the "API doc" link for "Current Weather Data".) Hunt down the endpoint URL for getting a result from latitude and longitude. We'll need that later.

- We'll be using the [requests module](http://docs.python-requests.org/en/master/api/#module-requests) to call the OpenWeather API at the "Current Weather" endpoint using our API key. 

> (Although this API key is very low security risk, it's still a good idea to add our secret keys to an `.env` file, and to also add `.env` to the `.gitignore` if it's not there already.)

> Look into the `python-dotenv` [pip package](https://pypi.org/project/python-dotenv/) if you're interested in learning more!

#### Starter Code

**Note:** This new code gets put into your previous code from Problem 1!

```python
# Import the module (top of the file).
import requests

# A variable to hold the base url for our API call from the OpenWeather docs.
API_BASE_URL = "http://api.openweathermap.org/data/2.5/weather"

# Previous code still here.

for point in destinations:
    # Previous `geocoder` code still here.

    # A full_api_url variable that holds our base url and the latitude and longitudes and api key. Check the docs again for the format (and don't forget the ?).
    result = requests.request('GET', full_api_url).json()

    # From the result, print out the summary and current temperature.
```

#### Expected Output

```
The Space Needle is located at (47.6199, -122.3487)
At The Space Needle right now, it's Partly Cloudy with a temperature of 65.63
Crater Lake is located at (42.9116, -122.1483)
At Crater Lake right now, it's Clear with a temperature of 63.52
The Golden Gate Bridge is located at (37.8183, -122.4784)
At The Golden Gate Bridge right now, it's Partly Cloudy with a temperature of 59.98
Yosemite National Park is located at (37.7490, -119.5885)
At Yosemite National Park right now, it's Clear with a temperature of 83.1
Las Vegas, Nevada is located at (36.1719, -115.1400)
At Las Vegas, Nevada right now, it's Clear with a temperature of 104.72
Grand Canyon National Park is located at (36.0573, -112.1096)
At Grand Canyon National Park right now, it's Clear with a temperature of 88.37
Aspen, Colorado is located at (39.1900, -106.8182)
At Aspen, Colorado right now, it's Clear with a temperature of 86.87
Mount Rushmore is located at (43.8803, -103.4588)
At Mount Rushmore right now, it's Partly Cloudy with a temperature of 77.62
Yellowstone National Park is located at (44.9775, -110.6983)
At Yellowstone National Park right now, it's Clear with a temperature of 72.09
Sandpoint, Idaho is located at (48.2730, -116.5478)
At Sandpoint, Idaho right now, it's Clear with a temperature of 68.81
Banff National Park is located at (51.1356, -115.4073)
At Banff National Park right now, it's Partly Cloudy with a temperature of 63.91
Capilano Suspension Bridge is located at (49.3432, -123.1133)
At Capilano Suspension Bridge right now, it's Mostly Cloudy with a temperature of 65.11
```

**Hint:** In the dictionary that holds the API results, you'll get an awful lot of data. Check the dictionary carefully, remember that dictionaries in Python use brackets and strings to access keys! 

**Hint:** Also note that the unit of measurement that the API default to is in Kelvin! Scour the API documentation for how you might change the data to Fahrenheit!

---

## Super Bonus: String Formatting for Matt

Matt likes Heather's idea of getting the weather for each location they plan on visiting, but he thinks the data is unreadable. Modify your code to:

1. Add a newline after each location (`\n`).
2. Add an F.
3. Add a unicode degree character.
4. Display only one decimal place on the temperature (think about string formatting).

### Sample Code:Decimal Places Display

There are other ways to format the string. This is one way!

```python
# prints 1.23456789
print("{0}".format(1.23456789))

# prints 1.23 (2 decimal places)
print("{0:.2f}".format(1.23456789))

# prints 1.2345 (4 decimal places)
print("{0:.4f}".format(1.23456789))
```

#### Expected Output

```
The Space Needle is located at (47.6199, -122.3487)
At The Space Needle right now, it's Partly Cloudy with a temperature of 65.6° F

Crater Lake is located at (42.9116, -122.1483)
At Crater Lake right now, it's Clear with a temperature of 63.5° F

The Golden Gate Bridge is located at (37.8183, -122.4784)
At The Golden Gate Bridge right now, it's Partly Cloudy with a temperature of 60.0° F

Yosemite National Park is located at (37.7490, -119.5885)
At Yosemite National Park right now, it's Clear with a temperature of 83.1° F

Las Vegas, Nevada is located at (36.1719, -115.1400)
At Las Vegas, Nevada right now, it's Clear with a temperature of 104.7° F

Grand Canyon National Park is located at (36.0573, -112.1096)
At Grand Canyon National Park right now, it's Clear with a temperature of 88.3° F

Aspen, Colorado is located at (39.1900, -106.8182)
At Aspen, Colorado right now, it's Clear with a temperature of 86.9° F

Mount Rushmore is located at (43.8803, -103.4588)
At Mount Rushmore right now, it's Partly Cloudy with a temperature of 77.6° F

Yellowstone National Park is located at (44.9775, -110.6983)
At Yellowstone National Park right now, it's Clear with a temperature of 72.0° F

Sandpoint, Idaho is located at (48.2730, -116.5478)
At Sandpoint, Idaho right now, it's Clear with a temperature of 68.8° F

Banff National Park is located at (51.1356, -115.4073)
At Banff National Park right now, it's Partly Cloudy with a temperature of 63.9° F

At Banff National Park right now, it's Partly Cloudy with a temperature of 63.9° F
Capilano Suspension Bridge is located at (49.3432, -123.113)
At Capilano Suspension Bridge right now, it's Mostly Cloudy with a temperature of 65.1° F
```

> **Hint**: Here's a list of [unicode characters](https://en.wikipedia.org/wiki/List_of_Unicode_characters). Refer to your class notes for how to use an escape character. Done and done!

![](https://media.giphy.com/media/PqwqtOLfG19Ti/giphy.gif)
