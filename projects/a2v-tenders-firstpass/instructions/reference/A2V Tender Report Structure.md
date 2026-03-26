# A2V Tender Report Structure

## Purpose

This document defines the standard structure the AI should use when presenting findings after analysing a tender.

Using a consistent structure ensures the A2V team can quickly understand the relevant context and supporting evidence.

The report should be concise, factual, and easy to scan.

The AI must present evidence rather than recommendations.

---

## Report Structure Overview

Every tender analysis should be organised using the following sections:

1. Tender Summary
2. Key Tender Details
3. Historical Matches
4. Supplier Insights
5. Retail Benchmarks
6. Operational Notes
7. Actionable Context
8. Evidence References

Not all sections will always contain information. If a section has no relevant findings, the AI should state that clearly.

---

## Tender Summary

Provide a short interpretation of the tender.

This section should answer:

* What product is being requested
* Which client or retailer issued the tender
* The general product category
* Any notable requirements

Example summary:

"The tender appears to request a heavy duty tape dispenser product for the specified retail client. Any retail price positioning should only be stated if it is explicitly specified in the provided tender text."

The summary should be brief and neutral.

---

## Key Tender Details

This section should list important structured information extracted from the tender documents.

Typical fields include:

Product name
Product category
Retail price (if specified)
Estimated quantity
Region (UK, IB, EU)
Submission deadline
Sample requirement

If certain fields are not available, the AI should indicate that they were not specified.

Evidence markers:
- Any value extracted from the tender documents must be followed by a tender-document evidence marker like `[T1]` and defined in "Evidence References".

---

## Historical Matches

This section lists similar projects found in Monday.com.

Each historical match should include:

Project name
Monday item reference or link
On Sale/OSD fields (if available in Monday for this item)
Brief explanation of why the project is relevant

Evidence markers (required):
- When a value in a historical match (including any On Sale/OSD field values) comes from Monday.com, attach an inline reference marker like `[M1]` at the end of the clause/sentence that states the value.
- Add the detailed evidence for each `[M#]` in the "Evidence References" section at the end of the report.

Example format:

Project: ALDI IB 3161 Heavy Duty Tape Dispenser
Reason: Same product type and client.

Project: ALDI UK 2240 Tape Dispenser
Reason: Similar product category and packaging format.

Projects should be listed from most relevant to least relevant.

---

## Supplier Insights

This section summarises supplier or production facility information found in historical projects.

Examples of useful insights include:

* Which suppliers previously produced similar products
* Whether those projects were successful
* Whether samples were successfully produced
* Any production issues that occurred

Example insight:

"AJ Union previously produced a similar tape dispenser product for ALDI IB."

If supplier information is unavailable, the AI should note this.

Evidence markers:
- When summarising supplier/production outcomes from Monday.com, append `[M#]` markers to the sentences that contain those facts.

---

## Retail Benchmarks

This section summarises retail pricing information found in similar projects.

Examples include:

Retail price ranges for similar products
Pricing expectations for similar tenders

Evidence-only requirement:
- Only include retail price benchmarks when the underlying retail price (or the relevant Monday field you use as a retail benchmark) is explicitly present in Monday for the cited matches.
- If retail price/value evidence is not found in Monday for these matches, state "Retail benchmark not found in Monday for the cited matches" (and do not guess).

Evidence markers:
- Any benchmark value included in this section must be supported by `[M#]` markers.

---

## Operational Notes

This section highlights practical considerations discovered in historical projects.

Examples may include:

Packaging challenges
Supplier issues
Shipping or damage problems
Sample development constraints

Example:

"A previous production run experienced packaging damage during shipping."

Operational notes provide context about potential risks.

Evidence markers:
- When operational notes come from Monday.com fields/subitems, append `[M#]` markers.

---

## Actionable Context

This section summarises the most useful insights discovered during the analysis.

Examples include:

* Similar tenders previously won or lost
* Known supplier capabilities
* Retail pricing benchmarks
* Operational risks

The purpose of this section is to provide clear context that helps the team evaluate the opportunity.

The AI must remain neutral and factual.

Evidence markers:
- Any fact in this section that derives from Monday.com history must have `[M#]` markers.

---

## Important Rule

The AI must not recommend whether the company should pursue or decline the tender.

The AI’s role is to provide structured information and historical context.

All decisions remain with the A2V team.

---

## Evidence References

To keep the main UX clean, use short inline markers in the body and put the evidence details here.

Markers:
- Use `[M1]`, `[M2]`, ... for Monday.com evidence.
- Use `[T1]`, `[T2]`, ... for tender-document evidence (user-provided text/files).

Evidence list format (one entry per marker):
- `[M1]` Monday item: <project name> | Link: <Monday URL if available> | Field: <column/subitem title> | Value: <exact stored value text>
- `[T1]` Tender doc: <filename/section if available or "user-provided tender text"> | Field: <what you extracted> | Value: <exact extracted text>

If a date/value (including any On Sale/OSD fields) is not found for a given match, explicitly state that it was not found, and do not create a marker for a value that does not exist.
