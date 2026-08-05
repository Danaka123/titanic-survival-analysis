# Titanic Survival Analysis

Python, Pandas, Seaborn, SciPy — classic dataset, used here as a training exercise in EDA and statistical testing

A from-scratch exploratory analysis of the Titanic passenger dataset: cleaning missing data, engineering a few features from the raw columns, and checking with actual statistical tests (not just eyeballing charts) which factors correlate with survival.

## What this covers

- Handled missing values with group-aware logic instead of blanket fills: `Embarked` filled with the mode, `Age` filled with the median for each passenger's own Pclass/Sex group (age varies a lot between a 1st class woman and a 3rd class man)
- Noticed a batch of passengers with Fare = 0 and traced it to a real explanation — checking the names showed they were crew, not a data error
- Engineered features from the raw columns: extracted a `Title` from each name, built `FamilySize` and `IsAlone` from `SibSp`/`Parch`, and turned "has a recorded cabin" into its own signal before dropping the mostly-empty `Cabin` column
- Ran a correlation heatmap and grouped survival breakdowns by class, sex, age bracket, and family size
- Backed the visual patterns with Welch's t-tests instead of assuming a chart difference is meaningful

## Key findings

- Sex and class dominate survival — women in 1st/2nd class survived at over 90%, men in 3rd class at just 13.5%
- Fare difference between survivors and non-survivors is statistically significant (t = 6.84, p < 0.001), but it's mostly a proxy for class
- Age is *not* a significant factor on its own (t = -1.74, p = 0.082) — despite children doing somewhat better
- Small families (2-4 people) had better odds than solo travelers or large families (5+)

## Stack

Python, Pandas, Seaborn, Matplotlib, SciPy
