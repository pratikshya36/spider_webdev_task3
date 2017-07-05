

### SPIDER WEB DEVELOPMENT TASK-3
# FRONT-END
# CREATED a weather application that shows the weather of the location clicked by the user on a Google Map

# STEP BY STEP APPROACH TO CREATE THE APPLICATION

# STEP-1:INCLUSION OF GOOGLE MAP
1.The map can be obtained from GOOGLE MAPS API.
2.The link for the website is "https://developers.google.com/maps/".
3.Click on "web".
![googlemapapi](https://user-images.githubusercontent.com/28576445/27851665-6a9d5b42-6179-11e7-87e8-5d55b2add3ba.PNG)
4.Then click on "GET A KEY".
![api_key](https://user-images.githubusercontent.com/28576445/27851725-ba311f86-6179-11e7-8637-e5b3b773660d.PNG)
5.Typed the project name and then click on "ENABLE API" and got my API KEY.
![name](https://user-images.githubusercontent.com/28576445/27851810-145998ee-617a-11e7-9906-d72485998979.PNG)
6.In your HTML file include this:<script async defer src="https://maps.googleapis.com/maps/api/js?key=API KEY&callback=initMap"><script>
Instead of API KEY I gave my API KEY=6ae549aa7de464d892343ab1a948fa14.
7.Then I created a function "initMap" and wrote the following code
	options={zoom:4,center:{lat:20.5937,lng: 78.9629}};
	map=new google.maps.Map(document.getElementById("map"),options);

![initmap](https://user-images.githubusercontent.com/28576445/27851815-19bb2b86-617a-11e7-91f5-3289d719a38c.PNG)
  This creates a map object of google maps.
  The map is now available on the browser page at the location mentioned by div element having id as "map" and the map is having zoom     level of 4 and centered at India(The given lat and lng are latitude and longitude of India).
  # spider_webdev_task3

use github issues to host images

# STEP-2:INCLUSION OF INFOWINDOWS
  1.There are 4 infowindows which are visible when the index.html is run.
  2.I created an array of objects by the name of "cities" and stored the name of 4 cities and corresponding latitudes and longitudes.
  3.Then I created 4 different objects of google.maps.InfoWindow().If we create one object then we will see one infowindow which is of the last city because the content of the object will be overwritten.
  4.The different objects can be created by taking a variable s and assigning it the value "info"+i.toString() where i is the looping variable.It can be seen in the "info_window" function.
  ![info_window](https://user-images.githubusercontent.com/28576445/27851918-8de17e70-617a-11e7-9fb9-092a6d2ba253.PNG)


  5.Each infowidow object has content and position.
    I gave content as city name and temperature.The way I got the temperature is explained later in the README.
    Position implies the position of the info window which can be specified by the latitude and longitude.
    I did this in a loop and obtained city,lat,lng from cities array and temperature from temperauure array.
  6." &#8451" is for degree C symbol.

# STEP-3:INCLUSION OF SEARCH BOX WITH AUTOCOMPLETION
  1.I included google library "places" in the script<script async defer src="https://maps.googleapis.com/maps/api/js?key=API KEY&callback=initMap"><script>
  ![auto_complete](https://user-images.githubusercontent.com/28576445/27851929-96aa69f4-617a-11e7-996d-46116701a0ef.PNG)
  2.I stored the location typed by the user in the search box (having id as "search") in a variable "search".
  3.Then I created an object of google.maps.places.Autocomplete(search) by  the name autocomplete.
  4.Then I added an addListener event to the autocomplete object when autocomplete is completedand location is selected.
  5.Then I create an object to get the place selected by using variable "place" using autocomplete.getPlace()
  and obtained the complete address and latitude and longitude of this place by using the properties of this object 
  "place" using various syntaxes.
  
  
  # STEP-4:FINDING TEMPERATURE OF A GIVEN LOCATION
  1.Temperature can be obtained using OPEN WEATHER MAP API.
  2.I went to the link https://openweathermap.org/api and then clicked on API key and signed up and obtained the key.
  3.Then I used AJAX in the following ways.
  1.Web browsers have built in tool called "XMLHttpRequest".It establishes connection with the URL that we specify and helps us to send or receive data.I created a new instance of this tool by the name xmlhttp.
    xmlhttp=new XMLHttpRequest();
    ![xmlhttp](https://user-images.githubusercontent.com/28576445/27851938-9f4ada44-617a-11e7-98a5-70c520002f45.PNG)
  2.I used a method of this tool"open" to get data from the url  url="http://api.openweathermap.org/data/2.5/weather?lat="+lat+"&lon="+lng+"&APPID="+api"
   where lat and lng are latitude and longitude of the place and api is my API KEY
    "6ae549aa7de464d892343ab1a948fa14".It will tell the object to go this URL and get teh JSON object.I sent this request using "send" method
    When this request receives response I declared an anonymous function and when this request receives a package bag (xmlhttp.readyState==4) and when it is succesful (xmlhttp.readyState==200).
   I parsed the data to JSON data and obtained the location and temperature.
   
   # STEP-5:DISPLAYING THE TEMPERATURE
   1.I used 2 textboxes.
   2."update()" receives the data for temperature and location and sends those values to the 2 boxes.
   
   # STEP-6:CREATING THE MARKERS
   ![mark](https://user-images.githubusercontent.com/28576445/27852786-2098e610-617e-11e7-88e5-ec55d9280769.PNG)
   1.I added an addListener event such that when the user clicks on the map, a marker is set there.Latitude and longitude are obtained from LatLng object
   
  
 
  
  
   
