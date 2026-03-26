# Product Similarity Heuristics

## Purpose

When analysing tenders, the exact product name used in the tender documents may not match the product name used in historical projects.

For example, the same product type may be described using different terminology.

This document provides guidelines that help the AI recognise when two product descriptions refer to the same or similar product.

These heuristics help the AI identify relevant historical tenders even when the wording differs.

---

## Core Principle

Two projects may be considered similar if they refer to the same **functional product type**, even if the wording is different.

The AI should prioritise **functional similarity** rather than exact wording.

---

## Example Terminology Variations

Many products can be described using multiple names.

Example:

Tape dispenser
Tape gun
Packing tape holder
Heavy duty tape dispenser

These all refer to the same general product type.

If any of these terms appear in a tender, the AI should search for related variations.

---

## Product Category Matching

If an exact product match cannot be found, the AI should search for products within the same category.

Examples:

| Tender Product  | Related Category Matches |
| --------------- | ------------------------ |
| Tape dispenser  | Packaging tools          |
| Craft scissors  | Craft tools              |
| Paint brush set | Art supplies             |
| Glue gun        | Craft tools              |

Products within the same category can still provide useful historical insight.

---

## Packaging Format Matching

Products with the same packaging format may be relevant even if the product differs.

Examples include:

Blister pack
Window box
PDQ display
Counter display unit
Clip strip

Packaging requirements often affect production cost and logistics.

If a historical project used the same packaging format, it may provide useful insight.

---

## Retail Positioning Similarity

Products with similar retail price positioning may be relevant even if the product category differs.

Examples:

Low price point impulse items
Mid range craft kits
Seasonal promotional products

Retail price positioning often affects supplier selection and manufacturing feasibility.

---

## Client Matching

Projects for the same client are particularly valuable references.

Example:

ALDI IB tenders should prioritise other ALDI IB projects.

Even if the product differs, the same retailer may have:

* similar price expectations
* similar packaging requirements
* similar supplier preferences

---

## Supplier Matching

If the same supplier has previously produced a similar product, that project should be prioritised.

Supplier capability is often product specific.

Relevant insights include:

* whether the supplier successfully delivered the project
* whether issues occurred during production
* whether the supplier provided samples

---

## Similarity Ranking

When comparing potential historical matches, prioritise them in this order:

1. Same product type
2. Same client
3. Same supplier
4. Same product category
5. Similar retail price positioning
6. Similar packaging format

Projects matching multiple criteria are likely to be highly relevant.

---

## When No Strong Matches Exist

If no strong matches are found, the AI should:

1. Expand the search to similar product categories.
2. Identify projects with similar retail positioning.
3. Highlight the closest relevant examples.

Even partial matches can provide useful insight.

---

## Output Guidance

When presenting historical matches, the AI should explain why the project is relevant.

Example explanation:

"This project appears relevant because it involved a tape dispenser for ALDI IB, which is the same product category and client as the current tender."

Providing reasoning helps users understand the relevance of the match.

---

## Continuous Improvement

Product similarity rules may evolve over time.

If new product categories or naming conventions appear in tenders, they should be added to this document.

Improving these heuristics will increase the accuracy of historical tender matching.
