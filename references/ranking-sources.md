# Ranking sources and live verification

For every journal × list, record: the value (exactly as the list prints it), the edition, a confidence code, the source URL and the date checked. These go into the `rankings` object of the JSON (see `data-schema.md`) and appear in the workbook's "Ranking evidence" sheet.

## Status of each list (written in autumn 2026; confirm at the start of each run)

| List | Current edition | Labels | Official access |
|---|---|---|---|
| FNEGE | 2025 (published December 2025; triennial; previous 2022) | 1*, 1, 2, 3, 4 | Public list on fnege.org |
| CNRS Section 37 | Latest found: version 5.07, June 2020 | 1*, 1, 2, 3, 4 | PDF hosted on several institutional sites |
| HCERES (économie-gestion) | Built by merging the FNEGE and CNRS lists | Listed / not listed | Derived; see below |
| CABS AJG | 2024; grades frozen until AJG 2027 | 4*, 4, 3, 2, 1 | Requires registration, so not fetchable |
| ABDC | 2025 (released early 2026; previous 2022) | A*, A, B, C | Public search tool and spreadsheet on abdc.edu.au |
| Scopus / SCImago | Updated yearly | Q1–Q4 per subject category | Public journal pages on scimagojr.com |
| Web of Science JCR | Updated each June | Q1–Q4, JIF | Subscription; publishers usually display the JIF |

At the start of each run, do one quick search per list to check whether a newer edition exists (e.g., "AJG 2027", "FNEGE 2028", "ABDC JQL review"). If one does, use it and say so in the report's verification notes.

## How to look up each list

### FNEGE
Search `classement FNEGE 2025 revues` and open the official document on fnege.org once, then look up every candidate in it (match on title and ISSN, since titles can be abbreviated or translated). If the official document can't be opened, accept a publisher or journal announcement that explicitly names the 2025 edition (confidence S).

Pitfall: many pages still show the 2022 categories, and the 2025 edition moved some journals, francophone ones included. Never carry a 2022 category into the 2025 column; if 2022 is all you find, record it with edition "2022" and note it.

### CNRS Section 37
Search `catégorisation des revues économie gestion section 37`. Confirm the version number on the cover page (5.07 dated June 2020 is the latest known when this file was written). Newer or applied journals are often absent; record "Not listed" only if you checked the full document. Because the list is old, a CNRS "Not listed" is displayed but not scored.

### HCERES
Search once per run for a current standalone HCERES list for économie-gestion (SHS1). If none is found, the HCERES column is derived: write "Listed (via FNEGE)" or "Listed (via CNRS)" when either list includes the journal, use the weaker of the two confidence codes, and add the note "derived". HCERES is displayed but not scored, to avoid counting the same evidence twice.

### CABS AJG
The official guide sits behind a free registration, so it can't be fetched. Use, in order of preference:
1. the publisher's or journal's own page stating "AJG 2024" or "ABS 2024";
2. a university library or business-school page reproducing AJG 2024 levels;
3. a targeted search: `"<journal title>" AJG 2024` or `"<journal title>" ABS rating 2024`.

These are all confidence S. If only an AJG 2021 grade is found, record it with edition "2021" and a note. AJG 2024 was an intermediate review (new journals plus journals whose metrics shifted significantly), so a 2021 grade is often still valid, but not always.

### ABDC
Try the official journal search or spreadsheet on abdc.edu.au first (confidence O). Otherwise use a publisher or journal page that names "ABDC 2025" (S). A rating labelled 2022 or 2019 is a different edition: record it with that edition and a note.

### Scopus (SCImago)
Search `<journal title> scimagojr` and open the journal's page on scimagojr.com (confidence O). Record the best quartile across subject categories as the value, and put the category name, the SJR value and the year in the detail field. If the page says the journal was discontinued in Scopus, treat that as a red flag (Phase 5).

### Web of Science (JCR)
JCR itself isn't public. Publisher homepages usually display "Impact Factor YYYY: x.x" (confidence S), more rarely the quartile. Record the quartile as the value when it is stated; otherwise set the value to "not verified" and put the JIF and its year in the detail field. Note the index (SSCI, SCIE, ESCI) when stated.

## Confidence rules

- **O**: the official document or database was consulted in this run.
- **S**: a secondary source names the list and the edition explicitly.
- **U**: anything else, including your own recollection. U values display as "not verified" and are left out of the prestige score.
- **"Not listed"** may only be recorded with confidence O, after checking the full official list. Otherwise use U.
- When sources disagree, prefer O; between S sources, prefer the most recent and the publisher's own page, and mention the disagreement in the note.
