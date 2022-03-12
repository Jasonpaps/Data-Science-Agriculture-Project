# Data Science Interview Project: Feature Engineering

# Scenario: 
You and your team are building a random-forest model to predict the yield of sugarcane fields at harvest. Your job is to look at the time-series data provided and derive a number of features from it that you think are worth testing further. You will then present these ideas to your team as well as your planned methodology about how you are going to test the value of these features further on a larger data set.  You are also free to propose other interesting ideas for features you had while exploring the data, but have not had time to build.

# Rules and Criteria:
1. Project must be done in python. Feel free to use any python libraries. 
2. Feature ideas can be your own and/or from papers. Please link to any papers used. 
3. Feel free to ignore parts of the provided dataset completely and spend your time in areas you believe highlight your skills. Dive deep into a single feature or two or present a broad set of simple features, both are valid options.
4. Project should not take more than a few hours. If you find yourself spending too much time on the project, feel free to make notes about how you would continue if you had more time. Your ability to articulate thoughts and ideas is more important than your code.
5. Have A plan on how you would analyze how suitable the features you developed are for potential inclusion in the final machine learning model. 
6. Feel free to make some assumptions, just be aware of any assumptions you made and let us know what they were.
7. Feel free, but not obligated to ask questions.




# About the Data:
1. Cultivations.csv: This is a collection of five sugarcane fields over a single season. It has information about the fields' start date and harvest date as well as the fields id, which should help you link the csv files together.
   1. Cultivation_id: unique id used to link cultivation to other files.
   2. Cultivation_name: human readable name for the cultivation (i.e. sugarcane field)
   3. Harvest_date: date field was harvested
   4. grow_start_date: date field started growing. 
   5. Yield: metrics tons per hectare harvested from the field. 
      1. This value would be the eventual target of the machine learning model.


2. Msavi_mean.csv: This is a collection of satellite imaging data taken from the landsat or sentinel satellite missions. In it’s raw format the data is a time-series of 2D imagings. However, in this csv, each 2D image has been aggregated into a single value which is the mean of the images cloud-free pixels.
   1. Cultivation_id: unique id used to link cultivation to other files.
   2. Meta_data: 
      1. pixel_count: total number of pixels used to display the field. 
      2. Unmasked_count: number of pixels that are cloud free.
      3. Unmasked_fraction: percentage of pixels that are cloud free.
   3. Observation_date: date the image was taken
   4. Data_value: mean value of all un-masked pixels.
      1. The data here is MSAVI2 data which is a common agricultural index. You can read more about it here: https://wiki.landscapetoolbox.org/doku.php/remote_sensing_methods:modified_soil-adjusted_vegetation_index


3. Weather.csv: This file contains the weather data for each field.
   1. Observation_date: date the image was taken
   2. Cultivation_id: unique id used to link cultivation to other files.        
   3. Weather_data:
      1. Et: evapotranspiration measured in mm per day.
         1. Evapotranspiration (ET) is the sum of evaporation and plant transpiration from the Earth's land and ocean surface to the atmosphere. Evaporation accounts for the movement of water to the air from sources such as the soil, canopy interception, and bodies of water. Transpiration accounts for the movement of water within a plant and the subsequent loss of water as vapor through stomata in its leaves. Evapotranspiration is an important part of the water cycle.
      2. Prcp: precipitation (mm/day)
      3. Tmax: max temperature ( C )
      4. Tmin: min temperature( C )
      5. Gdd12: growing degree days, with a base temperature of 12c 
         1. See: https://en.wikipedia.org/wiki/Growing_degree-day
      6. Smi_5: soil moisture index at 5 cm depth 
         1. This index is computed using the permanent wilting point and the field capacity, which both depend on the geographical location (soil type). The index is 0 if the permanent wilting point is reached and 1 at field capacity. Note that the index can exceed 1 after rainfall events.
      7. Smi_15: soil moisture index at 15 cm depth
         1. See above
      8. Smi_50: soil moisture index at 50 sm depth
         1. See above
