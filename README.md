# Analysing Crime Data - Using Machine Learning Models


# Abstract
Chicago is a bustling city full of energy, but it also grapples with a serious issue: crime. Gaining insights into the patterns and factors that influence crime rates is essential for creating safer communities. This study examines an extensive dataset of Chicago's crime incidents, seeking to uncover valuable information that can put up effective strategies.

In 2022 alone, over 40,000 crimes were reported in Chicago, each with significant consequences that affect individuals, families, and the city's overall well-being. This research explores various dimensions of crime in Chicago, focusing on:

**Spatial distribution:** By identifying areas with higher crime rates, resources can be allocated more efficiently, and preventative measures can be implemented. Understanding which areas have higher crime rates can help estimate the number of residents exposed to issues such as fear, safety concerns, and property damage.

**Temporal trends:** Analyzing crime patterns across different seasons and days of the week can help predict and address potential issues proactively. Recognizing seasonal trends and day-of-week patterns can help forecast periods with increased crime occurrences, enabling targeted interventions and potentially reducing the number of victims during those times.

**Location-based risk factors:** Examining the relationship between specific locations and types of crime can reveal potential risk factors. Identifying associations between specific locations and crime types can highlight areas with higher risks for certain crimes, helping individuals avoid these locations or take preventive measures.

Overall, this research aims to provide a deeper understanding of crime patterns in Chicago, contributing to the development of more effective crime prevention strategies.

# Introduction To The Project
This project uses data analysis to uncover valuable insights into crime patterns throughout Chicago city. By exploring how crime varies by area, season, and even day of the week, the study aims to identify effective crime prevention strategies.

### Research Questions:
**This study will address several critical questions about crime in Chicago:**

1. How does the frequency of various crime types differ across different districts in Chicago?

2. What are the most common locations for domestic-related crimes?

3. Are certain crime types more likely to lead to arrests than others?

4. How do crime rates and types change with different seasons and days of the week?

5. Can a machine learning model accurately predict the primary type of crime (e.g., theft, assault) using features?

# Data source:
Dataset is a publicly available dataset provides information on reported crime incidents in Chicago, hosted by the Chicago Police Department

(source: https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2/about_data)

This dataset reflects reported incidents of crime (with the exception of murders)

Though the full dataset 8 million entries (2001 to present), the initial analysis will focus on a subset of 1.5 million rows (2018 to 2024 July) due to resource constraints. As training on the full 8 million rows would be computationally intensive. The final dataset will consist of 1,594,870 rows.


# Data Content:

**The dataset provides information on reported crime incidents in Chicago, including various attributes for each crime record:**

ID: A unique identifier for each crime record.
Case Number: A unique identifier for each crime incident.
date: The date and time when the crime occurred.
block: The block address where the crime occurred.
iucr: Illinois Uniform Crime Reporting code, a numerical code that represents the crime type.
primary_type: The primary classification of the crime (e.g., theft, assault, robbery).
description: A detailed description of the crime.
location_description: The type of location where the crime occurred (e.g., street, residence, park).
arrest: Indicates whether an arrest was made for the crime (Yes/No).
domestic: Indicates whether the crime was domestic-related (Yes/No).
beat: The police beat where the crime occurred.
district: The police district where the crime occurred.
ward: The city ward where the crime occurred.
community_area: The community area where the crime occurred.
fbi_code: The FBI's classification for the crime.
x_coordinate: The X-coordinate of the location where the crime occurred (often -in a projected coordinate system like UTM).
y_coordinate: The Y-coordinate of the location where the crime occurred (often in a projected coordinate system like UTM).
year: The year when the crime occurred.
updated_on: The date and time when the record was last updated.
latitude: The latitude coordinate of the crime location. (This location is shifted from the actual location for partial redaction but falls on the same block.)
longitude: The longitude coordinate of the crime location. (This location is shifted from the actual location for partial redaction but falls on the same block.)
location: A combined field of latitude and longitude, often represented as a point on a map.


# Approach:
**1.Data Acquisition and Storage:**
I have Downloaded the Chicago crime data from the official website in .CSV format and imported it into Jupyter Notebook.

**2.Exploratory Data Analysis (EDA):**
Explore the data to understand its structure, identify any anomalies, and uncover relationships between different factors. Visualization libraries like Matplotlib and Seaborn will be used to create informative charts and graphs. Additionally, we'll leverage the Folium library for geospatial analysis to:

**Visualizing Crime Distribution:** Creating interactive maps to show the spatial distribution of various crime types across Chicago.
**Identifying Crime Hotspots:** Applying clustering techniques to identify areas with high concentrations of specific crimes.

**3.Data Cleaning and Feature Engineering:**
Based on the EDA, we addressed data quality issues such as missing values and inconsistencies. Feature engineering techniques also be applied to enhance model performance, such as encoding categorical variables and creating new features from existing data.

**4.Model Building and Evaluation:**
Main objective is to predict the type of crime. I have build and evaluated three machine learning models for this purpose:

**Logistic Regression:** This model will attempt to predict the primary crime type (e.g., theft, assault) based on features like date, location, and community area.
**Random Forest:** Similar to the logistic regression model, this will also predict crime type based on features like date, location, and community area.
**XGBoost :** This model might be explored to predict crime type using historical data on crime types and locations.
The performance of these models will be compared using metrics such as accuracy, precision, recall, and F1 score. The best-performing model will be selected for further analysis.

**5.Ensemble Model Construction:**
To potentially achieve better results, I created an ensemble model that combined the predictions of the individual models. This ensemble approach aimed to leverage the strengths of each model while compensating for their weaknesses. I used Python libraries like scikit-learn for this step and implemented **AdaBoost as the ensemble model, with Decision Trees as the weak learners.**



# Conclusion
This research project successfully analyzed crime data in Chicago to gain valuable insights and inform crime prevention strategies. Here's a summary of the key findings:

- We explored how crime frequency varies across districts, identified hotspots for domestic-related crimes, and analyzed crime trends based on season and day of the week.
- Machine learning models were built and evaluated to predict the primary type of crime based on various features.

Our analysis identified XGBoostClassifier as the strongest performing model. It achieved the highest accuracy (0.6) and precision (0.68) on training set correctly classifying the most data points with minimal errors. This model also generalizes well, performing well on unseen data in the testing set. It performs better than Rnadom Forest Classifier and Logistic Regression on all metrics. This model also outperformed our ensemble model AdaBoost. While XGBoostClassifier might take longer to train, its superior overall performance makes it the preferred choice for this project.

# Future Extensions:

This project lays the groundwork for further exploration. Here are some potential extensions:

- Integrate real-time data feeds (e.g., weather, social media) to enhance crime prediction models.

- Include data on race and sex and other socio economic factors in the analysis to explore potential racial disparities in crime rates.

- Move beyond basic prediction models and explore more sophisticated machine learning algorithms like deep learning models.

- Focus on specific crime types can provide better intuition.

- Create a crime map
