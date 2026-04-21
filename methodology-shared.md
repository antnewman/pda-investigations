# Shared methodology for PDA Investigations

This document describes the principles common to every PDA Investigation. Each case has its own `methodology.md` that builds on this baseline with case-specific scoring. This document is policy-neutral: it describes how we work, not what we find.

## Purpose

To make reassessment of UK major-programme business cases fast, public, and reproducible. Each investigation asks a question that a public scrutiny body (the NAO, the Public Accounts Committee, the IPA, NISTA, or an equivalent) has formally put on the record, and scores the relevant assumptions against current public data using an open-source tool.

## What a case is

A PDA Investigation case:

- Takes a recommendation or question that a public body has already asked.
- Identifies the specific, numeric assumptions in the official business case that the recommendation targets.
- Scores those assumptions against current public external data.
- Publishes a narrative report with mandatory methodological caveats, alongside the data, the code, and the review record.

A PDA Investigation case is not:

- A freelance critique of a public body.
- A policy recommendation.
- A replacement for statutory assurance functions.

## Standards that bind every case

**Reproducibility.** Every claim is reproducible from public inputs. If an input is not public, it cannot be used in a published finding.

**Source citation.** Every assumption, every external signal value, and every drift calculation cites its source. Sources live in `data/sources.yaml` with a stable `citation_key`. Other files reference the key, not the value.

**Append-only data model.** Assumptions and external observations are never updated in place. If a value is revised, insert a new row with a new `baseline_date`; set the previous row's `is_superseded = true`. Historical state stays queryable.

**Temporal honesty.** Baseline dates are never fudged. If HMRC published a figure on 2 September 2025, that is its baseline date, regardless of when we ingest it.

**Caveats are mandatory.** Every published finding carries its methodological caveats in the same publication. No finding is published without stated limitations.

**Independent review before publication.** Findings go through an independent domain reviewer before publication. The review is recorded in the `reviews` table. Reviewer consent to be named is explicit per review. Sceptical or negative reviews are published alongside the finding, not hidden from it.

**Data integrity over narrative convenience.** Boring findings are published. Findings that contradict an expected framing are published with equal prominence. The framing can emphasise what is interesting; it cannot hide what is inconvenient.

## Shared data model

All cases share the `pda_shared` schema in Supabase project `pda-investigations` (ID `bulheatuxvktopxrwbvs`, eu-west-2 London, free tier):

- `pda_shared.source_documents`: primary source metadata, keyed by `citation_key`.
- `pda_shared.external_series`: external data series metadata.
- `pda_shared.external_observations`: append-only time-series observations.
- `pda_shared.reviewers`: reviewer metadata, service-role access only (identifying details are private by default; named attribution happens in the published methodology, not in the database).
- `pda_shared.reviews`: independent reviews of methodology, assumptions, calculations, or findings.

Each case has its own schema (for example `mtd_2026`) for case-specific tables: `assumptions`, `drift_calculations`, `findings`. The schema name is stable and case-named.

Row-level security is enabled on every table. Public reads are enabled on most tables. `pda_shared.reviewers` is service-role-only. `findings` are public only when `published = true`. Writes require the service role key, which is never committed to git.

## Review process

No finding is published without an independent review recorded in `pda_shared.reviews`. The target reviewer for each case has domain expertise appropriate to the case (for example, a tax-policy practitioner with ICAEW or CIOT credentialling for a tax case, a programme-assurance specialist for a delivery case). The review covers the methodology, the inputs, the scoring, and the framing.

The review is not pro forma. A sceptical or negative review is published alongside the finding. A missing review means the finding is not published.

## Tooling

All cases use the [PDA Platform](https://github.com/antnewman/pda-platform), an open-source Model Context Protocol platform for project and programme data. Analysis is deterministic given the inputs. Each run stamps the inputs, the platform version, and a checksum into the result row, so that any reader can reproduce the scored output from the same inputs.

## Licensing

Written content is released under CC BY 4.0. Code and structured data are released under MIT. Each case repository carries the same dual-licence structure.

## Citing

The programme as a whole has a citation record in `CITATION.cff` at the umbrella. Each case has its own. Each case is archived on Zenodo with its own DOI at the point of publication.

## Correspondence

Programme lead: Ant Newman CEng, TortoiseAI. ORCID [0000-0002-8612-3647](https://orcid.org/0000-0002-8612-3647).

Issues, corrections, and collaboration proposals are welcome as issues on the relevant case repository, or on this umbrella repository if they apply to the programme as a whole.
