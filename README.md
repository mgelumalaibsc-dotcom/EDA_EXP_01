~~~
ELUMALAI G
~~~
~~~
212225220030
~~~
**#Experiment 1: EDA in IPL Dataset**
~~~
**Aim:**
To perform Exploratory Data Analysis (EDA) on the IPL matches dataset and derive insights about matches per season, winning teams, toss decisions, and top venues.
~~~
**Algorithm:
~~~
Start the program.
Import the required libraries (pandas and numpy).
Load the matches.csv dataset.
Read the result column.
Check each value in the result column:
If the value is "runs", assign "Won by Runs".
If the value is "wickets", assign "Won by Wickets".
If the value is "tie", assign "Tie".
If the value is "no result", assign "No Result".
Otherwise, assign "Other".
Store the transformed values in a new column named win_type.
Display the result and win_type columns.
Stop the program.
~~~
Procedure:
~~~
Import the Pandas and NumPy libraries.
Load the IPL dataset (matches.csv) into a DataFrame.
Use conditional transformation (np.where) to convert the values in the result column into meaningful categories.
Create a new column named win_type to store the transformed values.
Display the first few rows of the result and win_type columns to verify the transformation.
End the program.
~~~

**1.Import Libraries**
  Import pandas for data handling.
  Import matplotlib and seaborn for visualization.
**2.Load Dataset**
  Use pd.read_csv() to load the IPL matches dataset.
  Check dataset shape using .shape.
  View first 5 rows using .head().
**3.Matches per Season (Univariate Analysis)**
  Group data by season and count matches.
  Plot a bar chart to visualize growth/decline in matches.
**4.Top Winning Teams (Univariate Analysis)**
  Use value_counts() on the winner column.
  Plot top 5 winning teams in a bar chart.
**5.Toss Decisions (Univariate Analysis)**
  Count toss decision preferences (bat vs field).
  Plot results using a bar chart.
**6.Top Venues (Univariate Analysis)**
  Count matches per venue.
  Display top 5 venues with a horizontal bar chart.
**7.Draw Insights**
  Observe patterns in toss decisions.
  Identify teams with consistent winning trends.
  
  **Program**
  ~~~
import pandas as pd
import matplotlib.pyplot as plt
df=pd.read_csv("matches.csv")
df
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
print(df.dtypes)
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
print("Is 'id' column unique? :", df['id'].is_unique)
print("Total Rows :", len(df))
print("Unique IDs :", df['id'].nunique())
duplicates = df[df['id'].duplicated()]
print("Duplicate IDs:")
print(duplicates)
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
print(df.isnull().sum())
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
duplicates = df[df.duplicated()]
print(duplicates)
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
df['city'] = df['city'].fillna('Unknown')
df = df.drop_duplicates()
print("Missing values in 'city' column:")
print(df['city'].isnull().sum())
print("\nNumber of duplicate records:")
print(df.duplicated().sum())
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
matches_per_season = df.groupby('season').size()
print(matches_per_season)
~~~
~~~
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("matches.csv")
matches_per_season = df.groupby('season').size()
print(matches_per_season)
max_season = matches_per_season.idxmax()
max_matches = matches_per_season.max()
print("\nSeason with the highest number of matches:")
print("Season:", max_season)
print("Matches:", max_matches)
plt.figure(figsize=(10,5))
matches_per_season.plot(kind='bar')
plt.title("Number of Matches Played in Each IPL Season")
plt.xlabel("Season")
plt.ylabel("Number of Matches")
plt.xticks(rotation=45)
plt.show()
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
team_wins = df.groupby("winner").size().sort_values(ascending=False)
print(team_wins)
~~~
~~~
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("matches.csv")
top5_teams = df.groupby("winner").size().sort_values(ascending=False).head(5)
print(top5_teams)
plt.figure(figsize=(8,5))
top5_teams.plot(kind="bar")
plt.title("Top 5 Teams with Most Match Wins")
plt.xlabel("Team")
plt.ylabel("Number of Wins")
plt.xticks(rotation=45)
plt.show()
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
csk_wins = df[df["winner"] == "Chennai Super Kings"]
print(csk_wins)
print("Total Wins:", csk_wins.shape[0])
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
toss_decision = df["toss_decision"].value_counts()
print(toss_decision)
~~~
~~~
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("matches.csv")
toss_pref = df["toss_decision"].value_counts()
most_preferred = toss_pref.idxmax()
count = toss_pref.max()
percentage = (count / len(df)) * 100
print("Most Preferred Toss Decision:", most_preferred)
print("Count:", count)
print("Percentage: {:.2f}%".format(percentage))
plt.figure(figsize=(6,4))
toss_pref.plot(kind="bar")
plt.title("Overall Toss Preference")
plt.xlabel("Toss Decision")
plt.ylabel("Frequency")
plt.xticks(rotation=0)
plt.show()
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
cross_tab = pd.crosstab(df["season"], df["toss_decision"])
print(cross_tab)
~~~
~~~
import pandas as pd
df = pd.readimport pandas as pd
df = pd.read_csv("matches.csv")
largest_margin = df["result_margin"].max()
match = df[df["result_margin"] == largest_margin]
print(match)_csv("matches.csv")
cross_tab = pd.crosstab(df["season"], df["toss_decision"])
print(cross_tab)
preferred = cross_tab.idxmax(axis=1)
print("\nPreferred Toss Decision in Each Season:")
print(preferred)
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
top5_venues = df.groupby("venue").size().sort_values(ascending=False).head(5)
print(top5_venues)
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
top10_matches = df.sort_values(by="result_margin", ascending=False).head(10)
print(top10_matches)
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
result_types = df["result"].value_counts()
print(result_types)
~~~
~~~
import pandas as pd

df = pd.read_csv("matches.csv")
df["date"] = pd.to_datetime(df["date"])
print(df["date"].dtype)
~~~
~~~
import pandas as pd
df = pd.read_csv("matches.csv")
df["date"] = pd.to_datetime(df["date"])
df["year"] = df["date"].dt.year
print(df[["date", "year"]])
~~~
~~~
import pandas as pd
import numpy as np

df = pd.read_csv("matches.csv")

df["win_type"] = np.where(df["result"] == "runs", "Won by Runs",
                  np.where(df["result"] == "wickets", "Won by Wickets",
                  np.where(df["result"] == "tie", "Tie",
                  np.where(df["result"] == "no result", "No Result", "Other"))))

print(df[["result", "win_type"]].head())
~~~
  **Output**
  <img width="1137" height="195" alt="image" src="https://github.com/user-attachments/assets/38984100-f61d-4cf0-9a87-7506eddf28c8" />
  <img width="860" height="691" alt="image" src="https://github.com/user-attachments/assets/680ca12a-908b-43c0-abdb-4c81c8343987" />
  <img width="837" height="432" alt="image" src="https://github.com/user-attachments/assets/e810ab48-9398-4890-8e0c-a5a354f67f36" />
  <img width="997" height="303" alt="image" src="https://github.com/user-attachments/assets/1eda3e77-3e66-4d35-b812-d969697c3d35" />
  <img width="1017" height="467" alt="image" src="https://github.com/user-attachments/assets/e8d6989d-e13b-4f2b-ac2c-efa3a0510c88" />
  <img width="1002" height="175" alt="image" src="https://github.com/user-attachments/assets/6bd766fc-b7ea-419c-92aa-2aab7704e2c1" />
  <img width="1002" height="250" alt="image" src="https://github.com/user-attachments/assets/5b47df4c-68a7-40b9-8846-48184d116abd" />
  <img width="1010" height="428" alt="image" src="https://github.com/user-attachments/assets/706f9493-da38-4b96-9e74-15a04f7d119a" />
  <img width="626" height="768" alt="image" src="https://github.com/user-attachments/assets/c2ca1858-0581-4ee9-9d90-5203de6e923e" />
  <img width="932" height="416" alt="image" src="https://github.com/user-attachments/assets/29c8f903-ffcb-4fb3-8731-e0e3a703a73d" />
  <img width="838" height="807" alt="image" src="https://github.com/user-attachments/assets/0eb7517a-7700-4b2a-bc01-8ca849e52469" />
  <img width="600" height="882" alt="image" src="https://github.com/user-attachments/assets/df6e7c27-b1f4-473d-be80-cbff99105c60" />
  <img width="1612" height="236" alt="image" src="https://github.com/user-attachments/assets/43031565-d156-4399-b35f-123128a4c726" />
  <img width="837" height="613" alt="image" src="https://github.com/user-attachments/assets/bac16885-9f74-46cc-99f1-ddf82d880900" />
  <img width="1013" height="413" alt="image" src="https://github.com/user-attachments/assets/05384737-ba97-4569-b0bb-ea519ccbf174" />
  <img width="935" height="802" alt="image" src="https://github.com/user-attachments/assets/940db44e-6374-4c71-9034-eec76de35c79" />
  <img width="1266" height="275" alt="image" src="https://github.com/user-attachments/assets/f1a4b912-cb74-44a1-bfda-d4b080bdc308" />
  <img width="1248" height="385" alt="image" src="https://github.com/user-attachments/assets/b960fddf-6e91-4bd6-a56a-9ccc329dceb3" />
  <img width="621" height="825" alt="image" src="https://github.com/user-attachments/assets/7fffd7eb-3419-446b-afb2-5b64167e815f" />
  <img width="1132" height="212" alt="image" src="https://github.com/user-attachments/assets/87f2b9d0-f8eb-46ba-b63b-a86f747975da" />
  <img width="1132" height="196" alt="image" src="https://github.com/user-attachments/assets/15de26d7-fcc7-4f1b-820e-3b2d6a8b0526" />
  <img width="1128" height="487" alt="image" src="https://github.com/user-attachments/assets/a831cde9-a880-4b99-8e7e-e2c919986ee1" />
  <img width="1117" height="372" alt="image" src="https://github.com/user-attachments/assets/8943dfac-ff68-4c17-aead-a220076e038d" />




















  




 ** Result**
  This experiment is executed successfully



Highlight the stadiums hosting maximum matches.
