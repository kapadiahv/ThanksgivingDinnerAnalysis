
# Thanksgiving Dinner Analysis

In this first python based project I will analyzing data on Thanksgiving dinner in the US. . I will primarily be using Python and the Pandas libraty to preform aalysis with. The dataset came from FiveThirtyEight.

The dataset is stored in the thanksgiving.csv file. It contains 1058 responses to an online survey about what Americans eat for Thanksgiving dinner. Each survey respondent was asked questions about what they typically eat for Thanksgiving, along with some demographic questions, like their gender, income, and location. This dataset will allow us to discover regional and income-based patterns in what Americans eat for Thanksgiving dinner.

The dataset has 65 columns, and 1058 rows. Most of the column names are questions, and most of the column values are string responses to the questions. Most of the columns are categorical, as a survey respondent had to select one of a few options. For example, one of the first column names is What is typically the main dish at your Thanksgiving dinner?. The potential responses are:

Turkey
Other (please specify)
Ham/Pork
Tofurkey
Chicken
Roast beef
I don't know
Turducken
Most of the columns follow the same question/response format as the above. There are also quite a few NaN values in the columns, which occurred when a survey respondent didn't fill out a question because they didn't want to, or it didn't apply to them.

Here are the first few rows of the dataset:


```python
import pandas as pd
data = pd.read_csv("thanksgiving.csv", encoding="Latin-1",)
data.head(5)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>RespondentID</th>
      <th>Do you celebrate Thanksgiving?</th>
      <th>What is typically the main dish at your Thanksgiving dinner?</th>
      <th>What is typically the main dish at your Thanksgiving dinner? - Other (please specify)</th>
      <th>How is the main dish typically cooked?</th>
      <th>How is the main dish typically cooked? - Other (please specify)</th>
      <th>What kind of stuffing/dressing do you typically have?</th>
      <th>What kind of stuffing/dressing do you typically have? - Other (please specify)</th>
      <th>What type of cranberry saucedo you typically have?</th>
      <th>What type of cranberry saucedo you typically have? - Other (please specify)</th>
      <th>...</th>
      <th>Have you ever tried to meet up with hometown friends on Thanksgiving night?</th>
      <th>Have you ever attended a "Friendsgiving?"</th>
      <th>Will you shop any Black Friday sales on Thanksgiving Day?</th>
      <th>Do you work in retail?</th>
      <th>Will you employer make you work on Black Friday?</th>
      <th>How would you describe where you live?</th>
      <th>Age</th>
      <th>What is your gender?</th>
      <th>How much total combined money did all members of your HOUSEHOLD earn last year?</th>
      <th>US Region</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4337954960</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>Middle Atlantic</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4337951949</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Other (please specify)</td>
      <td>Homemade cranberry gelatin ring</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>18 - 29</td>
      <td>Female</td>
      <td>$50,000 to $74,999</td>
      <td>East South Central</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4337935621</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>Mountain</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4337933040</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$200,000 and up</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4337931983</td>
      <td>Yes</td>
      <td>Tofurkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$100,000 to $124,999</td>
      <td>Pacific</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 65 columns</p>
</div>



## All columns associated to the dataset


```python
data.columns.tolist()
```




    ['RespondentID',
     'Do you celebrate Thanksgiving?',
     'What is typically the main dish at your Thanksgiving dinner?',
     'What is typically the main dish at your Thanksgiving dinner? - Other (please specify)',
     'How is the main dish typically cooked?',
     'How is the main dish typically cooked? - Other (please specify)',
     'What kind of stuffing/dressing do you typically have?',
     'What kind of stuffing/dressing do you typically have? - Other (please specify)',
     'What type of cranberry saucedo you typically have?',
     'What type of cranberry saucedo you typically have? - Other (please specify)',
     'Do you typically have gravy?',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Brussel sprouts',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Carrots',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Cauliflower',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Corn',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Cornbread',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Fruit salad',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Green beans/green bean casserole',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Macaroni and cheese',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Mashed potatoes',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Rolls/biscuits',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Squash',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Vegetable salad',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Yams/sweet potato casserole',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Other (please specify)',
     'Which of these side dishes aretypically served at your Thanksgiving dinner? Please select all that apply. - Other (please specify).1',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Apple',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Buttermilk',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Cherry',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Chocolate',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Coconut cream',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Key lime',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Peach',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Pecan',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Pumpkin',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Sweet Potato',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - None',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Other (please specify)',
     'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Other (please specify).1',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Apple cobbler',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Blondies',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Brownies',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Carrot cake',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Cheesecake',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Cookies',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Fudge',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Ice cream',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Peach cobbler',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - None',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Other (please specify)',
     'Which of these desserts do you typically have at Thanksgiving dinner? Please select all that apply.   - Other (please specify).1',
     'Do you typically pray before or after the Thanksgiving meal?',
     'How far will you travel for Thanksgiving?',
     "Will you watch any of the following programs on Thanksgiving? Please select all that apply. - Macy's Parade",
     'What\'s the age cutoff at your "kids\' table" at Thanksgiving?',
     'Have you ever tried to meet up with hometown friends on Thanksgiving night?',
     'Have you ever attended a "Friendsgiving?"',
     'Will you shop any Black Friday sales on Thanksgiving Day?',
     'Do you work in retail?',
     'Will you employer make you work on Black Friday?',
     'How would you describe where you live?',
     'Age',
     'What is your gender?',
     'How much total combined money did all members of your HOUSEHOLD earn last year?',
     'US Region']



## How many people celebrate Thanksgiving?


```python
data['Do you celebrate Thanksgiving?'].value_counts()
```




    Yes    980
    No      78
    Name: Do you celebrate Thanksgiving?, dtype: int64



## Create a dataset that only contains people who answered yes to celebrating Thanksgiving.


```python
#Remove folks who have not celebrated thanksgiving
celebrate_thanksgiving=data.loc[data['Do you celebrate Thanksgiving?'] != "True"]
celebrate_thanksgiving
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>RespondentID</th>
      <th>Do you celebrate Thanksgiving?</th>
      <th>What is typically the main dish at your Thanksgiving dinner?</th>
      <th>What is typically the main dish at your Thanksgiving dinner? - Other (please specify)</th>
      <th>How is the main dish typically cooked?</th>
      <th>How is the main dish typically cooked? - Other (please specify)</th>
      <th>What kind of stuffing/dressing do you typically have?</th>
      <th>What kind of stuffing/dressing do you typically have? - Other (please specify)</th>
      <th>What type of cranberry saucedo you typically have?</th>
      <th>What type of cranberry saucedo you typically have? - Other (please specify)</th>
      <th>...</th>
      <th>Have you ever tried to meet up with hometown friends on Thanksgiving night?</th>
      <th>Have you ever attended a "Friendsgiving?"</th>
      <th>Will you shop any Black Friday sales on Thanksgiving Day?</th>
      <th>Do you work in retail?</th>
      <th>Will you employer make you work on Black Friday?</th>
      <th>How would you describe where you live?</th>
      <th>Age</th>
      <th>What is your gender?</th>
      <th>How much total combined money did all members of your HOUSEHOLD earn last year?</th>
      <th>US Region</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>4337954960</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>Middle Atlantic</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4337951949</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Other (please specify)</td>
      <td>Homemade cranberry gelatin ring</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>18 - 29</td>
      <td>Female</td>
      <td>$50,000 to $74,999</td>
      <td>East South Central</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4337935621</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>Mountain</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4337933040</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$200,000 and up</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4337931983</td>
      <td>Yes</td>
      <td>Tofurkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$100,000 to $124,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>5</th>
      <td>4337929779</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>6</th>
      <td>4337924420</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>Rural</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$25,000 to $49,999</td>
      <td>East North Central</td>
    </tr>
    <tr>
      <th>7</th>
      <td>4337916002</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Rural</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>Prefer not to answer</td>
      <td>Mountain</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4337914977</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>Middle Atlantic</td>
    </tr>
    <tr>
      <th>9</th>
      <td>4337899817</td>
      <td>Yes</td>
      <td>Other (please specify)</td>
      <td>Turkey and Ham</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Other (please specify)</td>
      <td>Both Canned and Homemade</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$25,000 to $49,999</td>
      <td>East South Central</td>
    </tr>
    <tr>
      <th>10</th>
      <td>4337899680</td>
      <td>No</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$25,000 to $49,999</td>
      <td>Mountain</td>
    </tr>
    <tr>
      <th>11</th>
      <td>4337893416</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$25,000 to $49,999</td>
      <td>Middle Atlantic</td>
    </tr>
    <tr>
      <th>12</th>
      <td>4337888291</td>
      <td>Yes</td>
      <td>Ham/Pork</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>East North Central</td>
    </tr>
    <tr>
      <th>13</th>
      <td>4337878450</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>Middle Atlantic</td>
    </tr>
    <tr>
      <th>14</th>
      <td>4337878351</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>60+</td>
      <td>Male</td>
      <td>$50,000 to $74,999</td>
      <td>West North Central</td>
    </tr>
    <tr>
      <th>15</th>
      <td>4337857295</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$200,000 and up</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>16</th>
      <td>4337856362</td>
      <td>Yes</td>
      <td>Turducken</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Doesn't apply</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$200,000 and up</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>17</th>
      <td>4337854106</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>East North Central</td>
    </tr>
    <tr>
      <th>18</th>
      <td>4337844879</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$25,000 to $49,999</td>
      <td>Mountain</td>
    </tr>
    <tr>
      <th>19</th>
      <td>4337823612</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>East North Central</td>
    </tr>
    <tr>
      <th>20</th>
      <td>4337820281</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>21</th>
      <td>4337813502</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Fried</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Urban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>22</th>
      <td>4337809020</td>
      <td>No</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>Middle Atlantic</td>
    </tr>
    <tr>
      <th>23</th>
      <td>4337793158</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>24</th>
      <td>4337792130</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Female</td>
      <td>$50,000 to $74,999</td>
      <td>West South Central</td>
    </tr>
    <tr>
      <th>25</th>
      <td>4337790002</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$200,000 and up</td>
      <td>Middle Atlantic</td>
    </tr>
    <tr>
      <th>26</th>
      <td>4337783794</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$50,000 to $74,999</td>
      <td>South Atlantic</td>
    </tr>
    <tr>
      <th>27</th>
      <td>4337779071</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Suburban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$100,000 to $124,999</td>
      <td>East North Central</td>
    </tr>
    <tr>
      <th>28</th>
      <td>4337778119</td>
      <td>Yes</td>
      <td>Other (please specify)</td>
      <td>Varies</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Female</td>
      <td>Prefer not to answer</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>29</th>
      <td>4337774090</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1028</th>
      <td>4335956575</td>
      <td>No</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>60+</td>
      <td>Male</td>
      <td>Prefer not to answer</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1029</th>
      <td>4335955478</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>60+</td>
      <td>Male</td>
      <td>$50,000 to $74,999</td>
      <td>South Atlantic</td>
    </tr>
    <tr>
      <th>1030</th>
      <td>4335955206</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>45 - 59</td>
      <td>Male</td>
      <td>$10,000 to $24,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1031</th>
      <td>4335955152</td>
      <td>Yes</td>
      <td>Ham/Pork</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>45 - 59</td>
      <td>Female</td>
      <td>$75,000 to $99,999</td>
      <td>West North Central</td>
    </tr>
    <tr>
      <th>1032</th>
      <td>4335955050</td>
      <td>No</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>Prefer not to answer</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1033</th>
      <td>4335954681</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>East South Central</td>
    </tr>
    <tr>
      <th>1034</th>
      <td>4335954394</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Other (please specify)</td>
      <td>Rotisserie</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Female</td>
      <td>Prefer not to answer</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1035</th>
      <td>4335954376</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$25,000 to $49,999</td>
      <td>East North Central</td>
    </tr>
    <tr>
      <th>1036</th>
      <td>4335954286</td>
      <td>No</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>30 - 44</td>
      <td>Female</td>
      <td>$50,000 to $74,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1037</th>
      <td>4335954207</td>
      <td>Yes</td>
      <td>Other (please specify)</td>
      <td>salmon</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Female</td>
      <td>$10,000 to $24,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1038</th>
      <td>4335954131</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>60+</td>
      <td>Male</td>
      <td>$100,000 to $124,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1039</th>
      <td>4335953888</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>18 - 29</td>
      <td>Female</td>
      <td>$75,000 to $99,999</td>
      <td>East South Central</td>
    </tr>
    <tr>
      <th>1040</th>
      <td>4335952833</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Female</td>
      <td>$50,000 to $74,999</td>
      <td>New England</td>
    </tr>
    <tr>
      <th>1041</th>
      <td>4335951505</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Other (please specify)</td>
      <td>Cornbread</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>45 - 59</td>
      <td>Female</td>
      <td>$25,000 to $49,999</td>
      <td>West South Central</td>
    </tr>
    <tr>
      <th>1042</th>
      <td>4335951437</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>45 - 59</td>
      <td>Female</td>
      <td>$125,000 to $149,999</td>
      <td>Mountain</td>
    </tr>
    <tr>
      <th>1043</th>
      <td>4335951082</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>45 - 59</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>East North Central</td>
    </tr>
    <tr>
      <th>1044</th>
      <td>4335950917</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>60+</td>
      <td>Male</td>
      <td>$25,000 to $49,999</td>
      <td>West North Central</td>
    </tr>
    <tr>
      <th>1045</th>
      <td>4335950654</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>I don't know</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>30 - 44</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1046</th>
      <td>4335949486</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>Urban</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$10,000 to $24,999</td>
      <td>South Atlantic</td>
    </tr>
    <tr>
      <th>1047</th>
      <td>4335949169</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>30 - 44</td>
      <td>Female</td>
      <td>$25,000 to $49,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1048</th>
      <td>4335949112</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>60+</td>
      <td>Male</td>
      <td>$75,000 to $99,999</td>
      <td>West North Central</td>
    </tr>
    <tr>
      <th>1049</th>
      <td>4335947496</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1050</th>
      <td>4335945415</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>60+</td>
      <td>Male</td>
      <td>$125,000 to $149,999</td>
      <td>South Atlantic</td>
    </tr>
    <tr>
      <th>1051</th>
      <td>4335944854</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>60+</td>
      <td>Male</td>
      <td>$125,000 to $149,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1052</th>
      <td>4335944115</td>
      <td>No</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>18 - 29</td>
      <td>Male</td>
      <td>$0 to $9,999</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1053</th>
      <td>4335944082</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Roasted</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Rural</td>
      <td>30 - 44</td>
      <td>Female</td>
      <td>$100,000 to $124,999</td>
      <td>Mountain</td>
    </tr>
    <tr>
      <th>1054</th>
      <td>4335943173</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>No</td>
      <td>NaN</td>
      <td>Suburban</td>
      <td>60+</td>
      <td>Female</td>
      <td>$50,000 to $74,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1055</th>
      <td>4335943060</td>
      <td>Yes</td>
      <td>Other (please specify)</td>
      <td>Duck</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Rice-based</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>Urban</td>
      <td>60+</td>
      <td>Male</td>
      <td>$100,000 to $124,999</td>
      <td>Pacific</td>
    </tr>
    <tr>
      <th>1056</th>
      <td>4335934708</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>None</td>
      <td>NaN</td>
      <td>Homemade</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>No</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1057</th>
      <td>4335894916</td>
      <td>Yes</td>
      <td>Turkey</td>
      <td>NaN</td>
      <td>Baked</td>
      <td>NaN</td>
      <td>Bread-based</td>
      <td>NaN</td>
      <td>Canned</td>
      <td>NaN</td>
      <td>...</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>No</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1058 rows × 65 columns</p>
</div>




```python
#Get unique count - What is typically the main dish at your Thanksgiving dinner?
celebrate_thanksgiving['What is typically the main dish at your Thanksgiving dinner?'].value_counts()
```




    Turkey                    859
    Other (please specify)     35
    Ham/Pork                   29
    Tofurkey                   20
    Chicken                    12
    Roast beef                 11
    I don't know                5
    Turducken                   3
    Name: What is typically the main dish at your Thanksgiving dinner?, dtype: int64




```python
#Out of people who have Tofurkey how many also had gravy
Tofurkey=celebrate_thanksgiving.loc[celebrate_thanksgiving['What is typically the main dish at your Thanksgiving dinner?'] == "Tofurkey"]
Tofurkey['Do you typically have gravy?'].value_counts()
```




    Yes    12
    No      8
    Name: Do you typically have gravy?, dtype: int64



## How many people had pies, aggregate all the pie boolean columns to get True/False Value


```python
#Shorted Pie collumn names and assign to variable
Apple = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Apple'
Buttermilk = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Buttermilk'
Cherry = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Cherry'
Chocolate = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Chocolate'
Cocounut_cream = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Coconut cream'
Key_lime = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Key lime'
Peach = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Peach'
Pecan = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Pecan'
Pumpkin = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Pumpkin'
Sweet_potato = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Sweet Potato'
Other = 'Which type of pie is typically served at your Thanksgiving dinner? Please select all that apply. - Other (please specify)'

ate_pies = (pd.isnull(data[Apple])&
            pd.isnull(data[Buttermilk])&
            pd.isnull(data[Cherry])&
            pd.isnull(data[Chocolate])&
            pd.isnull(data[Cocounut_cream])&
            pd.isnull(data[Key_lime])&
            pd.isnull(data[Peach])&
            pd.isnull(data[Pecan])&
            pd.isnull(data[Pumpkin])&
            pd.isnull(data[Sweet_potato])&
            pd.isnull(data[Other])


)
    
#boelean count of how many ate pies
ate_pies.value_counts()

```




    False    926
    True     132
    dtype: int64



## Convert age column to numeric value to preform analysis on


```python
data['Age'].value_counts()

def extract_age(age_str):
    if pd.isnull(age_str):
        return None
    age_str = age_str.split(" ")[0]
    age_str = age_str.replace("+", "")
    return int(age_str)

#Use pandas series apply to abov method above to each row in the data column
data["int_age"] = data["Age"].apply(extract_age)
#Get descriptive statisitcs for the new int age column derived from above.
data["int_age"].describe()

```




    count    1025.000000
    mean       39.383415
    std        15.398493
    min        18.000000
    25%        30.000000
    50%        45.000000
    75%        60.000000
    max        60.000000
    Name: int_age, dtype: float64



### Findings
Even though we only took the first number, skewing our findings downwards, the numbers seem evenley distributed and the standard deviation seems relatively low.

## Convert income brackets to int values to preform analysis on


```python
income = "How much total combined money did all members of your HOUSEHOLD earn last year?"

def extract_income(income_str):
    if pd.isnull(income_str):
        return None
    income_str = income_str.split(" ")[0]
    if income_str == "Prefer":
        return None
    income_str = income_str.replace(",", "")
    income_str = income_str.replace("$", "")
    return int(income_str)

data["int_income"] = data[income].apply(extract_income)
data["int_income"].describe()
```




    count       889.000000
    mean      74077.615298
    std       59360.742902
    min           0.000000
    25%       25000.000000
    50%       50000.000000
    75%      100000.000000
    max      200000.000000
    Name: int_income, dtype: float64



### Findings
Standard deviation seems high, but seems distributed eventley. Downwards skew because taking lower number from range to calcuate.

## Travel habbits for thanksgiving during thanksgiving


```python
thanksgivng_travel = 'How far will you travel for Thanksgiving?'

data[data["int_income"] < 150000][thanksgivng_travel].value_counts()
```




    Thanksgiving is happening at my home--I won't travel at all                         281
    Thanksgiving is local--it will take place in the town I live in                     203
    Thanksgiving is out of town but not too far--it's a drive of a few hours or less    150
    Thanksgiving is out of town and far away--I have to drive several hours or fly       55
    Name: How far will you travel for Thanksgiving?, dtype: int64




```python
data[data['int_income'] > 150000 ][thanksgivng_travel].value_counts()
```




    Thanksgiving is happening at my home--I won't travel at all                         49
    Thanksgiving is local--it will take place in the town I live in                     25
    Thanksgiving is out of town but not too far--it's a drive of a few hours or less    16
    Thanksgiving is out of town and far away--I have to drive several hours or fly      12
    Name: How far will you travel for Thanksgiving?, dtype: int64



### Findings
It appears that more people with high income have Thanksgiving at home than people with low income. This may be because younger students, who don't have a high income, tend to go home, whereas parents, who have higher incomes, don't.

## Linking Friendship And Age

There are two columns which directly pertain to friendship, Have you ever tried to meet up with hometown friends on Thanksgiving night?, and Have you ever attended a "Friendsgiving?. In the US, a "Friendsgiving" is when instead of traveling home for the holiday, you celebrate it with friends who live in your area. Both questions seem skewed towards younger people. Let's see if this hypothesis holds up.


```python
data.pivot_table(
    index="Have you ever tried to meet up with hometown friends on Thanksgiving night?", 
    columns='Have you ever attended a "Friendsgiving?"',
    values="int_age"
)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Have you ever attended a "Friendsgiving?"</th>
      <th>No</th>
      <th>Yes</th>
    </tr>
    <tr>
      <th>Have you ever tried to meet up with hometown friends on Thanksgiving night?</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>No</th>
      <td>42.283702</td>
      <td>37.010526</td>
    </tr>
    <tr>
      <th>Yes</th>
      <td>41.475410</td>
      <td>33.976744</td>
    </tr>
  </tbody>
</table>
</div>



### Findings
Hypothesis seems to hold true here as the data suggests the average age for somone attending Frendsgiving and visting hometown friends during thanksgiving is the lowest

## Linking Friendship and Income
Younger people tend to be in the lower income bracket. If the above correlation between age and Freindsgiving is accurate, then the correlation between income and Friendsgiving should confirm the hypothesis.


```python
data.pivot_table(
    index="Have you ever tried to meet up with hometown friends on Thanksgiving night?", 
    columns='Have you ever attended a "Friendsgiving?"',
    values="int_income"
)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Have you ever attended a "Friendsgiving?"</th>
      <th>No</th>
      <th>Yes</th>
    </tr>
    <tr>
      <th>Have you ever tried to meet up with hometown friends on Thanksgiving night?</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>No</th>
      <td>78914.549654</td>
      <td>72894.736842</td>
    </tr>
    <tr>
      <th>Yes</th>
      <td>78750.000000</td>
      <td>66019.736842</td>
    </tr>
  </tbody>
</table>
</div>



### Findings
Hypothesis seems to hold true here, folks in the lower income bracket seem to visit friends on Thanksgiving versus the higher income bracket.
