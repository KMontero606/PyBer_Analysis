# PyBer_Analysis
# 1.	Overview of the analysis:

V. Isualize has assigned a brand-new assignment to create a summary DataFrame of the ride-sharing data by city type, create a multiple-line graph that shows the total weekly fares for each city type and submit a written report that summarizes how the data differs by city type and how those differences can be used by decision-makers at PyBer.
  
# 2.	Results:

o	Description of the differences in ride-sharing data among the different city types. 

o	Ride-sharing data of the following:

  o	total rides:
  ## 1. Get the total rides for each city type
  total_rides_df = pyber_data_df.groupby(["type"]).count()["ride_id"]
  total_rides_df.head()
  type
  Rural        125
  Suburban     625
  Urban       1625
  Name: ride_id, dtype: int64

  
  o	total drivers 
  
  o	total fares 
  
  o	average fare per ride and driver 
  
  o	total fare by city type

# 3.	Summary:
o	There is a statement summarizing three business recommendations to the CEO for addressing any disparities among the city types. (4 pt)
