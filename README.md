# Finding A Random Location in the U.S. Based on Census Data

Downloads census data from [https://api.census.gov/](https://api.census.gov/) and geography data from 
[https://www2.census.gov/geo/tiger/](https://www2.census.gov/geo/tiger/). Uses that data to draw a random lattitude and longitude within the U.S. weighted by population. Locations can be plotted on Google Maps API or using matplotlib.

Project documented at:<br>
[Choosing a Random Census Block in the United States using Python and Census Data](https://medium.com/@datasciencefilmmaker/i-know-where-you-live-71119a00914c)<br>
[Choosing a Random Location Within A Geographical Polygon Using Python and Census Data](https://medium.com/@datasciencefilmmaker/i-know-where-you-live-choosing-a-random-location-within-a-geographical-area-b65dfa73c323)<br>
[Plotting Locations Using Google Maps API and Javascript](https://medium.com/@datasciencefilmmaker/i-know-where-you-live-3-6b6b32c05fa3)

## get_census_data.py

Downloads the relevant data from census.gov and puts it into a form that can be read in efficiently and used by python.

# get_census_data()

Uses requests to download state-level data first. Then uses the county codes in the state-level files to download county-level data. Finally, uses the block codes in the county-level data to download the population of each census block. 

# test_census_data()

Tests the census data that we downloaded for internal consistency, then draws random blocks from the data weighted by population and compares them to the actual populations of those blocks. If working properly, this should just be a straight line though the origin (with scatter)


# download_shape_files():
Downloads all of the shapefiles from census 2020.

# make_shape_lookup():
Uses the blocks.csv file and the shape files for each state and creates a lookup table so that we can look up the shapefiles quickly by row number if we know the FIPS number.

## choose_random_people.py

# get_random_location() -> Point:
Randomly chooses a latitude and longitude within a given ploygon'''

# load_lookup()
Loads the lookup table created by make_shape_lookup.py. Also sets the random seed (if provided).

# get_random_people()
Uses the lookup table to draw a random group of lattitudes and longitudes
in the U.S., weighted by population. Requires call to load_lookup() first.

# create_cameras_json()
Main function to create the final file that I need, which is a list of 
n_samples randomly-drawn locations in the U.S., weighted by population,
with a random radius for each to represent a circular area around that point.
Output in json format.

# plot_philly_cameras()
Plots randomly drawn circles in the Philadelphia metro area.

# plot_US_cameras()
Plots randomly drawn circles in the continental U.S.

Various other functions test aspects of the code.

## html and javascript

Code for plotting a bunch of randomly drawn points on a map using the Google Maps API.