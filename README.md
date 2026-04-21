# PDA Investigations

Public-data investigations of UK major programmes, conducted using the open-source [PDA Platform](https://github.com/antnewman/pda-platform) and published under CC BY 4.0 for written content and MIT for code and structured data.

**Programme lead:** Ant Newman, TortoiseAI. ORCID: [0000-0002-8612-3647](https://orcid.org/0000-0002-8612-3647).

---

## What this is

Each investigation is a self-contained case: a structured assumption register, external signal data, drift calculations, independently reviewed findings, and a narrative report. The case is built from public inputs only, using a tool that anyone can inspect, and published alongside the methodology and the data.

The methodology is intentionally conservative. We operationalise public recommendations (from the National Audit Office, the Public Accounts Committee, the Infrastructure and Projects Authority, NISTA, and equivalent bodies) against current public data, through an open-source tool. We do not freelance critique. We do not publish findings that cannot be reproduced from public inputs alone.

This repository is the umbrella. Each case has its own repository.

## Current cases

| Case | Repository | Status |
|---|---|---|
| MTD assumption drift at the point of £50k mandation | [`mtd-assumption-drift-2026`](https://github.com/antnewman/mtd-assumption-drift-2026) | In progress (April 2026) |
| Crossrail retrospective drift analysis | [`crossrail-retrospective-2026`](https://github.com/antnewman/crossrail-retrospective-2026) | In progress (April 2026) |

See [`cases/`](cases/) for the full index with short case summaries.

## What we publish

For every case:

- The assumption register, as structured data.
- The external series used, with stable source URLs.
- The drift calculations, with inputs, formula, and result.
- The findings, with mandatory methodological caveats.
- The review record: who reviewed it, what they said, and whether they consent to be named.

Findings that are boring are published. Findings that contradict an expected framing are published with equal prominence. The framing can emphasise what is interesting; it cannot hide what is inconvenient.

## What we do not do

- Replace HMRC's Standard Cost Model, OBR forecasting, NAO investigations, or internal assurance functions.
- Make policy recommendations. Policy is for Parliament.
- Publish findings without an independent review recorded in the `reviews` table.

## Tooling and data

All cases use the [PDA Platform](https://github.com/antnewman/pda-platform), an open-source Model Context Protocol platform for project and programme data. All cases store inputs and outputs in the shared Supabase project `pda-investigations` (eu-west-2 London region), with case-specific schemas and a shared `pda_shared` schema for sources, external series, and reviews.

## Shared methodology

Principles that apply across all cases are in [`methodology-shared.md`](methodology-shared.md). Each case's own `methodology.md` builds on this baseline with case-specific scoring.

## Repository layout

```
pda-investigations/
├── README.md               (this file)
├── AGENT_CONTEXT.md        (standing context for AI coding assistants)
├── CLAUDE.md               (Claude Code project instructions)
├── CITATION.cff            (citation metadata for the programme as a whole)
├── LICENSE                 (dual-licence notice)
├── LICENSES/               (full text of MIT and CC BY 4.0)
├── methodology-shared.md   (principles common to all cases)
├── cases/                  (index of individual case repositories)
└── .gitignore
```

## Citing

See [`CITATION.cff`](CITATION.cff) for umbrella-level citation metadata. Each case has its own `CITATION.cff` and its own Zenodo DOI.

## Licence

Written content is released under [CC BY 4.0](LICENSES/CC-BY-4.0.txt). Code and structured data are released under [MIT](LICENSES/MIT.txt). See [`LICENSE`](LICENSE) for the combined notice.
