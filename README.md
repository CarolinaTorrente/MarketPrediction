# Summary of Project Idea & Goal

The main goal of this project is to develop a reliable model for predicting the market value of football players for a given season by identifying and analyzing key factors that contribute most significantly to their value.

Using advanced data analysis and machine learning techniques, we aim to detect patterns and relationships within player-specific attributes such as age, position, performance metrics, injury history, and nationality. Additionally, we consider external factors like league quality, club affiliations, and competition performance.

Furthermore, this project seeks to provide insights into how these variables interact and influence a player’s value over time. This will enable stakeholders such as clubs, agents, and analysts to make more informed decisions regarding transfers and player investments.

# Summary of the State of the Art & Differentiation

Football is one of the sports that handles the most money globally. Predicting the market value of players has been an active research area, with multiple tools and studies utilizing machine learning, data mining, and statistical analysis to identify trends and key influencing factors.

One example is Transfermarkt, a platform that showcases player valuations and performance trends through rich and structured datasets.

Despite the availability of these technologies, challenges persist, such as handling messy or incomplete data and ensuring model generalizability across leagues, countries, and historical periods.

Our project aims to differentiate itself by integrating multiple dimensions of player statistics to achieve a more accurate valuation. Additionally, we normalize market values to facilitate comparisons across different leagues and seasons. This approach helps mitigate variations in market value caused by inflation or market disparities.

Through this analysis, we can identify undervalued players with high potential, understand how players evolve throughout the seasons, and assess whether they perform differently across various leagues.

# Detailed Description of the Final Data Source

We collected data from Transfermarkt, a comprehensive database and marketplace for football player information. The platform provides structured data on players, teams, leagues, and competitions, including:

Player profiles (age, nationality, position, etc.)

Transfer histories with fees and dates

Estimated market values

Performance statistics (goals, assists, appearances, etc.)

Club and team data (rosters, coaches, stadiums, etc.)

The market value estimates and transfer details allow us to analyze trends in football economics, such as:

Rising stars and undervalued players

Transfer fee inflation

Market activity patterns in specific leagues or countries

Scraped data can power predictive models for player market values and trend visualization.

Additionally, Transfermarkt covers leagues worldwide, including major ones like the Premier League and La Liga, as well as emerging leagues. It also includes historical data, offering opportunities for longitudinal studies.

# Data Gathering Technique

After analyzing the website, we determined that the best scraping technique would be using BeautifulSoup. We extracted key data points, including player name, player ID, and nationality.

We then developed several methods to retrieve all market values, seasons, and positions for each player, as their value changes over time. Additionally, we collected relevant statistics for each competition and player.

Through this process, we built a structured dataset containing football player statistics from Transfermarkt. The dataset includes multiple seasons per player, providing insights that combine:

Gameplay-related metrics (appearances, goals, assists, substitutions)

Disciplinary records (yellow and red cards)

Player attributes (age, nationality, position, club affiliation)

Injury data (days missed, games affected)

Most importantly, we included market value and normalized market value, allowing for accurate player comparisons. Our analysis explores how on-field performance, injuries, and other factors influence a player's market value.

# Preprocessing

Loading and Preparing Data

Basic Inspection: Extracts and prints the list of column names.

Aggregation Function: Sums up columns containing certain keywords and replaces them with their total, dropping the original columns.

Applying Aggregations: Iterates through a list of metrics (e.g., appearances, goals) and aggregates related columns.

Feature Engineering:

Combines goal data across different competitions into a single column (goals).

Aggregates yellow card data.

Grouping and Aggregating: Groups data by Player and Season and applies aggregation functions:

first (e.g., age)

mean (e.g., market value)

sum (e.g., total appearances)

Rolling Metrics:

mean_goals: Calculates a rolling average of goals over the last three seasons.

goals_diff: Computes the season-over-season difference in goals.

Market_Value_normalized: Normalizes market value for easier comparison.

Handling Nulls: Cleans missing values in the dataset.

Processing Nationalities: Converts the Nationality column (stored as a string list) into a Python list and extracts the first nationality for each player.

Exporting Cleaned Data

# Analysis Techniques

We performed unsupervised and supervised analysis, as well as descriptive analysis, which is reflected in our dashboard.

## Descriptive Analysis (Dashboard)

Descriptive analysis was crucial for building a strong predictive model. During this phase, we extracted key insights into player performance and identified data inconsistencies, which were corrected to improve model accuracy.

We structured the analysis into three sections:

Player Overview

Club and League Overview

Position-Based Analysis

Data Issues and Fixes

Nationality Handling: Some players had multiple nationalities, which were stored as lists. This created aggregation issues, as different ordered lists were treated as distinct values. We resolved this by splitting and processing the column before plotting.

Duplicate Data: Player market values were recorded at both the start and end of the season, leading to overfitting. We adjusted the dataset accordingly.

Date Formatting Issue: Seasons were formatted as 12/13, but when uploaded to Locker Studio, they were misinterpreted as December 13th. We manually corrected approximately 13 seasons in Excel by converting the cells to text format.

Graphical Representation Challenge: We attempted to create a football field graph but faced issues in filtering and preserving coordinates.

## Unsupervised Analysis

Before implementing predictive models, we conducted Principal Component Analysis (PCA) to understand player distribution and detect correlations between variables.

Scaling & Normalization: Normalized market values for better visualization.

PCA Insights:

Lower market values (purple) are clustered near the origin, indicating common performance metrics among average or lower-tier players.

High-value players (yellow) are dispersed, suggesting unique performance characteristics.

Some players with low market values but distant from the center may be undervalued based on their statistical profile.

This analysis helped refine our approach by highlighting the need to account for unique performance factors rather than treating all players uniformly.

## Supervised models

Random Forest: Builds multiple decision trees and averages the results, reducing overfitting. Handles a wide range of data distributions and feature interactions.
XGBoost: gradient-boosted decision tree algorithm that uses regularization techniques (L1 and L2) to prevent overfitting.
Light GBM: Specifically designed for large datasets. Handles categorical features effectively by converting them into numerical formats internally.

### Steps:
Dummies of ‘Club’, ‘Position’ and ‘Nationality’.
Split of train and test sets with y as the market value normalized (target) and X the rest of the variables except from ‘Player’, ‘Season’ and ‘Market Value’.
Fine tuning of the parameters of the models.
Visualization of the results.
Ensemble and stacking of the models.
Comparison of the techniques.

### Key findings: Age, performance metrics, and injuries significantly influence market value.







