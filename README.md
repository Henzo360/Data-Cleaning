# FIFA Player Dataset: Data Cleaning and Preparation

## Project overview
This project uses Python and pandas to clean and standardise a FIFA player dataset. The notebook examines the structure and quality of the data, handles inconsistent formats and missing values, converts fields into more useful data types, and checks the prepared dataset.

Data cleaning is an important step before analysis or modelling because inconsistent units, mixed numeric formats, duplicate records, and poorly handled missing values can lead to misleading results.

## Tools and libraries
- **Python** — data preparation
- **pandas** — tabular data manipulation and type conversion
- **NumPy** — numerical operations
- **Matplotlib** — visualisation
- **missingno** — visual exploration of missing-value patterns

## Data-quality issues addressed
The notebook works with several types of inconsistencies:
- Club names containing newline characters.
- Height values recorded in different formats, including centimetres and feet/inches.
- Weight values recorded in kilograms and pounds.
- Financial fields such as `Value`, `Wage`, and `Release Clause` containing currency symbols and suffixes such as K and M.
- Rating fields such as `W/F`, `SM`, and `IR` containing characters that need to be handled before analysis.
- The `Hits` field containing mixed formats, including values with a K suffix.
- Date information in the `Joined` field requiring datetime conversion.
- Missing values and possible duplicate records.

## Cleaning workflow
### 1. Inspect the source data
The notebook loads the dataset and inspects its dimensions, columns, data types, and missing-value patterns to understand the initial state of the data.

### 2. Review missing values and columns
Missing values are examined by column. The notebook removes columns considered unsuitable for the intended analysis and handles missing values in selected fields.

### 3. Standardise physical measurements
Height values are converted to a consistent centimetre representation, and weight values are converted to kilograms so records use comparable units.

### 4. Convert financial values
Currency-formatted values in `Value`, `Wage`, and `Release Clause` are cleaned by removing formatting characters and interpreting K/M suffixes as numeric multipliers.

### 5. Clean ratings and counts
The notebook removes or transforms non-numeric characters in rating fields and standardises the `Hits` field so the values can be represented numerically.

### 6. Standardise text and dates
Newline characters are removed from club names, contract information is split into separate fields, and the `Joined` field is converted to a datetime representation.

### 7. Validate the cleaned data
The notebook checks missing values and duplicate records after the cleaning operations. It reports that no missing values remain in the resulting dataset; this result depends on the source data and the cleaning decisions used in the notebook.

## Notable handling decisions
- Missing values in `Hits` are set to zero in the notebook. This assumes that a missing value can be interpreted as zero; the dataset's meaning and collection process should be considered before making that assumption.
- `Loan Date End` is dropped after the notebook notes that more than 94% of its values are missing. This is a specific decision made for this analysis.
- The notebook's final validation checks should be rerun whenever the source dataset or cleaning logic changes.

## Repository contents
- `Fifa Data Cleaning.ipynb` — Jupyter notebook containing the cleaning workflow and checks.
- `.gitignore` — Git ignore configuration.

## Running the project
1. Clone or download the repository.
2. Install the dependencies:

   ```bash
   pip install pandas numpy matplotlib missingno jupyter
   ```

3. Place the source FIFA dataset at the path used by the notebook, or edit the data-loading cell to match your local file location.
4. Open the notebook in Jupyter and run the cells in order.

The source dataset is not currently included in this repository, so it must be supplied locally to reproduce the workflow.

## Author
Henry Odionye
