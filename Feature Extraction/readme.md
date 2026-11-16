# Anime Feature Extraction

A short pandas notebook that cleans a scraped anime dataset and pulls structured features (episode count, airing duration in months) out of messy text in the `Title` column. It then answers a few questions about the data: highest score, most episodes, and longest-running series.

## Contents

- `AnimeFeatureExtraction.ipynb`: the notebook
- `anime.csv`: the input dataset (not included in this repo; see [Data](#data))

## Requirements

- Python 3.x
- pandas
- numpy
- python-dateutil

Install with:

```bash
pip install pandas numpy python-dateutil
```

## Data

The notebook reads `anime.csv` from the working directory. The file has three columns:

| Column  | Description |
|---------|-------------|
| `Rank`  | Position in the list |
| `Title` | A single text field that mixes the title, format and episode count (e.g. `TV (64 eps)`), airing dates (e.g. `Apr 2009 - Jul 2010`), member count, and some extra page text |
| `Score` | Numeric score |

Because `Title` is scraped text, it contains more than the title itself. The notebook extracts the parts it needs using string parsing.

## What the notebook does

1. **Load the data.** Reads `anime.csv` into a DataFrame and previews it.
2. **Extract episodes.** A helper, `extract_episode`, takes the text between `(` and `)` in each title (e.g. `64 eps`). The result goes into a new `Episodes` column, and `" eps"` is stripped so the column can be converted to `int`.
3. **Extract airing period.** `extract_time` takes the 19 characters after the closing parenthesis to get the airing range (e.g. `Apr 2009 - Jul 2010`) into a `Total Time` column.
4. **Convert the period to months.** `calculate_total_months` parses the start and end dates with `datetime.strptime` and computes the number of months between them, inclusive of both endpoints. The result goes into a `Months` column. Rows that can't be parsed return `None`.
5. **Analysis:**
   - Show the anime with the highest score.
   - Show the top 5 anime by episode count (`nlargest`).
   - Show the anime with the longest airing period in months.

## Example findings

- **Highest score:** *Fullmetal Alchemist: Brotherhood* (9.10)
- **Most episodes:** *Gintama* with 201 episodes
- **Longest running:** *Ginga Eiyuu Densetsu* (OVA), 111 months (Jan 1988 to Mar 1997)

## How to run

1 Place `anime.csv` in the same folder as the notebook.
2. Open the notebook with Jupyter or VS Code.
3. Run all cells from top to bottom.
