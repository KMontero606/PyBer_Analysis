# PyBer_Analysis
# Overview of the analysis:

V. Isualize has assigned a brand-new assignment to create a summary DataFrame of the ride-sharing data by city type, create a multiple-line graph that shows the total weekly fares for each city type and submit a written report that summarizes how the data differs by city type and how those differences can be used by decision-makers at PyBer.
  
#	Results:
1. Description of the differences in ride-sharing data among the different city types. 
```
```
2. Ride-sharing data of the following:
  - total rides:
  ```
  1. Get the total rides for each city type
  total_rides_df = pyber_data_df.groupby(["type"]).count()["ride_id"]
  total_rides_df.head()
  type
  Rural        125
  Suburban     625
  Urban       1625
  Name: ride_id, dtype: int64
  ```
   - total drivers 
  ```
  2. Get the total drivers for each city type
total_drivers_df = pyber_data_df.groupby(["type"]).sum()["driver_count"]
total_drivers_df.head()
type
Rural         537
Suburban     8570
Urban       59602
Name: driver_count, dtype: int64
  ```
   - total fares 
  ```
  3. Get the total amount of fares for each city type
total_fares_df = pyber_data_df.groupby(["type"]).sum()["fare"]
total_fares_df.head()
type
Rural        4327.93
Suburban    19356.33
Urban       39854.38
Name: fare, dtype: float64
  ``` 
   - average fare per ride and driver 
  ```
  4. Get the average fare per ride for each city type. 
average_fare_ride = total_fares_df / total_rides_df
average_fare_ride.head()
type
Rural       34.623440
Suburban    30.970128
Urban       24.525772
dtype: float64

  5. Get the average fare per driver for each city type. 
average_fare_driver = total_fares_df / total_drivers_df
average_fare_driver.head()
type
Rural       8.059460
Suburban    2.258615
Urban       0.668675
dtype: float64
  ```
   - total fare by city type
  ```
  8. Format the columns.
pyber_summary_df["Total Rides"] = pyber_summary_df["Total Rides"].map("{:,}".format)
pyber_summary_df["Total Drivers"] = pyber_summary_df["Total Drivers"].map("{:,}".format)
pyber_summary_df["Total Fares"] = pyber_summary_df["Total Fares"].map("${:,.2f}".format)
pyber_summary_df["Average Fare per Ride"] = pyber_summary_df["Average Fare per Ride"].map("${:,.2f}".format)
pyber_summary_df["Average Fare per Driver"] = pyber_summary_df["Average Fare per Driver"].map("${:,.2f}".format)
pyber_summary_df


  ```
  
# Summary:
There is a statement summarizing three business recommendations to the CEO for addressing any disparities among the city types. (4 pt)
