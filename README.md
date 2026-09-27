# Netflix Catalogue: Exploratory Data Analysis

Exploratory analysis of Netflix's US catalogue of movies and shows: content type, age ratings, release years and IMDb scores,
joined with cast and crew credits.

## Data

"Netflix TV Shows and Movies" (Kaggle, 2022 snapshot of the US catalogue):
- `titles.csv`: 5,806 titles × 15 columns (type, release year, age certification, runtime, genres, IMDb/TMDB scores)
- `credits.csv`: 77,213 cast and crew credits

The two tables are joined on the title `id`.

## What the notebook covers

- Movies vs shows, and the distribution of age certifications (R, PG-13, TV-MA and so on)
- Release years from 1953 to 2022. Most credits belong to titles released in 2017–2021.
- IMDb score by release year
- Missing values in the joined table (for example, `character` is empty for 9,627 credits)

## Known limitations (and how to fix them)

The analysis runs on the **credits-joined** table, so every count is weighted by cast size. A film with 40 credited actors counts
40 times. As a result, "titles per year" and "score per year" really measure *credits* per year. The IMDb chart also plots the **sum**
of scores per year, which mostly tracks volume, not quality. The fixes: count `titles.id` directly (for example
`titles.groupby("release_year").id.nunique()`), and use the **mean or median** IMDb score per year.

## Run it

The notebook was written on Kaggle and reads from `/kaggle/input/netflix-tv-shows-and-movies/`. To run it locally, download the two CSVs
and update the paths in the first cells.

Tools: pandas, matplotlib, seaborn.

Notebook: [`data-analysis-on-netflix-data.ipynb`](data-analysis-on-netflix-data.ipynb)
