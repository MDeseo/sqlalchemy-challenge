## Assignment 10 - SQL Alchemy

In this assignment, Python and SQLAlchemy were used to do a basic climate analysis of Honolulu, Hawaii and data exploration of the provided climate database (hawaii.sqlite). Specifically, SQLAlchemy ORM queries, Pandas, and Matplotlib were used.

The assignment was created in conda version 4.13.0 in "PythonData" environment using Jupyter Noteboook (climate_starter_solved.ipynb).
The python file 'app_solved.py' was created in Visual Studio Code version 1.72.1 but MUST run in GitBash terminal.

## Part 1: Analysis and Climate Data Exploration

The analysis and data exploration were carried out using the "climate_starter_solved.ipynb" using the following functions:

   - SQLAlchemy <create_engine()> to connect to the SQLite database 'hawaii.sqlite'.
   - SQLAlchemy <automap_base()> to reflect the tables into classes, and then save references to the classes named "station" and "measurement."

Python was linked to the database by creating a SQLAlchemy session and the following analyses were performed:

1. Precipitation analysis

  - Find the most recent date in the dataset.
  - Using that date, get the previous 12 months of precipitation data by querying the previous 12 months of data.
  - Select only the "date" and "prcp" values. (Note: Precipitation is measured in millimetres.)
  - Load the query results into a Pandas DataFrame, and set the index to the "date" column.
  - Sort the DataFrame values by "date".
  - Plot the results by using the DataFrame <plot> method.
  - Print the summary statistics for the precipitation data using Pandas.

2. Station analysis

  - Design a query to calculate the total number of stations in the dataset.
  - Design a query to find the most-active stations using the function <func.count>. That is, the stations that have the most rows that corresponds to the station id that has the greatest number of observations.
  - Design a query that calculates the lowest, highest, and average temperatures that filters on the most-active station id found in the previous query. (Note: Temperature is measured in Celsius.)
  - Design a query to get the previous 12 months of temperature observation (TOBS) data by filtering by the station that has the greatest number of observations and query the previous 12 months of TOBS data for that station.
  - Plot the results as a histogram with "bins=12".

The session was closed after the query.


## Part 2: Design of Climate App

A Flask API was designed based on the queries developed above. The following routes were created:

1. </>
   - Start at the homepage and list all the available routes.

2. </api/v1.0/precipitation>
   - Convert the query results from precipitation analysis (i.e. retrieve only the last 12 months of data) to a dictionary using date as the key and prcp as the value.
   - Return the JSON representation of your dictionary.

3. </api/v1.0/stations>
   - Return a JSON list of stations from the dataset.

4. </api/v1.0/tobs>
   - Query the dates and temperature observations of the most-active station for the previous year of data.
   - Return a JSON list of temperature observations for the previous year.

5. </api/v1.0/<start>> and </api/v1.0/<start>/<end>>
   - Return a JSON list of the minimum temperature, the average temperature, and the maximum temperature for a specified start or start-end range.
   - For a specified start, calculate <TMIN>, <TAVG>, and <TMAX> for all the dates greater than or equal to the start date.
   - For a specified start date and end date, calculate <TMIN>, <TAVG>, and <TMAX> for the dates from the start date to the end date, inclusive.



