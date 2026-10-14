# FIFA Player Dataset: Data Cleaning and Preparation

## Project overview
A pandas-based data-cleaning project that prepares a FIFA player dataset for reliable analysis. The notebook focuses on inconsistent formats, missing values, and fields that need conversion to standard numeric, categorical, or datetime types.

## Data-quality problems addressed
- Inconsistent club names containing newline characters.
- Height recorded in centimetres and feet/inches.
- Weight recorded in kilograms and pounds.
- Financial fields (`Value`, `Wage`, and `Release Clause`) using currency symbols and K/M suffixes.
- Rating fields (`W/F`, `SM`, and `IR`) containing non-numeric characters.
- Mixed formats in the `Hits` field.
- Date conversion for the `Joined` field.
- Missing values, including a high proportion of missing values in `Loan Date End`.

## Tools
- Python
- pandas and NumPy
- Matplotlib
- missingno for visualising missingness

## Workflow
1. Loaded and inspected the dataset structure.
2. Reviewed missing values and duplicate rows.
3. Removed columns considered unsuitable for the intended analysis and handled missing values field by field.
4. Standardised height and weight into consistent units.
5. Converted financial values with K/M suffixes into numeric values.
6. Cleaned rating fields and converted suitable fields to categorical types.
7. Converted date fields and checked the resulting dataset for remaining missing values and duplicates.

## Important handling decisions
- The notebook sets missing `Hits` values to zero. This assumes a missing hit count means no recorded visits; confirm that interpretation against the dataset documentation before treating it as fact.
- The notebook drops `Loan Date End` after reporting that more than 94% of its values are missing. This is a project-specific choice, not a universal rule for handling missing data.
- The notebook reports no remaining missing values after cleaning. Re-run the checks to verify this whenever the source data or cleaning logic changes.

## Tools and setup
Install the main dependencies with:

```bash
pip install pandas numpy matplotlib missingno jupyter
```

Open `Fifa Data Cleaning.ipynb` and run the cells in order. The source FIFA dataset is not currently included in this repository, so place it at the path expected by the notebook or update the loading cell.

## Next improvements
- Add the source dataset link, licence, and a brief description of the dataset version.
- Include before/after counts for rows, columns, missing values, and duplicates.
- Add assertions or tests for unit conversion and currency parsing.
- Keep the raw data unchanged and write the cleaned output to a separate file.
- Explain why each dropped column is not needed for the intended analysis.
- Add a data dictionary for the cleaned columns.

## Author
Henry Odionye
