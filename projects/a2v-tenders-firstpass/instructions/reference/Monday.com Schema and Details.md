# Monday.com Schema and Details

## Purpose

This document describes how A2V stores historical tender and project data inside Monday.com. The AI assistant uses this information to research previous tenders and extract insights that may help when analysing new inbound tenders.

The goal is to quickly surface relevant historical context such as previous pricing, suppliers, outcomes, and operational issues.

---

## Workspaces

Relevant workspaces include:

**Main Workspace**

**Order Tracker {year}**

Examples:

* Order Tracker 2026
* Order Tracker 2025

The Order Tracker workspace typically contains the boards used for active and historical deals.

---

## Primary Boards

The most important boards for tender research are:

**Tender Tracker**

**Deals {year}**

Examples:

* Tender Tracker
* Deals 2026
* Deals 2025

These boards contain historical information about tenders, projects, suppliers, and outcomes.

When researching previous tenders, these boards should be searched first.

---

## Board Items

Each **item** represents a project or tender.

Item names usually contain:

* Client name
* Project number
* Short product description

Example:

ALDI IB 3161 Heavy Duty Tape Dispenser

Because item names contain useful identifiers, **searching item names is usually the best first step when trying to find similar tenders.**

---

## Groups

Groups are used to represent the stage or outcome of a project.

Common groups include:

* Proposed
* Active Comms
* Won
* Lost
* Declined

Groups often provide a quick indication of whether the tender was successful.

For example:

**Won** indicates A2V secured the project.
**Lost** indicates the tender was unsuccessful.
**Declined** indicates A2V chose not to pursue the tender.

---

## Important Columns

The following columns contain important information for tender analysis.

### Customer

The client or retailer requesting the product.

Example:

ALDI IB

---

### Category

The broad product category.

Examples:

Craft
Stationery
Party
Pets

---

### Sub Category

A more specific product type.

Examples:

Tape Dispenser
Paint Brush
Craft Scissors

---

### Tender Status

Indicates the outcome of the tender.

Common values include:

Won
Lost
Tender
Declined

---

### Lost Feedback

Contains information about why the tender was lost.

Examples may include:

* Price too high
* Buyer stayed with incumbent supplier
* Sample quality issues
* Strategic decision by buyer

This information can be useful when assessing the likelihood of winning similar tenders.

---

### Tender Value

Estimated value of the tender or project.

This may indicate the commercial scale of the opportunity.

---

### Sample Requirement

Indicates whether a new product sample is required.

Examples:

Existing product sample
New design sample
Prototype required

This helps estimate development effort and timeline.

---

### On Sale / OSD Fields (optional; if present)

In your Monday schema, "On Sale" is often abbreviated as `OSD`.

Some boards may store these values in one or more columns (titles may be approximate):

- `Aprox OSD` (approximate On Sale / OSD date)
- `On Sale Year`
- `OSD Week`

If any of these columns exist in the retrieved board structure for an item, extract their stored values and include them in Historical Matches.
If none of these fields are present for a given item, state that On Sale/OSD fields were not found in Monday for that item.

---

## Supplier Information

Supplier and production information is often stored in **subitems**.

Subitems may contain fields such as:

* Production Facility
* Quote received
* Sample requested
* Supplier tender status

This allows the team to track which suppliers were involved in previous projects.

When analysing tenders, reviewing subitems can reveal which factories previously produced similar products.

---

## Searching for Historical Projects

When researching historical tenders, follow this order:

1. Search **item names** using product keywords.
2. Identify the most relevant candidate matches.
3. Inspect column values for useful information.
4. Inspect subitems for supplier or production details.
5. Extract relevant insights.

---

## Referencing Historical Data

When presenting findings from Monday.com:

* Include the **project name**
* Include a **link to the Monday item if available**
* Explain **why the project is relevant**

This helps users verify the source and review the full project history if needed.

---

## Notes

The Monday.com data structure may evolve over time. If new boards, columns, or fields appear, they should be added to this document to ensure the AI understands how to interpret them.
