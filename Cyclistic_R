#LOAD PACKAGES
library(tidyverse)
library(lubridate)
library(dplyr)
library(ggplot2)
library(tidyr)
library(ggpubr) 
library(here)
library(skimr) 
library(janitor)
library(RColorBrewer)
library(forcats)
library(ggrepel)
library(scales)

#IMPORT DATA
apr_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202104-divvy-tripdata.csv")
may_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202105-divvy-tripdata.csv")
jun_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202106-divvy-tripdata.csv")
jul_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202107-divvy-tripdata.csv")
aug_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202108-divvy-tripdata.csv")
sep_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202109-divvy-tripdata.csv")
oct_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202110-divvy-tripdata.csv")
nov_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202111-divvy-tripdata.csv")
dec_21 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202112-divvy-tripdata.csv")
jan_22 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202201-divvy-tripdata.csv")
feb_22 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202202-divvy-tripdata.csv")
mar_22 <- read_csv("C:\\Users\\kdmq3\\OneDrive\\Documents\\A Coursera Capstone Project\\Cyclistic\\Unzip\\202203-divvy-tripdata.csv")

#DATA EXPLORATION
data <- bind_rows(apr_21, may_21, jun_21, jul_21, aug_21, sep_21, oct_21, nov_21, dec_21, jan_22, feb_22, mar_22)
head(data)
summary(data)

#DATA CLEANING
clean_names(data)
data <- data %>% drop_na()

#THE FOLLOWING ANALYSIS COMPARES DIFFERENCES BETWEEN MEMBERS AND CASUALS

#Main color theme
palette1 <- brewer.pal(5, "Set2") 
colors <- c("#66C2A5", "#FC8D62")

#Distribution between members and casuals
membership <- data %>% group_by(member_casual) %>% summarize(counts=n(), percentage = n()/nrow(data))

ggplot(data=membership, aes(x=" ", y = percentage, fill = member_casual)) +
  geom_col(color="white") + 
  coord_polar("y", start = 0) + 
  geom_text(aes(label = paste0(round(percentage*100), "%")), position=position_stack(vjust=0.5)) +
  ggtitle("Membership Distribution") +
  scale_fill_manual(values = colors) +
  theme_void() +
  theme(plot.title = element_text(hjust = 0.5))

#Types of bike usage distribution
ride_types <- data %>% group_by(member_casual, rideable_type) %>% summarize(counts=n()) %>% mutate(percentage = percent(counts/sum(counts)))
ride_types$member_casual <- factor(ride_types$member_casual)
ride_types$rideable_type <- factor(ride_types$rideable_type)

ggplot(ride_types, aes(x=" ", y=counts, group=rideable_type, fill=rideable_type)) +
  geom_bar(stat = "identity", width = 1, position = position_fill()) +
  coord_polar("y", start = 0) + 
  facet_wrap(.~ member_casual) +
  geom_text(aes(label = percentage), position=position_fill(vjust=0.5)) +
  ggtitle("Types of bikes distributions") +
  theme_void() +
  theme(plot.title = element_text(hjust = 0.5))

#Average traveling time per trip each month
data$time_diff <- difftime(data$ended_at, data$started_at, units="mins")
data$year_month <- format(data$started_at, "%Y-%m")
data_avg_time <- data %>% group_by(year_month, member_casual) %>% summarize(avg_time=mean(time_diff))
data_avg_time <- data_avg_time[order(data_avg_time$year_month), ]

ggplot(data=data_avg_time, aes(x=year_month, y=avg_time, fill=member_casual)) + 
  geom_histogram(stat = "identity") +
  facet_wrap(.~ member_casual) +
  theme(axis.text.x = element_text(angle = 90)) +
  scale_color_manual(values = colors) +
  labs(title="Average traveling time per trip each month") +
  theme(plot.title = element_text(hjust = 0.5))

#Average traveling time per trip for each type of bike
data_avg_time_bike_type <- data %>% group_by(member_casual, rideable_type) %>% summarize(avg_time=mean(time_diff))

ggplot(data=data_avg_time_bike_type, aes(x=rideable_type, y=avg_time, fill=rideable_type)) + 
  geom_bar(stat = "identity", position = "dodge") +
  facet_wrap(.~ member_casual) +
  theme(axis.text.x = element_text(angle = 90)) +
  labs(title="Average traveling time for each different bike types", x="bike_type", y="avg_trip_time") +
  theme(plot.title = element_text(hjust = 0.5))

#Top 10 Starting station for docked_bike users
data_casual_db <- filter(data_casual, rideable_type=="docked_bike")
start_st_casual_db <- data_casual_db %>% group_by(start_station_name) %>% summarize(use_frequency=n()) %>% arrange(desc(use_frequency))
start_st_casual_db <- head(start_st_casual_db, 10)

ggplot(start_st_casual_db, aes(x=start_station_name, y=use_frequency)) +
  geom_bar(stat="identity", fill="#66C2A5", alpha=.6, width=.4) +
  coord_flip() +
  xlab("") +
  labs(title="Docked-Bikes Riders' Top 10 Start Stations")

#Frequency of use for each day of the week
data$week_day <- weekdays(data$started_at)
data_week_day <- data %>% group_by(week_day, member_casual) %>% summarize(use_frequency=n())
weekday_order <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday")
data_week_day$week_day <- factor(data_week_day$week_day, levels = weekday_order)

ggplot(data=data_week_day, aes(x=week_day, y=use_frequency, fill=member_casual)) + 
  geom_histogram(stat = "identity") +
  facet_wrap(.~ member_casual) +
  theme(axis.text.x = element_text(angle = 90)) +
  scale_color_manual(values = colors) +
  labs(title="Frequency of use for each day of the week") +
  theme(plot.title = element_text(hjust = 0.5))

#Frequency of use for time in the day when people start trips
data$start_hour <- format(data$started_at, format = "%H:00:00")
data_start_hour <- data %>% group_by(start_hour, member_casual) %>% summarize(frequency=n())
data_start_hour <- data_start_hour[order(data_start_hour$start_hour), ]

ggplot(data=data_start_hour, aes(x=start_hour, y=frequency, fill=member_casual)) + 
  geom_histogram(stat = "identity") +
  facet_wrap(.~ member_casual) +
  theme(axis.text.x = element_text(angle = 90)) +
  scale_color_manual(values = colors) +
  labs(title="Frequency of trip starting time") +
  theme(plot.title = element_text(hjust = 0.5))

#Top 10 most frequently used starting stations
data_casual <- filter(data, member_casual=="casual")
data_member <- filter(data, member_casual=="member")

start_st_casual <- data_casual %>% group_by(start_station_name) %>% summarize(use_frequency=n()) %>% arrange(desc(use_frequency))
start_st_casual <- head(start_st_casual, 10)
start_st_member <- data_member %>% group_by(start_station_name) %>% summarize(use_frequency=n()) %>% arrange(desc(use_frequency))
start_st_member <- head(start_st_member, 10)

ggplot(start_st_casual, aes(x=start_station_name, y=use_frequency)) +
  geom_bar(stat="identity", fill="#66C2A5", alpha=.6, width=.4) +
  coord_flip() +
  xlab("") +
  labs(title="Casual Riders' Top 10 Start Stations")

ggplot(start_st_member, aes(x=start_station_name, y=use_frequency)) +
  geom_bar(stat="identity", fill="#FC8D62", alpha=.6, width=.4) +
  coord_flip() +
  xlab("") +
  theme_bw() +
  labs(title="Membership Riders' Top 10 Start Stations")
