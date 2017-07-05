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
