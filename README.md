# ETL Pipeline for Place Name Standardization

This project implements an ETL pipeline to audit, clean, and standardize census locality data. It utilizes web scraping (via BeautifulSoup) and fuzzy string matching (via RapidFuzz) to resolve inconsistencies across district records in United Nations/UNICEF vaccination database.

## Pipeline Steps

	1.	Load Required Libraries
	•	Import Pandas for data handling and RapidFuzz for string matching.
	2.	Load Input Data
	•	Scrape reference locality names from a website to create a standardized list of valid names.
	•	Load raw locality data from an existing Excel file for processing.
	3.	Normalize Reference Lists
	•	Prepare standardized reference lists of valid locality names (regions and districts) by converting them to lowercase and stripping whitespace.
	4.	Preprocess Input Data
	•	Normalize the raw locality names in the Excel file for consistency by applying the same transformations as the reference lists.
	5.	Fuzzy Matching
	•	Use fuzzy string matching to map raw locality names to standardized reference lists:
	•	Admin1 Matching: Match region names using a defined similarity threshold.
	•	Admin2 Matching: Split and separately match parts of district names to improve accuracy for compound entries.
	6.	Handle Unmatched Records
	•	Flag unmatched records for manual review with comments such as “Unmatched Admin1” or “Unmatched Admin2.”
	7.	Count and Report Matching Success
	•	Compute and display the number of successfully matched records for Admin1 (regions) and Admin2 (districts).
	8.	Save Cleaned Data
	•	Output a CSV file containing the cleaned and corrected locality names, match scores, and unmatched records for review.
