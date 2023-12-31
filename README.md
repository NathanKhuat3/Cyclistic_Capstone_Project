# Cyclistic_Capstone_Project
 
### INTRODUCTION

Hello there! This is my Cyclistic bike-share analysis case study capstone project for the Google Data Analytics course. In a hypothetical scenario, I am a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago and I have been asked by the marketing team to investigate the differences in behavior between Cyclistic’s 2 main types of customers: __annual members__ and __casual riders__

### ASK

__Main Objective:__ To convert the casual riders into annual members, which will provide sustainable revenue and enhance profit’s growth.

__Key Business Task:__ Investigate main differences in the way annual members and casual riders use Cyclistic

__Key Stakeholders:__  
Lily Moreno: The director of marketing and my manager  
Cyclistic marketing analytics team  
Cyclistic executive team  

### PREPARE

For the purpose of this project, the Cyclistic’s historical trip data will be used. The data has been made available by Motivate International Inc. under license, making it a credible and accurate data source. This data should still be verified by the manager to make sure that this is the appropriate dataset for analysis. 

### PROCESS

Upon initial inspection, the data appears to be clean and ready to use. The datasets from different months (from April 2021 - March 2022) will be imported and put into one main data frame called “data” for analysis.

### ANALYZE and SHARE

__Quick exploration of data__

1) First, we need to examine the current distribution of annual members and casual riders.

![image](https://github.com/NathanKhuat3/Cyclistic_Capstone_Project/assets/136769070/cd3eea29-4e70-4ae8-bc58-d5a8aacbc880)

*Analysis*: The majority of Cyclistic’s customers are annual members, however, a significant proportion of the customers remain casual riders (44%).

2) Another factor to quickly explore is the types of bike that each types of customer use

![image](https://github.com/NathanKhuat3/Cyclistic_Capstone_Project/assets/136769070/3f6ea810-959a-4b0a-9de4-5be542f9fd9b)

*Analysis*: The classic bike is the main preference for both types of customers. It is interesting to note that only casual riders use docked bikes while annual members do not. This can be a niche segment of customers to target specifically.

__An important factor of behavior is the average trip time for each customer type__

1) By month

![image](https://github.com/NathanKhuat3/Cyclistic_Capstone_Project/assets/136769070/b829f23a-716d-4490-aef9-02d9e862441d)

*Analysis*: Casual riders appear to have a significantly longer time per trip each month than annual members. In particular, casual riders have the longest average trip time in the summer months from April to June, exceeding 35 minutes per trip. 

To understand this discrepancy better, we can examine average trip time by types of bike.

2) By types of bike

![image](https://github.com/NathanKhuat3/Cyclistic_Capstone_Project/assets/136769070/92766c3a-9c67-4529-845d-bc34995a14bc)

*Analysis*: This illustration provides a clearer view of the phenomenon. While the travel time per trip for classic bike and electric bike users who are casual riders still eclipse their annual members counterparts, most of the discrepancy of the two customer types can be explained by the extraordinarily high average travel time of docked bike users. This suggests that docked bike riders, who are exclusively casual riders, have travel time that quadruples other types of bikes.

__Another crucial factor of behavior is frequency of usage for casual riders vs annual members__

By day of the week

![image](https://github.com/NathanKhuat3/Cyclistic_Capstone_Project/assets/136769070/e68ef198-77af-4c76-88d3-756058e14a15)

*Analysis*: Casual riders most frequently use Cyclistic in the weekends, specifically Saturday and report low usage during the week. In stark contrast, annual members use Cyclistic more consistently throughout the week, the weekend is the time when members use Cyclistic the least. A possible explanation for this is that members are more prone to use Cyclistic for commuting to work while casual riders predominantly use the bike-share service for other purposes, assumably health and entertainment. This is an area that requires further investigation. 

To dive deeper, we can examine the hour of the day in which trips are started.

By hour of the day

![image](https://github.com/NathanKhuat3/Cyclistic_Capstone_Project/assets/136769070/363ec379-38f3-4718-9513-ccc6d2e6fda4)


*Analysis*: For both customer types, the rate at which Cyclistic is used increases by the hour during daytime, peaking at 5pm when Cyclistic’s service is the busiest. The main difference is that there is a peak in usage for members at 8am, which serves as further evidence that a considerable proportion of annual members use Cyclistics service to commute to work and back. Cyclistics’s casual riders demonstrated no similar behavior. 

Now that we have had a good understanding of the “When?”, we can also look at the “Where?”

__Top 10 most used stations__

![image](https://github.com/NathanKhuat3/Cyclistic_Capstone_Project/assets/136769070/9a1a5bde-954a-48c5-997a-3db7b1412f2c)

*Analysis*: For Casual riders, the most popular starting station is Street Dr and Grand Ave” by a significant margin with over 60,000 trips made there during the period reported, followed by Millenium Park and Michigan Ave and Oak St. For annual members, the distribution of usage among starting stations is more even, with “Wells St & Elm St”, “Wells St & Concord ln” and “Kingsbury St and Kinzie St” being the busiest stations. This information can help inform the marketing teams of the most effective locations to place physical ads. 


### ACT

__Based on the analysis above, my top 3 recommendations are as follows:__

__1) A proportional discount program for membership fees based on minutes traveled per trip__  
  
Cyclistic should consider introducing this program. Given that casual riders usually have longer travel time each trip, this can be an effective way to incentivize the casual riders to convert to membership subscription, especially for docked bike users who have astronomically high travel time. The program should also highlight the benefits of membership for customers traveling extended periods of time  
  
__2) Weekend-specific promotions__  
  
From the analysis above, it is clear that casual riders are more likely to use Cyclistic’s services during the weekends. This is an opportunity for Cyclistic to promote their membership benefits on the weekends. This can range from app’s notifications to bonus credit for casual riders to build toward membership subscription. Specific time should also be prioritized for promotion such as 5pm when Cyclistic is the busiest.  
   
__3) Physical ads at popular stations__  
  
To target casual riders, Cyclistics should put up physical ads in the form of banners, billboards and brochures informing customers about membership’s advantages. In many cases clients may not subscribe to a membership due to not having a clear understanding of the merits. Having physical ads at the most optimal stations (such as Street Dr and Grand Ave) is crucial to converting casual riders.
