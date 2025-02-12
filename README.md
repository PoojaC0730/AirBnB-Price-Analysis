# AirBnB Price Analysis in New York City

## Overview

This project aims to analyze the factors influencing AirBnB prices in New York City. The analysis leverages a dataset containing information on listings, including location, room type, host details, and review statistics. The goal is to provide insights into the key drivers of pricing and identify potential areas for improvement for both hosts and guests.

## Data Source

The dataset used in this analysis is sourced from Kaggle [https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data]. The data includes the following features:

*   `id`: Listing ID
*   `name`: Name of the listing
*   `host_id`: Host ID
*   `host_name`: Host name
*   `neighbourhood_group`: Borough/area (e.g., Brooklyn, Manhattan)
*   `neighbourhood`: Specific neighborhood
*   `latitude`: Latitude coordinate
*   `longitude`: Longitude coordinate
*   `room_type`: Type of room (e.g., "Entire home/apt", "Private room")
*   `price`: Price per night
*   `minimum_nights`: Minimum number of nights required for a booking
*   `number_of_reviews`: Number of reviews the listing has received
*   `last_review`: Date of the most recent review
*   `reviews_per_month`: Average number of reviews per month
*   `calculated_host_listings_count`: Number of listings the host has in the area
*   `availability_365`: Number of days the listing is available in a year

## Data Cleaning and Preprocessing

The following steps were taken to clean and prepare the data for analysis:

*   **Missing Value Handling:**
    *   Missing values in the `reviews_per_month` column were imputed using the median value for each `neighbourhood_group`.
    *   Missing values in the `last_review` column were imputed using the median date for each `neighbourhood_group`.
*   **Outlier Removal:**
    *   Outliers in the `price` column were removed using the IQR method (values outside Q1 - 1.5 * IQR and Q3 + 1.5 * IQR).
    *   Outliers in the `minimum_nights` column were removed using the IQR method.
*   **Feature Engineering:**
    *   New features were created to extract the year, month, and day of the week from the `last_review` column. These features (`Year_last_review`, `Month_last_review`, `Day_last_review`) allow for time-based analysis.
    *   A new feature `price_per_review` was created, representing the price divided by the number of reviews (plus one to avoid division by zero).

## Exploratory Data Analysis (EDA)

The following EDA steps were performed to understand the data:

*   **Descriptive Statistics:** Calculated the average `number_of_reviews` for each `neighbourhood_group` to assess popularity.
*   **Correlation Analysis:** Calculated the correlation matrix between numerical features to identify potential relationships.
*   **Visualization:** Using countplot from the `seaborn` library to display distribution of `neighbourhood_group` feature.

## Key Findings

*   **Review Frequency:** The `neighbourhood_group` with the highest average number of reviews is Staten Island (average: 36.75). Queens and Bronx are also relatively high.  Manhattan has the lowest average number of reviews (27.32). This suggests that listings in Staten Island, Queens and Bronx are very popular.
*   **Categorical Feature Observations:** The most common `neighbourhood_group` is Manhattan. The most common `room_type` is Entire home/apt.
*   **Price Range:** The minimum price is 0, and the maximum price is 10000.
*   **Number of Reviews:** The minimum number of reviews is 0 and the maximum number of reviews is 629.
*   **Availability:** The minimum availability is 0 days and the maximum is 365 days.

## Notebook Structure

The project is implemented in a Jupyter Notebook (`AirBnB-Price-Analysis.ipynb`). The notebook is organized as follows:

1.  **Data Loading and Initial Exploration:** Loading the dataset and displaying initial rows.
2.  **Data Cleaning and Preprocessing:** Handling missing values and outliers.
3.  **Feature Engineering:** Creating new features.
4.  **Exploratory Data Analysis:** Analyzing the relationships between variables.
5.  **Conclusions:** Summarizing the key findings and potential future work.

## Dependencies

*   pandas
*   numpy
*   matplotlib
*   seaborn

## Usage

1.  Clone the repository.
2.  Install the required dependencies: `pip install pandas numpy matplotlib seaborn`
3.  Open and run the Jupyter Notebook (`AirBnB-Price-Analysis.ipynb`).

## Author

Pooja Chaudhari

## License

MIT License
