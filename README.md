.

### SPIDER WEB DEVELOPMENT TASK-3
# FRONT-END
# CREATED a weather application that shows the weather of the location clicked by the user on a Google Map

# STEP BY STEP APPROACH TO CREATE THE APPLICATION

# STEP-1:INCLUSION OF GOOGLE MAP
1.The map can be obtained from GOOGLE MAPS API.
2.The link for the website is "https://developers.google.com/maps/".
3.Click on "web".
4.Then click on "get API".
5.Typed the project name and then click on "ENABLE API" and got my API KEY.
6.In your HTML file include this:<script async defer src="https://maps.googleapis.com/maps/api/js?key=API KEY&callback=initMap"><script>
Instead of API KEY I gave my API KEY=6ae549aa7de464d892343ab1a948fa14.
7.Then I created a function "initMap" and wrote the following code
	options={zoom:4,center:{lat:20.5937,lng: 78.9629}};
	map=new google.maps.Map(document.getElementById("map"),options);
  This creates a map object of google maps.
  The map is now available on the browser page at the location mentioned by div element having id as "map" and the map is having zoom     level of 4 and centered at India(The given lat and lng are latitude and longitude of India).
  # spider_webdev_task3
use github issues to host images

# STEP-2:INCLUSION OF INFOWINDOWS
  1.There are 4 infowindows which are visible when the index.html is run.
  2.I created an array of objects by the name of "cities" and stored the name of 4 cities and corresponding latitudes and longitudes.
  3.Then I created 4 different objects of google.maps.InfoWindow().If we create one object then we will see one infowindow which is of the last city because the content of the object will be overwritten.
  4.The different objects can be created by taking a variable s and assigning it the value "info"+i.toString() where i is the looping variable.It can be seen in the "info_window" function.
  5.Each infowidow object has content and position.
    I gave content as city name and temperature.The way I got the temperature is explained later in the README.
    Position implies the position of the info window which can be specified by the latitude and longitude.
    I did this in a loop and obtained city,lat,lng from cities array and temperature from temperauure array.
  6." &#8451" is for degree C symbol.

# STEP-3:INCLUSION OF SEARCH BOX WITH AUTOCOMPLETION
  1.I included google library "places" in the script
  <script async defer src="https://maps.googleapis.com/maps/api/js?key=API KEY&callback=initMap"><script>
  2.I stored the location typed by the user in the search box (having id as "search") in a variable "search".
  3.Then I created an object of google.maps.places.Autocomplete(search) by  the name autocomplete.
