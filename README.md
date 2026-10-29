# refugeeadmissions
Data on refugee admissions, sourced from the [Admissions & Arrivals page](https://www.rpc.state.gov/admissions-and-arrivals/) of the U.S. Refugee Admissions Program.

The [original data file](https://www.rpc.state.gov/documents/Refugee%20Admissions%20Report%20as%20of%20September%2030,%202026.xlsx) covers refugee admissions from FY2001 onwards, and is current as of 30 September 2026.[^1]

I wanted year-by-year data. To assemble the full data set, I made copies of the tabs for FY2024, FY2025, and FY2026, and removed all rows that did not refer to a specific country, and then exported each of the new tabs to a CSV file.

I then imported each of the CSV files as a table in a PostreSQL database, and combined them into a larger dataset.

Having verified that the exported files had the same table structure and could be combined as expected, I gave the data file to Claude with the instructions to create CSV files for the remaining years, using the three files I created myself as a model.

[^1]: The cumulative summary on the file's first tab includes regional data from 1975 onwards, but the country-specific data available in the file only goes back as far as FY2001.