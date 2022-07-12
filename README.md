# PyBer_Analysis
# Overview of the analysis:

V. Isualize has assigned a brand-new assignment to create a summary DataFrame of the ride-sharing data by city type, create a multiple-line graph that shows the total weekly fares for each city type and submit a written report that summarizes how the data differs by city type and how those differences can be used by decision-makers at PyBer.
  
#	Results:
1. Description of the differences in ride-sharing data among the different city types. 
   - Urban and Suburban areas generated higher profit with total fares ~$1600 to ~$2200 and ~$700 to ~$1300 respectively, than rural area having ~$180 to ~$190 in a five month time period.
   - There is a higher PyBer ride service utilized in urban than suburban and rural areas.
   - One common noteable peak for all three city type occured around late February.
   
   ![PyBer_fare_summary](https://user-images.githubusercontent.com/106962921/178347549-643a03bd-5188-45ad-bc66-44edd60739af.png)

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
  6. Create a PyBer summary DataFrame. 
pyber_summary_df = pd.DataFrame()
pyber_summary_df["Total Rides"] = total_rides_df
pyber_summary_df["Total Drivers"] = total_drivers_df
pyber_summary_df["Total Fares"] = total_fares_df
pyber_summary_df["Average Fare per Ride"] = average_fare_ride
pyber_summary_df["Average Fare per Driver"] = average_fare_driver
pyber_summary_df
  8. Format the columns.
pyber_summary_df["Total Rides"] = pyber_summary_df["Total Rides"].map("{:,}".format)
pyber_summary_df["Total Drivers"] = pyber_summary_df["Total Drivers"].map("{:,}".format)
pyber_summary_df["Total Fares"] = pyber_summary_df["Total Fares"].map("${:,.2f}".format)
pyber_summary_df["Average Fare per Ride"] = pyber_summary_df["Average Fare per Ride"].map("${:,.2f}".format)
pyber_summary_df["Average Fare per Driver"] = pyber_summary_df["Average Fare per Driver"].map("${:,.2f}".format)
pyber_summary_df
  ```
  <img width="445" alt="Table1" src="https://user-images.githubusercontent.com/106962921/178345079-2b0cea90-ac93-486f-bb42-fd7ef1d6dd84.png">

# Summary:
Three business recommendations to address any disparities among the city types:
1. There are less drivers in rural area, although, the average fare per driver/ride is higher than urban and suburban areas. This could be indicative of PyBer users travelling longer distance. Hire more drivers in rural area to increase rural revenue.
2. The peak noted in late February as well as multiple peaks occuring in urban and rural areas may have occurred due to an event that led to increase in rides and fares. Research future events and allocate resources where they are needed, for example, allocating drivers from suburban area to work in urban and rural area and vice versa.
3. Urban areas have a higher revenue than suburban and rural area which indicates higher use of PyBer services. Promotions may entice loyal customers to ensure continued service with PyBer.
