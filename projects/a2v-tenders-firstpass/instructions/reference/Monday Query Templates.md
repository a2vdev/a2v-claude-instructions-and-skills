# Monday Query Templates

## Purpose

This document provides standard query templates for retrieving data from Monday.com using the GraphQL API.

The AI should use these templates as the starting point when interacting with Monday.com.

Using consistent query structures improves reliability and ensures the AI retrieves the correct information.

---

## API Endpoint

All Monday.com API queries must be sent to:

```
https://api.monday.com/v2
```

Requests must be sent using **POST** and include a **GraphQL query** in the request body.

Example request structure:

```
POST https://api.monday.com/v2
Authorization: <API_TOKEN>
Content-Type: application/json

{
  "query": "GRAPHQL_QUERY_HERE"
}
```

---

## Best Practices

When querying Monday.com:

* Prefer **targeted queries** rather than retrieving entire boards unnecessarily.
* Retrieve **only the fields needed**.
* Start with **item names**, then retrieve additional details once relevant projects are found.
* Inspect **column values and subitems** when deeper project information is required.

---

## Query Template – List Boards

Use this query to identify available boards.

```
query {
  boards(limit: 50) {
    id
    name
  }
}
```

This is useful when discovering the board ID needed for further queries.

---

## Query Template – Get Board Structure

Use this query to inspect the structure of a board.

```
query {
  boards(ids: BOARD_ID) {
    id
    name
    columns {
      id
      title
      type
    }
    groups {
      id
      title
    }
  }
}
```

This returns:

* Column IDs and titles
* Group names
* Board metadata

Column IDs are often needed when filtering or interpreting results.

---

## Query Template – Retrieve Board Items

Use this query to retrieve items from a board.

```
query {
  boards(ids: BOARD_ID) {
    items_page(limit: 100) {
      items {
        id
        name
        group {
          title
        }
        column_values {
          id
          text
        }
      }
    }
  }
}
```

This query returns:

* Item name
* Item group
* Column values

This information is usually sufficient for analysing historical tenders.

---

## Pagination Rule — Always Exhaust Search Results

When searching board items by keyword using `searchTerm`, results are paginated.
The AI must follow these rules without exception:

1. **Always check `has_more`** in every response. If `has_more` is `true`, a
   `nextCursor` value will be present — use it to fetch the next page immediately.

2. **Keep paginating until `has_more` is `false`**. Do not stop after the first
   page and do not assume the first page contains all relevant results. A matching
   project may appear on any page.

3. **Always run a separate project-number search** in addition to keyword searches.
   Project numbers (e.g. "3177") may not surface on the same result page as
   name-based keyword results. Search the project number explicitly and treat it
   as a distinct search pass.

4. **Use multiple keyword variations** where terminology may differ. For example,
   when searching for gift wrap tenders, search "gift wrap", "valentine gift",
   and any other likely phrasing separately, paginating through each fully.

5. **Do not conclude a search is complete** until all of the following are done:
   - All keyword search pages exhausted (`has_more: false`)
   - A dedicated project-number search performed (if a number is known)
   - Results from all passes reviewed together before shortlisting matches

Failure to follow this rule risks missing directly relevant historical projects,
as demonstrated by ALDI USA 3177 Valentines Gift Wrap being missed on the first
search pass.

---

## Query Template – Retrieve Subitems

Some supplier and production information is stored in subitems.

Use this query when additional project detail is needed.

```
query {
  items(ids: ITEM_ID) {
    id
    name
    subitems {
      id
      name
      column_values {
        id
        text
      }
    }
  }
}
```

Subitems often contain:

* Production facility information
* Supplier quotes
* Sample status
* Supplier tender outcomes

---

## Query Template – Retrieve Updates

Updates sometimes contain useful notes about a project.

```
query {
  items(ids: ITEM_ID) {
    id
    name
    updates {
      id
      body
    }
  }
}
```

Updates may include:

* Internal discussion
* Production notes
* Supplier communication

---

## Typical Retrieval Workflow

When researching a historical project:

1. Identify the relevant board.
2. Retrieve items using `items_page`.
3. Identify candidate matches based on item name.
4. Inspect column values for useful information.
5. Retrieve subitems if supplier details are needed.
6. Retrieve updates if additional context is required.

This workflow ensures the AI retrieves relevant information efficiently.

---

## Fields Typically Used in Tender Analysis

When reviewing board items, the following information is usually important:

Item name
Group title
Customer
Category
Sub Category
Tender Status
Lost Feedback
Tender Value
Sample Requirement

These fields help determine whether a historical project is relevant to the current tender.

---

## Important Reminder

The AI should not retrieve entire boards unnecessarily.

Instead, it should:

1. Search for likely matches using product keywords.
2. Retrieve deeper information only for the most relevant projects.

This approach reduces unnecessary API usage and improves response performance.
