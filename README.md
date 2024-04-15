# Project
FIFA World Cup 2022 Winner Prediction using Python and Machine Learning
As one of the most popular sports on the planet, football has always been followed very closely by a large number of people. In recent years, new types of data have been collected for many games in various countries, such as play-by-play data including information on each shot or pass made in a match.

The collection of this data has placed Data Science on the forefront of the football industry with many possible uses and applications:
•	Match strategy, tactics, and analysis
•	Identifying players, playing styles
•	Player acquisition, player valuation, and team spending
•	Training regimens and focus
•	Injury prediction and prevention using test results and workloads
•	Performance management and prediction
•	Tournament design and scheduling
•	Betting odds calculation
METHODOLOGY
Our main objectives of prediction are "Win / Lose / Draw" and "Goal Difference". In this work, we do two main experiments, for each experiment we follow this procedure
•	First we perform "normalization" of features, convert category to number
•	Then we use the best model to do prediction on 10-fold cross validation (9 folds for training and 1 fold for testing) to achieve the mean of test error. This error is more reliable.
Experiment 1. Build classifiers for "Win / Lose / Draw" from 2005. Because feature "Bet Odds" are only available after 2005 so we only conduct experiments for this period of time.
Experiment 2. Build classifiers for "Goal Difference" for "World Cup" and "UEFA EURO" after 2010. The reason is because features of "Squad Strength" are not always available before 2010, some national teams does not have database of squad strength in FIFA Video Games. We know that tackling prediction with regression would be hard so we turn "Goal Difference" into classification by defining labels as follows:
Team A vs. Team B 
•	"win_1": A wins with 1 goal differences
•	"win_2": A wins with 2 goal differences
•	"win_3": A wins with 3 or more goal differences
•	"lose_1": B wins with 1 goal differences
•	"lose_2": B wins with 2 goal differences
•	"lose_3": A wins with 3 or more goal differences
•	"draw_0": Draw
Feature Selection
1. Importing necessary libraries:
   - pandas: for data manipulation and analysis.
   - datetime: for working with dates and times.
   - numpy: for mathematical operations on arrays and matrices.
   - matplotlib.pyplot: for creating visualizations.
   - seaborn: for data visualization based on matplotlib.
   - warnings: for filtering warnings.

2. Reading the dataset:
   - The code reads the dataset from the CSV file 'international_matches.csv' 
     using the pandas library and assigns it to the Data Frame 'df'.
   - The head() function is used to display the first few rows of the Data Frame.
   - The shape attribute is used to display the dimensions of the DataFrame.
   - The info() method is used to display information about the DataFrame, 
     including the data types and missing values.

3. Data Wrangling:
   - The 'date' column is converted to datetime format using pd.to_datetime().
   - The 'fifa_rank' DataFrame is created by selecting relevant columns from 'df' 
     and renaming them for home and away teams.
   - The 'fifa_rank' DataFrame is sorted by team and date in descending order.
   - The 'row_number' column is added to track the rank order of each team.
   - The 'fifa_rank_top' DataFrame is created by selecting the top-ranked team 
     for each team and dropping the 'row_number' column.
4. Exploratory Data Analysis:
   - The 'columns_contains_null' list is created to store column names that 
     contain null values.
   - The list is printed to show the columns with null values.

5. Handling Missing Values:
   - A list named 'wc_2022' is created with the names of the teams participating 
     in the 2022 FIFA World Cup.
   - A nested loop is used to iterate over teams and columns with null values.
   - For each team and column, the missing values are filled with the mean value 
     of the corresponding column where the team name matches.
6. Analyzing Home Team Advantage:
   - The 'home_team' Data Frame is created to store the country, home team score, 
     and away team score.
   - The 'home_wins' Data Frame is created by selecting rows where the home team 
     has a higher score than the away team.
   - The 'home_loss' Data Frame is created by selecting rows where the home team 
     has a lower score than the away team.
   - The 'home_advantage' Data Frame is created by combining 'home_wins' and 
     'home_loss'.
   - A pie chart is plotted to visualize the percentage of home team wins and 
     losses.

7. Analyzing Team Wins:
   - The 'hometeam' Data Frame is created to store the date, home team, home team 
     score, and away team score.
   - The 'home_wins' Data Frame is created by selecting rows where the home team 
     has a higher score than the away team.
   - The 'home_loss' Data Frame is created by selecting rows where the home team 
     has a lower score than the away team.
   - The 'team_streak' Data Frame is created by combining 'home_wins' and 
     'home_loss'.
   - The value counts of each team are calculated to determine the team with the 
     most wins.

8. Analyzing Winning Percentage based on Rank:
   - Two functions are defined: 'victory' to determine the winner based on scores 
     and 'rank' to compare the ranks of two teams.
   - The 'winner' and 'better_rank' columns are created in the 'df' DataFrame 
     using the defined functions.
Data features
 We will now present the different tables and features that we have in our 
 database and that we can use in our models:
•	Matches table
–	ID
–	League ID
–	Season
–	Date
–	Home team ID
–	Away team ID

–	Home team goals scored
–	Away team goals scored
–	Home team possession
–	Away team possession
–	Home win odds
–	Draw odds
–	Away win odds
Events tables:
Here is a list of the different match events tables that we have extracted:
–	Goals
–	Shots on target
–	Shots off target
–	Corners
–	Crosses
–	Cards
–	Fouls
For each of these match event tables, we have the following features:
–	ID
–	Type
–	Subtype
–	Game ID
–	Team ID
–	Player ID
–	Distance to goal (only for goals and shots)
–	Angle to goal (only for goals and shots)
–	Time elapsed
Model Training 
The logistic regression model is trained using the generated features and the target variable indicating whether the home team has won the match. The model is trained on the training set and evaluated on the test set using  the receiver operating characteristic (ROC) curve and the area under the curve (AUC) score

![image](https://github.com/dheerajk31863/Projects/assets/167091638/585d4674-6baa-4572-bcd6-4ca7bf707a5b)
Result Analysis 
The results of the simulation are analyzed and visualized. The winners and probabilities at each stage (round of 16, quarterfinal, semifinal, and final) are extracted from the simulation results. The most common winners at each stage are identified and plotted in horizontal bar charts.
![image](https://github.com/dheerajk31863/Projects/assets/167091638/576d634e-013f-4277-ab5e-8dc3d96de4ae)
![image](https://github.com/dheerajk31863/Projects/assets/167091638/26eff439-37df-4d04-bbce-8048313acad0)
![image](https://github.com/dheerajk31863/Projects/assets/167091638/5b0c4243-768e-4e96-9d4b-3d997a062b4e)
Results and Analysis
Top 10 strongest teams
![image](https://github.com/dheerajk31863/Projects/assets/167091638/b22d6495-6e76-41cb-b516-63624cb3e861)
 Is there such a thing as home team advantage?
![image](https://github.com/dheerajk31863/Projects/assets/167091638/647c4ace-8e17-4b54-a0dc-4bf42f1164b8)
Which team has the most wins?
![image](https://github.com/dheerajk31863/Projects/assets/167091638/4467fa7d-a505-4a1c-b0ef-8a5ecf14b2f2)
What is the winning percentage comparing when the highest-ranked team plays against the lowest-ranked team?
![image](https://github.com/dheerajk31863/Projects/assets/167091638/2a0ba0af-1881-4b30-8eba-24cbdba2958b)
Top 10 Team which have strongest Defender, midfielder, offense?
![image](https://github.com/dheerajk31863/Projects/assets/167091638/9b387795-24c7-4e57-9d96-7831e033cbfc)
Winner prediction
![image](https://github.com/dheerajk31863/Projects/assets/167091638/da8c5409-04be-46d0-ac57-ffce5532be41)
#Winner Prediction of World Cup 2022 is Brazil

Interpretation:
1.	France has most win-rate in round-16 until semi-final World Cup 2022
2.	Senegal and Serbia most likely the weakest teams, for less appearance in Finals;
3.	Top 3 Teams are Brazil, Belgium and France with more than 10% chances of winning the tournament.
4.	Team which has most win chance to win the world cup 2022 is Brazil
