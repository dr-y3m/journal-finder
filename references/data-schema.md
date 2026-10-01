# JSON input for build_shortlist.py

Write one JSON file per run. Every field except `name` is optional; leave unknown values out (or null) rather than guessing. The script applies the fit gate, so include every journal you scored, passing or not.

```json
{
  "manuscript": {
    "title": "Working title",
    "date": "2026-10-01",
    "input_mode": "full",
    "language_scope": "English and French",
    "constraints": "No OA mandate; exclude Journal X (rejected 2026)",
    "fingerprint": {
      "Research question": "...",
      "Core constructs": "...",
      "Theoretical lens": "...",
      "Method and design": "...",
      "Empirical context": "...",
      "Level of analysis": "...",
      "Contribution type": "...",
      "Community addressed": "...",
      "Keywords": "..."
    }
  },
  "weights": {"prestige": 0.40, "fit": 0.35, "speed": 0.15, "apc": 0.10},
  "journals": [
    {
      "name": "Journal title",
      "publisher": "Publisher",
      "issn": "0000-0000",
      "homepage": "https://...",
      "channels": ["A", "B", "D"],
      "fit": {"scope": 4, "conversation": 5, "method": 4, "context": 3, "contribution": 4},
      "fit_rationale": "One or two sentences, own words.",
      "method_stance": "Publishes PLS-SEM regularly; no editorial concerns found.",
      "desk_reject_risks": "Single-country sample; frame generalisability carefully.",
      "rankings": {
        "FNEGE":  {"value": "2",  "edition": "2025", "confidence": "O", "source": "https://...", "checked": "2026-10-01", "note": ""},
        "CNRS":   {"value": "Not listed", "edition": "5.07 (2020)", "confidence": "O", "source": "https://..."},
        "HCERES": {"value": "Listed (via FNEGE)", "edition": "derived", "confidence": "O"},
        "AJG":    {"value": "3", "edition": "2024", "confidence": "S", "source": "https://..."},
        "ABDC":   {"value": "A", "edition": "2025", "confidence": "S", "source": "https://..."},
        "SJR":    {"value": "Q1", "edition": "2025", "confidence": "O", "source": "https://...", "detail": "Business and International Management; SJR 1.21"},
        "WOS":    {"value": "not verified", "edition": "JCR 2026", "confidence": "S", "source": "https://...", "detail": "JIF 2025: 4.3 (SSCI)"}
      },
      "days_to_first_decision": 45,
      "acceptance_rate": "12% (2025)",
      "oa_model": "Hybrid; OA optional",
      "apc_mandatory": false,
      "apc_eur": 2900,
      "length_limit": "8,000–10,000 words",
      "recent_papers": [
        {"title": "Paper title", "year": 2024, "url": "https://doi.org/..."}
      ],
      "special_issue": {"title": "SI title", "deadline": "2027-01-31", "url": "https://..."},
      "red_flags": ""
    }
  ],
  "special_issues": [
    {"journal": "Journal title", "title": "SI title", "deadline": "2027-01-31", "url": "https://...", "note": "Fits the paper's digital angle"}
  ],
  "excluded": [
    {"name": "Journal title", "reason": "Scope limited to public-sector management", "channels": ["D"]}
  ]
}
```

## Field notes

- **rankings keys**: `FNEGE`, `CNRS`, `HCERES`, `AJG`, `ABDC`, `SJR`, `WOS`. Omit a key, or set confidence `U`, when nothing was verified; it then displays as "not verified".
- **value labels**: FNEGE and CNRS use `1*`, `1`, `2`, `3`, `4`; AJG `4*`, `4`, `3`, `2`, `1`; ABDC `A*`, `A`, `B`, `C`; SJR and WOS `Q1`–`Q4`. Use `Not listed` only with confidence `O`. HCERES takes free text.
- **edition**: write what the source actually shows. If it differs from the column's current edition (e.g., an AJG 2021 grade), the cell is still scored but the comment and the evidence sheet show the edition, and the note should say so.
- **apc_mandatory**: `true` for gold OA journals that charge every author, `false` for subscription or hybrid journals where OA is optional, and for diamond OA. Unknown → omit.
- **apc_eur**: approximate conversion to euros (state the original currency in `oa_model`).
- **days_to_first_decision**: a number of days, as reported by the journal; omit if unknown. The script maps it to a speed score.
- **fit** scores follow `fit-rubric.md`; the script averages the five.
