# Data Retention and Table Growth

SolarMeterCloud writes one new row per day into the Google Sheet.
Each daily export is appended to the end of the table.
No existing rows are modified or overwritten.

## Continuous Growth of the Table

Because every day adds a new row, the table will grow over time:

365 rows after one year

730 rows after two years

and so on

This behavior is intentional. It ensures that long‑term statistics and charts always have access to the full historical dataset.

## Manual Backup of the Data

Google Sheets does not automatically archive or rotate old data.
If you want to keep historical records, you must create backups manually.

Typical backup options:

Duplicate the sheet inside Google Sheets

Download the sheet as CSV or Excel

Copy the data into a separate archive document

Export the entire Google Drive folder

Backups can be created at any time without affecting the live data.

## Manual Deletion of Old Data

If the table becomes too large or you want to reduce storage:

Old rows can be deleted manually

Deleting rows does not affect the daily export

Node‑RED will continue appending new rows at the bottom

This allows you to keep the live sheet small while storing older data elsewhere.

## Automatic Chart Updates

The charts displayed on the SolarMeterCloud website update automatically.
They are based on the daily dataset sent from Node‑RED to Google Sheets.
Each day, a new row with a fresh timestamp is appended to the table, and the charts refresh accordingly.