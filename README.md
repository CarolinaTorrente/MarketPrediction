Summary of Project Idea & Goal

The main goal of this project is to develop a reliable model for predicting the market value of football players for a given season by identifying and analyzing key factors that contribute most significantly to their value.

Using advanced data analysis and machine learning techniques, we aim to detect patterns and relationships within player-specific attributes such as age, position, performance metrics, injury history, and nationality. Additionally, we consider external factors like league quality, club affiliations, and competition performance.

Furthermore, this project seeks to provide insights into how these variables interact and influence a player’s value over time. This will enable stakeholders such as clubs, agents, and analysts to make more informed decisions regarding transfers and player investments.

Summary of the State of the Art & Differentiation

Football is one of the sports that handles the most money globally. Predicting the market value of players has been an active research area, with multiple tools and studies utilizing machine learning, data mining, and statistical analysis to identify trends and key influencing factors.

One example is Transfermarkt, a platform that showcases player valuations and performance trends through rich and structured datasets.

Despite the availability of these technologies, challenges persist, such as handling messy or incomplete data and ensuring model generalizability across leagues, countries, and historical periods.

Our project aims to differentiate itself by integrating multiple dimensions of player statistics to achieve a more accurate valuation. Additionally, we normalize market values to facilitate comparisons across different leagues and seasons. This approach helps mitigate variations in market value caused by inflation or market disparities.

Through this analysis, we can identify undervalued players with high potential, understand how players evolve throughout the seasons, and assess whether they perform differently across various leagues.

Detailed Description of the Final Data Source

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

Data Gathering Technique

After analyzing the website, we determined that the best scraping technique would be using BeautifulSoup. We extracted key data points, including player name, player ID, and nationality.

We then developed several methods to retrieve all market values, seasons, and positions for each player, as their value changes over time. Additionally, we collected relevant statistics for each competition and player.

Through this process, we built a structured dataset containing football player statistics from Transfermarkt. The dataset includes multiple seasons per player, providing insights that combine:

Gameplay-related metrics (appearances, goals, assists, substitutions)

Disciplinary records (yellow and red cards)

Player attributes (age, nationality, position, club affiliation)

Injury data (days missed, games affected)

Most importantly, we included market value and normalized market value, allowing for accurate player comparisons. Our analysis explores how on-field performance, injuries, and other factors influence a player's market value.

Preprocessing

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

mean_go
