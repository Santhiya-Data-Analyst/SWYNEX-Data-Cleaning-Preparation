🎬 Netflix Titles - Data Cleaning

📁 About the Dataset
Netflix Movies and TV Shows dataset from Kaggle (by Shivam Bansal).
- Original file: netflix_titles.csv
- Original rows: 8,807
- Columns: 12 (show_id, type, title, director, cast, country, date_added, release_year, rating, duration, listed_in, description)

🛠️ Tools Used
Microsoft Excel (Power Query)

⚠️ What Was Wrong With the Data
- director, cast, and country columns had a large number of missing values
- date_added had a few blank rows and was stored as text, not a date
- rating had a few blank rows
- duration mixed two different things in one column - minutes for movies, seasons for TV shows
- country had multiple countries listed together in some rows, separated by commas
- type column had inconsistent capitalization (movie, Movie, MOVIE)
- Some duplicate show_id entries
- Extra spaces in several text columns

✅ Cleaning Steps
1. Filled missing values in director, cast, and country with "Unknown" instead of dropping those rows, since too much data would have been lost
2. Removed rows with blank date_added or rating (very few rows affected)
3. Converted date_added to a proper date format
4. Added two new columns from date_added: year_added and month_added
5. Split duration into two columns: duration_int (number) and duration_type (min or Season/Seasons)
6. Split country into primary_country, keeping only the first country listed and dropping the rest
7. Standardized the type column so values are consistently capitalized (Movie, TV Show)
8. Removed duplicate rows based on show_id
9. Trimmed extra leading/trailing spaces from all text columns

📊 Before and After
| | Before | After |
| |--------|-------|
| Rows | 8,807 | 8,807 |
| director missing | 30% | 0 (filled as Unknown) |
| cast missing | 9% | 0 (filled as Unknown) |
| country missing | 6% | 0 (filled as Unknown) |

💡 Assumptions Made
- Only the first listed country was kept for each title, since most titles had one primary country and the rest were minor co-production credits
- Missing director/cast/country values were labeled "Unknown" rather than removed, to preserve the rest of the row's data for analysis

📂 Files
- netflix_titles.csv - original raw data
- netflix_cleaned.xlsx - cleaned data, ready for analysis
