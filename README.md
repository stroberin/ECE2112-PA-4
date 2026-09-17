# ECE2112-PA-4
Made by: Erin Madeline M. Sumeguin | 2ECEB

## Overview
At the end of this laboratory activity, the student should be able to:
1. filter tabular data using several categorical and numerical conditions;
2. construct focused DataFrames by selecting relevant features;
3. summarize the relationship between categorical features and a numerical variable; and
4. communicate a data comparison using clear and correctly labeled plots.

## Files

* `SUMEGUIN_PA4.ipynb`
* `boards2_csv`

Import pandas using:
```python
import pandas as pd
```

## Problems

### A. VISAYAS COMMUNICATION DATAFRAME

The `VisComm` DataFrame contains Communication students from Visayas and displays the required student information

``` python
VisComm = df[(df["Hometown"] == "Visayas") & (df["Track"] == "Communication")][["Name", "Gender", "Math", "Electronics", "Average"]]
VisComm
```

The number of rows was also required to be displayed, and thus this code was used:

``` python
display(VisComm)
print("Number of rows:", len(VisComm))
```

### B. VISAYAS FEMALE DATAFRAME

The `VisFemale` DataFrame contains female students from Visayas. A second filter only displays students with an Average of at least 60 without overwriting the original DataFrame.

``` python
VisFemale = df[(df["Hometown"] == "Visayas") & (df["Gender"] == "Female")][["Name", "Track", "GEAS", "Electronics", "Average"]]
display(VisFemale)

VisFemale_60 = VisFemale[VisFemale["Average"] >= 60]
display(VisFemale_60)
```

### C. CATEGORY-AVERAGE VISUALIZATION 
The mean Average is calculated for each Track, Gender, and Hometown. The results are displayed and compared using three bar charts

Import Matplotlib library using:
``` python
import matplotlib.pyplot as plt
```

a. Mean of Average of every category
``` python
track_avg = df.groupby('Track')['Average'].mean()
gender_avg = df.groupby('Gender')['Average'].mean()
hometown_avg = df.groupby('Hometown')['Average'].mean()
```

b. Three summary tables
``` python
print("Mean Average by Track:")
display(track_avg)

print("Mean Average by Gender:")
display(gender_avg)

print("Mean Average by Hometown:")
display(hometown_avg)
```

c. Three bar charts of Mean Averages
``` python
fig, axes = plt.subplots(1, 3, figsize=(15, 5))

track_avg.plot(kind='bar', ax=axes[0])
axes[0].set_title('Mean Average by Track')
axes[0].set_xlabel('Track')
axes[0].set_ylabel('Mean Average')
axes[0].tick_params(axis='x', rotation=45)

gender_avg.plot(kind='bar', ax=axes[1])
axes[1].set_title('Mean Average by Gender')
axes[1].set_xlabel('Gender')
axes[1].set_ylabel('Mean Average')
axes[1].tick_params(axis='x', rotation=0)

hometown_avg.plot(kind='bar', ax=axes[2])
axes[2].set_title('Mean Average by Hometown')
axes[2].set_xlabel('Hometown')
axes[2].set_ylabel('Mean Average')
axes[2].tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.show()
```

d. Category with highest sample of mean
``` python
highest_track = track_avg.idxmax()
highest_gender = gender_avg.idxmax()
highest_hometown = hometown_avg.idxmax()

print(f"{highest_track} has the highest sample mean Average among the Track categories.")
print(f"{highest_gender} has the highest sample mean Average among the Gender categories.")
print(f"{highest_hometown} has the highest sample mean Average among the Hometown categories.")
```

## Libraries Used:
* `pandas` - data filtering and analysis
* `matplotlib.pyplot` - data visualization
