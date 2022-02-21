# Python Geocoder - Modules, Packages, and APIs

## Learning Objectives: 
- Importing and using python modules.
- Iterating through lists and drilling into dictionaries.
- Reading documentation for modules and APIs.

## Introduction:

This lab will be a two-part code challenge with a bonus. Part 2 will build on the code from Part 1. You can put all of your code in one file called `main.py`.

_Reminder: you can run the file from your command line with the following:_

```bash
python3 main.py
```

> **Hint:** Make sure your `main.py` program is printing something out with a `print` statement. Otherwise, you won't see any output from running it!


## Part 1: Geo Cody

Cody and his friends Heather and Matt are going on a road trip across the Western United States and Canada. They want to visit several landmarks, national parks, and big cities. Here's their agenda:

```
Space Needle
Crater Lake
Golden Gate Bridge
Yosemite National Park
Las Vegas, Nevada
Grand Canyon National Park
Aspen, Colorado
Mount Rushmore
Yellowstone National Park
Sandpoint, Idaho
Banff National Park
Capilano Suspension Bridge
```

Your job is to put these destinations into a list of strings called `destinations`. Then, import the [geocoder module](https://geocoder.readthedocs.io/providers/ArcGIS.html#geocoding) and use it to translate each of the landmarks into latitude-longitude coordinates. You'll need to loop through the list and print each location's latitude and longitude. We will be using the `arcgis` method from our `geocoder` module to translate the places to coordinates. Visit the [docs](https://geocoder.readthedocs.io/results.html) for sample code.

#### Example Usage (`geocoder`/`arcgis`)

This code will give you the latitude and longitude for one destination.

```python
import geocoder

g = geocoder.arcgis('Redlands, CA')

print(g.latlng) # latlng is a tuple with a length of 2.
```

#### Starter Code

This is the general structure you'll follow to get the results for all of the destinations.

```python
import geocoder

# Declare destinations list here.

# Loop through each destination.
for destination in destinations:
#   Get the lat-long coordinates from `geocoder.arcgis`.
#   Print out the place name and the coordinates.
```

#### Expected Output

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

> **Hint:** We're following the pattern in the `geonames` example in the [docs](https://geocoder.readthedocs.io/results.html), only replacing `geonames` with `arcgis`.


## Part 2 

If you're feeling comfortable, tackle [part 2](README-part2.md) next for an API integration!
