# EDGAR Filing Tree Index

Auto-generated index of every SEC EDGAR filer and their filings.
Rebuilt daily from [`submissions.zip`](https://www.sec.gov/Archives/edgar/daily-index/bulkdata/submissions.zip).

**Last rebuilt:** 2026-03-27 19:41 UTC

## Stats

| Metric | Count |
|---|---|
| Companies with filings | 959334 |
| Total filing entries | 26592593 |
| index.json size | 34.1 MB |

## Structure

```
index.json                     ← [[cik, "COMPANY_NAME"], ...]
manifests/
  000/
    1000.json                  ← per-CIK manifest
  001/
    1001.json
  ...
```

### index.json

Compact array of every CIK with at least one filing, paired with company name:
```json
[[21344,"COCA_COLA_CO"],[320193,"APPLE_INC"],...]
```

### Manifest files

Each `manifests/<cik % 1000>/<cik>.json` contains:
```json
{
  "cik": 1321655,
  "name": "Palantir_Technologies_Inc.",
  "columns": [
    "accessionNumber", "filingDate", "reportDate",
    "acceptanceDateTime", "act", "form", "fileNumber",
    "filmNumber", "items", "size", "isXBRL",
    "isInlineXBRL", "primaryDocument",
    "primaryDocDescription", "core_type"
  ],
  "filings": [
    ["0001321655-26-000011", "2026-02-17", "2025-12-31",
     "2026-02-17T11:14:19.000Z", "34", "10-K", "001-39540",
     "26635963", "", 11245671, 1, 1,
     "pltr-20251231.htm", "10-K", "XBRL"],
    ...
  ]
}
```

The `columns` array is the key for each position in a filing row.
All metadata from SEC EDGAR submissions is preserved: form type,
dates, accession numbers, XBRL flags, items, sizes, etc.

## Source

Data sourced from [SEC EDGAR](https://www.sec.gov/search-filings/edgar-application-programming-interfaces).
