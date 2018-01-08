# Thanksgiving Dinner Analysis

In this project, I will be using a jupyter notebook with Python, and analyzing data on Thanksgiving dinner in the US. I will primarily ue the Pandas library to aide with the analysis. 
The dataset came from FiveThirtyEight and can be found here ->
https://fivethirtyeight.com/features/heres-what-your-part-of-america-eats-on-thanksgiving/

The dataset is stored in the thanksgiving.csv file. It contains 1058 responses to an online survey about what Americans eat for Thanksgiving dinner. Each survey respondent was asked questions about what they typically eat for Thanksgiving, along with some demographic questions, like their gender, income, and location. This dataset will allow us to discover regional and income-based patterns in what Americans eat for Thanksgiving dinner.

The dataset has 65 columns, and 1058 rows. Most of the column names are questions, and most of the column values are string responses to the questions. Most of the columns are categorical, as a survey respondent had to select one of a few options. For example, one of the first column names is What is typically the main dish at your Thanksgiving dinner?. The potential responses are:

Turkey Other (please specify) Ham/Pork Tofurkey Chicken Roast beef I don't know Turducken Most of the columns follow the same question/response format as the above. There are also quite a few NaN values in the columns, which occurred when a survey respondent didn't fill out a question because they didn't want to, or it didn't apply to them.
