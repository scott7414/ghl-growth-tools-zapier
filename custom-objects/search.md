# HighLevel Records Search API (Reference + Examples)

This page provides a structured overview of the [HighLevel Records Search API](https://doc.clickup.com/8631005/d/h/87cpx-277156/93bf0c2e23177b0/87cpx-379336), including filtering, sorting, pagination, and sample payloads for both Custom Objects and Business (Company) records.

> ℹ️ **Note:** This API currently supports only custom objects and business (company). More standard object support is planned.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Request Body Fields](#request-body-fields)
- [Filtering Syntax](#filtering-syntax)
- [Supported Operators](#supported-operators)
- [Sorting](#sorting)
- [Pagination](#pagination)
- [Sample Payloads](#sample-payloads)
  - [Custom Object Example](#custom-object-example)
  - [Business Object Example](#business-object-example)
- [Helpful Links](#helpful-links)

---

## Overview

The Records Search API enables advanced querying of custom object and business records. It supports:

- Filter groups with `AND` and `OR` logic
- Nested filters
- Search-after pagination
- Sort order
- Full-text queries

**Endpoint:**
```
POST /objects/${objectKey}/records/search
```

---

## Request Body Fields

| Field         | Type     | Required | Description |
|--------------|----------|----------|-------------|
| `locationId` | string   | ✅ Yes   | The Location ID in which the search is performed |
| `page`       | number   | ✅ Yes   | Page number of results |
| `pageLimit`  | number   | ✅ Yes   | Number of results per page |
| `query`      | string   | ❌ No    | Full-text query across indexed fields |
| `filters`    | array    | ❌ No    | Filter groups using `AND` / `OR` logic |
| `sort`       | array    | ❌ No    | Sort criteria by field and direction |
| `searchAfter`| array    | ❌ No    | Cursor for pagination `[timestamp, id]` |

---

## Filtering Syntax

Filters follow a flexible nested structure. Each filter object can include:

- `field`: the field or property to filter (e.g., `properties.name`)
- `operator`: comparison type (`eq`, `gt`, `lt`, etc.)
- `value`: the value to compare against
- `group`: logical grouping (`AND` or `OR`)
- `filters`: array of nested filters if grouped

> By default, multiple filters are grouped using `AND`.

---

## Supported Operators

Below is a list of supported operators you can use when building filters:

| Operator       | Description                     | Value Type                | Notes / Example Format                              |
|----------------|----------------------------------|----------------------------|-----------------------------------------------------|
| `eq`           | Equals                           | String, Number, Boolean    | `"operator": "eq", "value": "red"`                  |
| `not_eq`       | Not Equals                       | String, Number, Boolean    | `"operator": "not_eq", "value": true`               |
| `contains`     | Contains (no special characters) | String                     | `"operator": "contains", "value": "john"`           |
| `not_contains` | Not Contains                     | String                     | `"operator": "not_contains", "value": "admin"`      |
| `exists`       | Field exists (has any value)     | *None*                     | Only `"field"` and `"operator"` are required        |
| `not_exists`   | Field does not exist             | *None*                     | Only `"field"` and `"operator"` are required        |
| `range`        | Range between two values         | Object                     | See example below                                   |

### Example for `range` operator:

```json
{
  "field": "properties.price",
  "operator": "range",
  "value": {
    "gte": 5000,
    "lte": 15000
  }
}
```

---

## Sorting

Sort results using:

```json
"sort": [
  {
    "field": "updatedAt",
    "direction": "asc"
  }
]
```

---

## Pagination

Use the `searchAfter` array to paginate records. This is returned in every response as:
```json
"searchAfter": [timestamp, id]
```

To fetch the next page, send the same array in your next request.

---

## Sample Payloads

### Custom Object Example

```jsonc
{
  "locationId": "mbEVGywZGDnPkLKytm26",
  "page": 1,
  "pageLimit": 20,
  "query": "buddy",
  "filters": [
    {
      "group": "AND",
      "filters": [
        {
          "group": "OR",
          "filters": [
            {
              "group": "AND",
              "filters": [
                {
                  "field": "properties.name",
                  "operator": "eq",
                  "value": "jerry"
                }
              ]
            },
            {
              "group": "AND",
              "filters": [
                {
                  "field": "properties.color",
                  "operator": "eq",
                  "value": "red"
                }
              ]
            }
          ]
        }
      ]
    }
  ],
  "sort": [
    {
      "field": "updatedAt",
      "direction": "asc"
    }
  ]
}
```

---

### Business Object Example

```jsonc
{
  "locationId": "mbEVGywZGDnPkLKytm26",
  "page": 1,
  "pageLimit": 20,
  "filters": [
    {
      "group": "AND",
      "filters": [
        {
          "group": "OR",
          "filters": [
            {
              "group": "AND",
              "filters": [
                {
                  "field": "properties.name",
                  "operator": "eq",
                  "value": "Biomedics"
                }
              ]
            },
            {
              "group": "AND",
              "filters": [
                {
                  "field": "properties.phone",
                  "operator": "eq",
                  "value": "+919876543229"
                }
              ]
            }
          ]
        }
      ]
    }
  ],
  "sort": [
    {
      "field": "phone",
      "direction": "asc"
    }
  ]
}
```

---

## Helpful Links

- 🔗 [HighLevel API Filter Reference](https://doc.clickup.com/8631005/d/h/87cpx-277156/93bf0c2e23177b0/87cpx-379336)
- 🔗 [JSON Validator (jsonlint.com)](https://jsonlint.com/)
