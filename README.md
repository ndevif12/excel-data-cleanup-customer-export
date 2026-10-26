
# Excel Data Cleanup: Customer Sales Export

Cleaned a messy 511-row customer sales export into a reliable, analysis-ready table, with a full exceptions log for items that need client input.

> All data in this repository is synthetic. No client or employer information is included.

## The problem

A business exports customer and invoice data from a legacy CRM plus manual entries. The file can't be used for reporting or system upload because it has:

- Mixed text formats: casing, extra and non-breaking spaces, inconsistent names
- Five different date formats, plus "N/A" and impossible future dates
- Amounts written as text (₹, Rs., INR, "k" shorthand, brackets for negatives)
- Phone numbers, emails and tax IDs in inconsistent or invalid formats
- Category values spelled many ways (city, department, status, payment terms)
- Duplicates (exact, near-duplicate, and same ID with a different customer)
- Structural junk: title rows, blank rows, repeated headers, a hardcoded total row

## The result

| | Before | After |
|---|---|---|
| Rows | 511 data rows + junk rows | **450 unique customer records** |
| Amounts | Mixed text formats | Numeric, correctly converted |
| Dates | 5 text formats | Real Excel dates (dd-mmm-yyyy) |
| Categories | Many variants per field | One standard value each |
| Unfixable items | Hidden in the data | **406 logged** in an Exceptions sheet, prioritised |

Nothing was guessed. Missing or invalid values were flagged for the client, not filled in.

## Exceptions log

| Field | Items |
|---|---|
| Email | 145 |
| Tax ID (PAN) | 94 |
| Amount | 50 |
| Rating | 36 |
| Invoice Date | 34 |
| Phone | 29 |
| Payment Terms | 18 |

Each item has a priority (High, Medium, Low), a suggested action, and columns for the client's decision and status.

## Approach

1. Profiled the raw data and listed every error pattern.
2. Built a repeatable **Power Query** workflow (no manual edits), so the same cleaning runs on the next export with **Data > Refresh All**.
3. Converted each date format explicitly rather than letting Excel guess, so no valid dates were blanked or swapped.
4. Kept every assumption in the README sheet, for example dash dates read month-first, "k" = thousand, brackets = negative.
5. Validated the output against the raw data, checking amounts, dates and phones row by row.

## Tools

Excel, Power Query (M), Excel formulas.

## Repository contents

```
/data
  Raw_Data.xlsx          Messy source file (synthetic)
/solution
  Cleaned_Data.xlsx      Cleaned table, Exceptions sheet, README sheet
/screenshots
  before.png             Raw data
  after.png              Cleaned data
  exceptions.png         Exceptions log
```

## Screenshots

![Before](<img width="1280" height="720" alt="before" src="https://github.com/user-attachments/assets/4da44844-592e-4676-aa4b-5a1403332e24" />
)
![After](<img width="1280" height="720" alt="after" src="https://github.com/user-attachments/assets/8fb18de5-202c-4606-bd6e-73ece2ceaed0" />
)

## Need something similar?

I clean and automate Excel data, build reconciliation tools, and set up reports that refresh in one click.

- Fiverr: [devi_n24]
- Contact: [ndevif12@gmail.com]
