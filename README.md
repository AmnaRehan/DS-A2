# Cleaned datasets for Assignment 2 (23L-XXXX)

Version: **v1.0**  |  Date: **[date you publish]**
Course: [course name], FAST School of Computing, FAST-NU Lahore

These are the cleaned versions of two datasets used in Assignment 2 (EDA).
Assignment 3 loads them from this repository at tag v1.0.

## 1. Netflix (23L_XXXX_A2_netflix_cleaned.csv)

**Original source:** https://www.kaggle.com/datasets/shivamb/netflix-shows
(by Shivam Bansal). Licence: [copy the licence shown on the Kaggle page].
Credit belongs to the original author.

**Shape:** 8,807 rows x 22 columns (12 original + 10 derived).
**One row =** one title (Movie or TV Show) in the Netflix catalogue.

**What I changed**
- Stripped whitespace in text columns.
- 3 Movies had a duration ("74 min", "84 min", "66 min") stored in `rating`;
  moved to `duration`, rating set to Unknown.
- Missing director, cast, country and rating filled with "Unknown".
  The 10 missing `date_added` values were left missing.
- `date_added` converted to a date.
- Overlapping rating labels (NR, UR) grouped as "Unrated/Unknown" in `rating_group`.
- No rows removed. Outliers and 14 titles added before their release year were kept.

**Derived columns:** year_added, month_added, n_countries, n_genres, n_cast,
primary_country, movie_minutes, n_seasons, lag_years (year_added - release_year),
rating_group (Kids / Older kids / Teens / Adults / Unrated/Unknown).

## 2. Supermarket Sales (23L_XXXX_A2_supermarket_cleaned.csv)

**Original source:** instructor-provided file `supermarket_Sales.csv`
(FAST-NU Lahore course material).

**Shape:** 1,000 rows x 22 columns (17 original + 5 derived).
**One row =** one customer invoice at one of three branches.

**What I changed**
- No missing values, duplicates or inconsistent labels were found, so none were fixed.
- `Date` and `Time` converted to date and time types.
- No rows removed. 9 high `Total` outliers were kept (valid large baskets).
- Cost of goods sold, Tax 5%, Total and Gross income are exact functions of
  Unit price x Quantity, and Gross margin percentage is constant, so they
  are flagged as redundant. They were kept unchanged.

**Derived columns:** hour, time_of_day, weekday, month, is_weekend.

## Versioning
v1.0 is the version used in Assignment 2. Any later change to the cleaning
will be published as a new version (v1.1, v2.0, ...) and the old one left unchanged.
