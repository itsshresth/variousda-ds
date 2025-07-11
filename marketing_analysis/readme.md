##Marketing Analytics Case Study

## Overview

ShopEasy, an online retail business, faced challenges with declining customer engagement and conversion rates despite increased marketing investments. This project presents a comprehensive data analytics solution to identify improvement areas and optimize marketing strategies.

## Project Objectives

- **Increase Conversion Rates:** Identify bottlenecks in the customer journey and recommend actionable improvements.
- **Enhance Customer Engagement:** Analyze which content types and channels drive the highest engagement.
- **Improve Customer Feedback Scores:** Extract insights from customer reviews and sentiment to guide product and service enhancements.


## Data Sources Utilized

- **Customer Reviews:** Text feedback on products and services.
- **Social Media Comments:** Audience sentiment and engagement data.
- **Campaign Performance Metrics:** Data on reach, clicks, conversions, and spend.
- **Customer Journey Table:** Tracks user navigation and drop-off points.
- **Engagement Data Table:** Interaction metrics for various content types.
- **Customers, Products, Geography Tables:** Demographic and product-level insights.


## Tools \& Technologies

- **SQL:** Data cleaning, transformation, and initial insights.
- **Python (NLTK, pyodbc):** Sentiment analysis and data manipulation.
- **Power BI:** Data integration, relationship management, and interactive dashboard creation.


## Solution Workflow

### 1. Data Cleaning \& Preparation (SQL)

- **Formatting \& Trimming:** Standardized text fields for consistency.
- **Referencing \& Value Mapping:** Unified reference keys across tables for robust joins.
- **Duplicate \& Null Handling:** Removed duplicate records and replaced null values to ensure data integrity.
- **Insight Extraction:** Used SQL queries for descriptive statistics and key metric calculations.

![SQL QUERY WITH RESULT1](https://github.com/itsshresth/variousda-ds/blob/master/marketing_analysis/sql%20results/Screenshot%202025-07-11%20142916.png)
![SQL QUERY WITH RESULT2](https://github.com/itsshresth/variousda-ds/blob/master/marketing_analysis/sql%20results/Screenshot%202025-07-11%20142930.png)
![SQL QUERY WITH RESULT3](https://github.com/itsshresth/variousda-ds/blob/master/marketing_analysis/sql%20results/Screenshot%202025-07-11%20142943.png)

### 2. Customer Engagement \& Sentiment Analysis (Python)

- **Sentiment Analysis:** Leveraged NLTK for natural language processing and sentiment scoring of customer reviews and social media comments.
- **Database Connectivity:** Utilized pyodbc to extract, process, and update sentiment data directly from SQL databases.
- **Insight Generation:** Identified recurring themes and customer pain points.


### 3. Data Visualization \& Dashboarding (Power BI)

- **Data Import:** Loaded cleaned and enriched tables into Power BI.
- **Relationship Management:** Established relationships between tables (customers, products, engagement, geography) for unified analysis.
- **Interactive Dashboards:** Built dynamic dashboards to visualize:
    - Conversion rates by month and product
    - Customer engagement trends (views, clicks, likes)
    - Sentiment distribution and feedback analysis
    - Content type performance
![BI DASHBOARD](https://github.com/itsshresth/variousda-ds/blob/master/marketing_analysis/Screenshot%202025-07-11%20153731.png)


## Key Insights \& Achievements

- **Conversion Rate Trends:** Identified strong seasonality, with lowest rates in May (4.3%) and highest in January (18.5%).
- **Engagement Decline:** Detected a significant drop in views and interactions from August onwards, highlighting the need for more engaging content.
- **Customer Feedback:** Majority of reviews were positive (4-5 stars), but the average rating (3.7) fell below the target, indicating room for improvement.
- **Sentiment Analysis:** Positive sentiment dominated, but mixed and negative reviews revealed actionable areas for product and service enhancements.


## Impactful Results

- **Data-Driven Recommendations:** Actionable insights to optimize marketing spend, improve content strategies, and enhance customer experience.
- **Automated Reporting:** Reduced manual reporting time and increased data accessibility for stakeholders.
- **Business Value:** Enabled ShopEasy to make informed decisions, improving both engagement and conversion outcomes.


## Skills Demonstrated

- **Advanced Data Cleaning \& SQL Querying**
- **Natural Language Processing \& Sentiment Analysis**
- **Data Integration \& Relationship Management**
- **Interactive Dashboard Development (Power BI)**
- **Business Insight Generation \& Communication**


## How to Use This Repository

1. **Data Preparation:** Use provided SQL scripts to clean and preprocess raw data.
2. **Sentiment Analysis:** Run Python scripts to analyze customer feedback and update sentiment scores.
3. **Visualization:** Open the Power BI dashboard to explore interactive reports and key business metrics.

*This project showcases end-to-end data analytics skills, transforming raw business data into actionable insights and compelling visualizations to drive strategic improvements at ShopEasy.*
