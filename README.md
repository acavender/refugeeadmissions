# refugeeadmissions
Data on refugee admissions, sourced from the [Admissions & Arrivals page](https://www.rpc.state.gov/admissions-and-arrivals/) of the U.S. Refugee Admissions Program.

The [original data file](https://www.rpc.state.gov/documents/Refugee%20Admissions%20Report%20as%20of%20September%2030,%202026.xlsx) covers refugee admissions from FY2001 onwards, and is current as of 30 September 2026.[^1]

## The goal

A map, filterable by year, visualizing the countries of origin of refugees admitted to the United States from Fiscal Year 2001 through Fiscal Year 2026.

## Preparing the data

I wanted year-by-year data. To assemble the full data set, I made copies of the tabs for FY2024, FY2025, and FY2026, and removed all rows that did not refer to a specific country, and then exported each of the new tabs to a CSV file.

I then imported each of the CSV files as a table in a PostreSQL database, and combined them into a larger dataset as a test.

Having verified that the exported files had the same table structure and could be combined as expected, I gave the data file to Claude with the instructions to create CSV files for the remaining years, using the three files I created myself as a model. A transcript of the process is available: [refugee-data-session-transcript.md](refugee-data-session-transcript.md).

Once all the files were created, checked for accuracy, and imported to the database as tables, I combined them into single table.

## Building the map

Once I had the single table, I exported it to a CSV and connected that CSV to Tableau.

As I built the map in Tableau, I discovered that there are some decisions to make. Tableau turned up a number of unmatched locations. Most of them were easy to correct, since the difficulty was due to how the country's name was entered in the source file. But three pose challenges for Tableau: Tibet, the Union of Soviet Socialist Republics, and Yugoslavia.

I added a filter for the fiscal year (after first converting it to discrete), so users can quickly see which countries sent the most refugees.

Questions that can be answered in Tableau:

1. Which countries had the highest number of refugees admitted to the U.S. in any given year? In total for all years in the data set?
2. How many refugees in total were admitted each fiscal year? Over all fiscal years in the data set?

[^1]: The cumulative summary on the file's first tab includes regional data from 1975 onwards, but the country-specific data available in the file only goes back as far as FY2001.