# Bus Schedule Optimization
A project done for the course **CSE3024 - Web Mining** under **Dr.A.Bhuvaneswari** 

<h3>Team members</h3>
<ul>
<li><b>AKASH R 20BCE1501</b> Github: <a href="https://github.com/akash-r34">akash-r34</a></li>
<li><b>ABRAR AHAMED 20BCE1437</b> Github: <a href="https://github.com/Abrar-Ahamed">Abrar-Ahamed</a></li>
<li><b>AKSHAY GIRISH 20BCE1573</b> Github: <a href="https://github.com/Akshaykviit023">Akshaykviit023</a></li>
</ul>

<h3>Prerequisites</h3>
You can install the necessary dependencies by running the requirements.txt file.
<ul>
<li>Python 3x</li>
<li>Numpy</li>
<li>Pandas</li>
<li>Matplotlib</li>
<li>Seaborn</li>
<li>Requests</li>
</ul>

<h2>Abstract</h2>
The need for efficient and optimized bus schedules is a common problem in public transportation systems. Efficient bus schedules not only benefit passengers by reducing wait times and increasing reliability, but they also benefit bus operators by reducing costs and improving efficiency. The Bus Schedule Optimization project is a software engineering project aimed at optimizing bus schedules using a genetic algorithm. The genetic algorithm takes into account the bus routes, stops, and schedules to find the optimal schedule that minimizes waiting time for passengers and maximizes efficiency for the bus operator. The project is designed to be flexible and customizable, allowing users to input their own data and parameters to generate a customized optimal schedule. Overall, this project has the potential to improve public transportation systems by reducing wait times and increasing efficiency.

<h2>Dataset</h2>
This project uses a dataset constructed from data retrieved from a public API called <a href="https://rapidapi.com/transloc/api/openapi-1-2"><b><i>OpenAPI 1.2 by TransLoc</i></b></a>.
<h3>Overview</h3>
The <b>OpenAPI 1.2</b> API provided by TransLoc is a public API that allows developers to access transit data for various cities in the United States. The API provides real-time data on the location and status of buses, shuttles, and other transit vehicles, as well as schedules, routes, and stop information. The API also allows developers to retrieve historical transit data for analysis and planning purposes. The API uses RESTful principles and returns data in JSON format. Developers can use the API to build transit-related applications, such as real-time transit tracking apps, trip planning tools, and transit analytics platforms. The API is available through RapidAPI, which provides a unified interface for accessing multiple APIs. 

<h3>Can getting data from API considered as Web Mining?</h3>
<p>Getting data from an API can be considered a type of web mining, specifically, it can be classified as web data mining or web content mining.</p>
<p>Web data mining refers to the process of extracting data from various sources on the World Wide Web, including web pages, web documents, and web databases. In this case, the API serves as a web-based data source that can be accessed through standard web protocols such as HTTP.</p>

<p>Web content mining, on the other hand, refers to the process of extracting useful information from the content of web pages, such as text, images, and videos. While an API may not necessarily provide access to raw web page content, it can still be used to extract structured data, such as transit schedules or real-time vehicle locations.</p>

<p>Therefore, while getting data from an API is not a traditional form of web mining, it can still be classified as a type of web data mining or web content mining, depending on the nature of the data being retrieved</p>

<h3>Data retrieval and preprocessing</h3>
<p>It is possible to sample and save the data of various buses and bus routes in a database. For the sake of this project, we will concentrate on a single data sample for a single bus that travels a single bus route. The data snippet was collected in March for roughly 5 hours (6 PM to 10:40 PM) throughout the evening on the Weekend RIT(Rochester Institute of Technology) Hotel bus (due to the Coronavirus pandemic that time the data collection was limited). The bus route has 6 distinct stops, and the entire trip takes 35 minutes. The bus service runs from 7:00 AM until 1:40 AM. You may get the complete bus timetable here.</p>

<p>An approximate rate of 2.2 samples per minute are taken from the data, which is then saved in a CSV file (Dataset/data.csv). The data is first averaged for every minute (1 minute bins). By doing this, it is made sure that every minute of the entire sampling period (about 5 hours) has a single passenger occupancy value assigned to it. Moreover, the data is averaged for 5-minute bins. The data is also averaged for bins of 35 minutes because the round journey time is 35 minutes. The timetable will be optimised using 35 minute bins as a foundation.</p>

<br>
<div align="center">
  <img src="https://user-images.githubusercontent.com/113085803/229866329-b5247539-0ab6-4025-aa15-86dfabda056f.png"/><br>
  <b><i>Figure 1<br>Passenger occupancy in 35 min time bins</i></b>
  <br>
  <br>

  <img src="https://user-images.githubusercontent.com/113085803/229866465-120ffb6d-b946-4f35-9666-7bea7bf79fb8.png"/><br>
  <b><i>Figure 2<br>Passenger occupancy in 5 min time bins</i></b>
  <br>
  <br>
  
  <img src="https://user-images.githubusercontent.com/113085803/229866553-c55ea359-9767-45eb-93d2-64eb2380ec2d.png"/><br>
  <b><i>Figure 3<br>Passenger occupancy in 1 min time bins</i></b>
  <br>
  <br>

</div>

<h2>Bus Schedule Optimization</h2>
<h3>Finding passenger ocuupancy data and thresholding</h3>
<p>To determine whether a bus should operate based on passenger occupancy data, you would need to establish a minimum threshold for passenger occupancy that is required for a bus to be considered financially viable to operate. This threshold will likely vary depending on the specific circumstances of the bus route, such as the cost of fuel and labor, the price of tickets, and any subsidies or government funding that may be available. Once you have established this threshold, you would then need to analyze the passenger occupancy data for each bus route to determine whether the number of passengers on a given trip meets or exceeds the minimum threshold. If the occupancy level is below the threshold, you would need to consider whether there are any factors that may be contributing to the low ridership, such as poor scheduling or routing, lack of marketing or outreach, or competition from other modes of transportation.</p>

<p>If you determine that a bus route is not meeting the minimum occupancy threshold and there are no obvious solutions to increase ridership, it may be necessary to consider reducing the frequency of service or eliminating the route altogether. However, it's important to carefully weigh the potential impacts on passengers and the broader transportation network before making such decisions.</p>

<h3>Optimization</h3>
<p>As passenger occupancy is exceptionally low during non-peak hours, particularly in the evening once most courses are done, a circumstance may emerge when no bus is scheduled for a lengthy period of time, for example, if we utilise a single threshold value of 10%. We may further improve the bus timetable while guaranteeing a convenient service for customers by setting distinct criteria for normal working/class hours (9AM to 7PM) and non-working hours (7PM forward). In the second row of the above picture, we can notice a rise in the amount of yellow blocks indicating that the bus will run for that specific time slot if a threshold of 5% is applied to all time slots starting at roughly 7 PM.</p>

<br>
<div align="center">
  <img src="https://user-images.githubusercontent.com/113085803/229868020-f09028a5-81e8-4fa9-ad48-361b04f8d9a3.png"/><br>
  <b><i>Figure 4<br>Various thresholds and Optimized schedule</i></b>
</div>

<br>
<p>The final row of the following diagram demonstrates how dynamic thresholding, which uses 10% during working hours and 5% outside of them, might be used to improve bus schedules. The red boxes indicate that a bus will not run during that specific timeslot, whereas the green blocks show the time periods for which a bus will run. The schedule was tailored for this 5-hour data sample such that the bus only runs for 4/8 time slots, or 50% of the overall operating window. Even at this pace, the bus won't reach its maximum capacity, preventing congestion.
</p>


<h2>Results</h2>
<p>As seen in the above graphic, the dynamic thresholding optimisation approach will cause the bus to run for half as long as it usually does. The distance travelled by the Weekend RIT Hotel bus is around 10 miles round way. As a result, the bus's total distance travelled throughout the 5-hour period will drop by 40 miles.</p>

<h2>Conclusion</h2>
<p>An optimized bus schedule could be useful for transportation planners or other professionals. It can help them make data-driven decisions to improve the efficiency and sustainability of bus services, and ultimately improve the mobility and quality of life for passengers. By optimizing bus schedules, transit agencies can improve the efficiency of their operations, reduce fuel consumption, and reduce operating costs. Passengers benefit from more frequent and reliable service, shorter wait times, and reduced travel times. The fact that this project has been tested on a real-world network is a promising sign, although it would be important to verify its effectiveness in other contexts as well. </p>

<p>This project also has the potential to help the environment in several ways. By optimizing bus schedules to reduce fuel consumption and operating costs, transit agencies can also reduce their carbon footprint and other harmful environmental impacts. According to the US Department of Energy, the average fuel economy for a transit bus is 3.26 miles per gallon of gasoline, which can be drastically reduced by implementing a optimized bus schedule. Additionally, by providing more frequent and reliable service, public transit becomes a more attractive option for commuters, which can lead to reduced vehicle use and fewer greenhouse gas emissions from cars and trucks.
</p>

<h2>References</h2>
<ol>
<li><a href="https://www.researchgate.net/publication/317745436_Environmental_Impacts_of_Promoting_New_Public_Transport_Systems_in_Urban_Mobility_A_Case_Study">
Environmental Impacts of Promoting New Public Transport Systems in Urban Mobility: A Case Study</a></li>
<li><a href="https://afdc.energy.gov/data/10310">Average Fuel Economy by Major Vehicle Category</a></li>
</ol>


