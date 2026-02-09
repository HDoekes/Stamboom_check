# Pedigree Checker - Streamlit App

A comprehensive tool for analyzing and validating pedigree data with multiple quality checks.

## Features

1. **Missing Parents Check**: Identifies animals that appear as parents but aren't in the pedigree list
2. **Duplicate ID Check**: Finds duplicate entries in the ID column
3. **Offspring Count**: Lists top 20 sires and dams by number of offspring
4. **Dual-Role Check**: Identifies animals appearing as both sire and dam
5. **Birth Date Validation**: Finds animals born before their parents
6. **Circular Reference Detection**: Detects circular references (kringverwijzingen) in the pedigree structure

## Installation

1. Install the required packages:
```bash
pip install -r requirements.txt
```

## Running the App

Run the Streamlit app with:
```bash
streamlit run pedigree_checker.py
```

The app will open in your default web browser at `http://localhost:8501`

## Usage

1. Upload your pedigree CSV file
2. Map the columns to the required fields:
   - ID (animal identifier)
   - Vader (sire)
   - Moeder (dam)
   - Geboortedatum (date of birth)
3. Run individual checks by clicking the corresponding buttons
4. Download results for each check as needed

## File Format

Your CSV file should contain at least the following columns:
- Animal ID
- Sire ID (use '0' for unknown)
- Dam ID (use '0' for unknown)
- Date of birth (preferably in format: d-m-yyyy)

Example:
```
ID,Vader,Moeder,Geboortedatum,Geslacht,Kleur
141209548,0,0,1-1-1970,M,bruinbont
141209555,0,0,1-1-1967,V,palomino
15,0,0,1-1-1941,V,zwart
```

A sample file (`sample_pedigree.csv`) is included for testing.

## Output Files

- **Missing Parents**: CSV file with records to add to the pedigree
- **Duplicate IDs**: CSV file with all duplicate records
- **Top Sires/Dams**: Two CSV files with top 20 animals by offspring count
- **Dual-Role Animals**: Excel file with separate sheets for each animal
- **Birth Date Inconsistencies**: CSV file with problematic records
- **Circular References**: Text file listing all circular reference chains

## Notes

- Parent IDs marked as '0' are treated as unknown/missing parents
- Date parsing attempts multiple formats automatically
- Excel sheet names are limited to 31 characters
