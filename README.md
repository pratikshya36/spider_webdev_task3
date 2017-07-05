 # spider_webdev_task3

use github issues to host images

### SPIDER WEB DEVELOPMENT TASK-3
# FRONT-END
# CREATED a weather application that shows the weather of the location clicked by the user on a Google Map
# 1.Both index.html and graph.html are to be downloaded
# 2.The tasks will run on Chrome and Mozilla Firefox
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
t    xmlhttp=new XMLHttpRequest();
    ![xmlhttp](https://user-images.githubusercontent.com/28576445/27851938-9f4ada44-617a-11e7-98a5-70c520002f45.PNG)
  2.I used a method of this tool"open" to get data from the url  url="http://api.openweathermap.org/data/2.5/weather?lat="+lat+"&lon="+lng+"&APPID="+api"
   where lat and lng are latitude and longitude of the place and api is my API KEY

"6ae549aa7de464d892343ab1a948fa14".It will tell the object to go this URL and get the JSON object.I sent this request using "send" method
    When this request receives response I declared an anonymous function and when this request receives a package bag (xmlhttp.readyState==4) and when it is succesful (xmlhttp.readyState==200).
   I parsed the data to JSON object and obtained the location and temperature.
   
   # STEP-5:DISPLAYING THE TEMPERATURE
   1.I used 2 textboxes.
I   2."update()" receives the data for temperature and location and sends those values to the 2 boxes.
   
   # STEP-6:CREATING THE MARKERS
   ![mark](https://user-images.githubusercontent.com/28576445/27852786-2098e610-617e-11e7-88e5-ec55d9280769.PNG)
   1.I added an addListener event such that when the user clicks on the map, a marker is set there.Latitude and longitude are obtained from LatLng object.
   
   # STEP-7:CREATING THE TEMPERATURE GRAPH
   I used 2 concepts here:
   1.LOCAL STORAGE  2.CANVASJS
   
   1.LOCAL STORAGE:It is used to store data in the web browser.
   It can be used by localStorage object.
   ![graph](https://user-images.githubusercontent.com/28576445/27870420-6dbdc9e6-61c0-11e7-9cee-737ddbfeb87e.PNG)
   Data can be stored by localStorage.setItem("give id to the data to be sent",data).
   I created an array of objects which stores the location of the place and temperature of that place and named the array as "datapoints".It stores the locations in "label"which will be on the X-Axis and temperatures in "y" which will be on the Y-Axis of the graph.
   Since local storage stores strings,array is converted to string using JSON.strigify() to convert the JSON objects to strings.
   Data can be obtained back from local storage using  localStorage.getItem('id given to the data sent').
   The string data is converted back to JSON object using JSON.parse() method.
   I am removing the data from local storage using localStorage.removeItem('id of the data sent').
   
   2.CANVASJS:It is an HTML and JAVSCRIPT based CHARTING LIBRARY.We have to include the canvas js library in the script.
   <script src="https://canvasjs.com/assets/script/canvasjs.min.js"></script>
   ![canvasjs](https://user-images.githubusercontent.com/28576445/27870605-e76499be-61c0-11e7-8f43-dfeb3601e1e4.PNG)
   I created a new instance of CanvasJS.Chart and gave the title to the graph and to X-axis as well as to Y-axis and data which specifies the type of the chart as line chart and the points on X and Y-axes.
   Then I called render method using the object which invokes the API to draw the graph.
   
   I used window.location.href which returns the current URL and set it as "graph.html" which displays the graph.
   
   # DESCRIPTION OF FUNCTIONS USED:
   1.initMap() : It is used to set up the google map and is also used for autocompletion purpose.It calls temperature1()and mark().
   2.temperature1(),temperature2(),temperature3(),temperature4():They are used to find the temperature of 1st,2nd,3rd and 4th cities to be displayed in the current viewport.
    I tried in a loop but it didn't work.So had to create 4 functions.
   3.info_window() :It is used to display the infowindows.
   4.updateByGeo():It obtains latitude and longitude of the location clicked by the user and is used to set the URL and send it to sendRequest().
   5.updateByGeo1():It obtains  the address, latitude and longitude of the location searched by the user using autocompletion and is used to set the URL and send it to sendRequest1().
   6.sendRequest():It is used to obtain location and temperature data from the OPEN WEATHER MAP API and send them to update().
   7.sendRequest1():It is used to obtain temperature data from the OPEN WEATHER MAP API and send the address and temperature to 
   update1().
   8.update():It receives weather object from sendRequest().It converts the temperature from kelvin to celcius and displays temperature and location in the two text boxes above the map.
   9.update1():It receives address and temperature of the place searched by the user from sendRequest1().It converts the temperature from kelvin to celcius and displays temperature and address in the two text boxes above the map.
   10.graph():It gets called when the user presses "VIEW THE GRAPH" button.It creates "datapoints" array of objects to store the locations and the corresponding temperatures.And then it stores it in local storage and loads graph.html
   
  
   
   
   
   
   
  
 
  
  
   
