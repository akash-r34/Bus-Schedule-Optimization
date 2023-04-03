# Bus Schedule Optimization
A project done for the course **CSE3024 - Web Mining** under **Dr.A.Bhuvaneswari** 

<h3>Team members</h3>
<ul>
<li><b>AKASH R 20BCE1501</b> Github: <a href="https://github.com/akash-r34">akash-r34</a></li>
<li><b>ABRAR AHAMED 20BCE1437</b> Github: <a href="https://github.com/Abrar-Ahamed">Abrar-Ahamed</a></li>
<li><b>AKSHAY GIRISH 20BCE1573</b> Github: <a href="https://github.com/Akshaykviit023">Akshaykviit023</a></li>
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

<h2>References</h2>
<ol>
<li><a href="https://www.researchgate.net/publication/317745436_Environmental_Impacts_of_Promoting_New_Public_Transport_Systems_in_Urban_Mobility_A_Case_Study">
Environmental Impacts of Promoting New Public Transport Systems in Urban Mobility: A Case Study</a></li>
<li><a href="https://afdc.energy.gov/data/10310">Average Fuel Economy by Major Vehicle Category</a></li>
</ol>
