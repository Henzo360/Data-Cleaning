# FIFA Player Dataset: Data Cleaning and Preparation

## Project overview

This project uses Python and pandas to clean and standardise selected fields in the FIFA 21 player dataset. The workflow focuses on data profiling, duplicate checks, missing-value assessment, unit conversion, currency parsing, contract-field parsing, date conversion, and exporting a cleaned dataset.

## Objectives

- Inspect the dataset structure, data types, missing values, and duplicate rows.
- Remove non-analytical profile fields where appropriate.
- Standardise player height to centimetres and weight to kilograms.
- Convert player value, wage, and release clause fields to numeric euro amounts.
- Parse contract details, ratings, website hits, and joining dates.
- Validate the cleaned dataset and export it for later analysis.

## Tools

- Python
- pandas
- NumPy
- Jupyter Notebook

See `requirements.txt` for the dependencies.

## Repository contents

- `Fifa Data Cleaning.ipynb` — the end-to-end cleaning workflow.
- `requirements.txt` — Python package dependencies.
- `fifa21 raw data v2.csv` — source dataset included at the repository root; the notebook also supports the conventional `data/fifa21_raw_data_v2.csv` path.
- `output/` — created by the notebook when the cleaned CSV is exported.
- 'fifa_cleaned.csv' - the cleaned file for preview sake

## Data preparation workflow

1. Load the source CSV and inspect its shape, columns, data types, missing values, and duplicates.
2. Drop selected profile URL columns and remove exact duplicate rows if any are present.
3. Measure missingness in `Loan Date End`; drop that column from the cleaned dataset because it is highly incomplete in the source data.
4. Trim club-name whitespace and split the original `Contract` field into `Contract_type` and `Contract_end`.
5. Convert height and weight to centimetres and kilograms.
6. Parse `Value`, `Wage`, and `Release Clause` into numeric euro amounts.
7. Convert `W/F`, `SM`, and `IR` to nullable numeric ratings; parse `Joined` as a datetime; and convert selected descriptive fields to categorical data.
8. Review remaining missing values and duplicates, then export the cleaned CSV.

## Important data-quality decisions

- **Missing Hits are not set to zero.** A missing value does not prove that a player's page received zero visits, so unknown values remain missing.
- **Missing values are reported, not automatically erased.** Some fields can legitimately be missing; assess them in context before analysis.
- **Contract end values preserve their source representation.** Standard contracts usually contain a year, while loan records can contain a full date.
- **Unparseable measurements or monetary values become missing.** This avoids silently introducing incorrect numeric values.

## How to run

1. Clone or download this repository.
2. Install the dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

3. Create a folder named `data` beside the notebook.
4. Place the source CSV in that folder and name it `fifa21_raw_data_v2.csv`.
5. Open `Fifa Data Cleaning.ipynb` in Jupyter and run the cells from top to bottom.

The expected input path is `data/fifa21_raw_data_v2.csv`. The cleaned file is written to `output/fifa_cleaned.csv`.

## Limitations

- The source dataset is not included in this repository, so users must obtain it separately and ensure they have the right to use it.
- The notebook reports missing values after cleaning rather than claiming that all missing values have been eliminated.
- The transformations standardise fields for analysis; they do not independently validate the real-world accuracy of FIFA player attributes.

## Author

Henry Odionye
