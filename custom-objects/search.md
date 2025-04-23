# HighLevel Search Records Filters Reference for GHL Growth Tools Zapier App

This guide shows how to format the `filters` object for the **Filters** field in the [GHL Growth Tools Zapier app](https://www.ghlgrowthtools.com).  

> 🔗 _External links open in a new tab when clicked._

---

## 📌 How to Use

- Always wrap your filters inside `{ "filters": [ ... ] }`
- Do **not** include `locationId`, `page`, `pageLimit`, `sort`, `schemaKey`, `searchAfterTimestamp`, or `searchAfterId` — those are handled separately in the app.
- Validate your JSON using [jsonlint.com](https://jsonlint.com) before pasting it into Zapier.

---

## ✅ Example: Single Filter on a Custom Field of a Custom Object  
_This example searches for all records in the selected object where the custom text type field labeled `year` equals `2022`._

```json
{
  "filters": [
    {
      "field": "properties.year",
      "operator": "eq",
      "value": 2022
    }
  ]
}
```

---

## ✅ Example: Filter by Multiple Contact Records  
_This example returns all records in the selected object that are related to two specific contacts, based on their contact IDs._  
➡️ **Note:** When using the `relations` filter, only the `eq` (equals) operator is supported.

```json
{
  "filters": [
    {
      "field": "relations",
      "operator": "nested",
      "value": [
        {
          "field": "recordId",
          "operator": "eq",
          "value": [
            "vPt2TwsfFWWKcUIDM3RT",
            "riy5TaVTIY7rUX5q8mlg"
          ]
        }
      ]
    }
  ]
}
```

---

## ✅ Example: AND Group with Two Filters

```json
{
  "filters": [
    {
      "group": "AND",
      "filters": [
        {
          "field": "properties.make",
          "operator": "eq",
          "value": "Toyota"
        },
        {
          "field": "properties.year",
          "operator": "eq",
          "value": 2022
        }
      ]
    }
  ]
}
```

---

## ✅ Example: OR Group

```json
{
  "filters": [
    {
      "group": "OR",
      "filters": [
        {
          "field": "properties.type",
          "operator": "eq",
          "value": "trade-in"
        },
        {
          "field": "properties.type",
          "operator": "eq",
          "value": "new"
        }
      ]
    }
  ]
}
```

---

## ✅ Example: Range Filter

```json
{
  "filters": [
    {
      "field": "properties.price",
      "operator": "range",
      "value": {
        "gte": 5000,
        "lte": 15000
      }
    }
  ]
}
```

---

## ✅ Example: Field Exists

```json
{
  "filters": [
    {
      "field": "properties.trade_status",
      "operator": "exists"
    }
  ]
}
```

---

## ✅ Example: Field Does Not Exist

```json
{
  "filters": [
    {
      "field": "properties.description",
      "operator": "not_exists"
    }
  ]
}
```

---

## ✅ Example: Contains Text

```json
{
  "filters": [
    {
      "field": "properties.notes",
      "operator": "contains",
      "value": "pending"
    }
  ]
}
```

---

## 🧠 Supported Operators

| Operator        | Description                  | Value Type                |
|------------------|------------------------------|----------------------------|
| `eq`             | Equals                       | String, Number, Boolean    |
| `not_eq`         | Not Equals                   | String, Number, Boolean    |
| `contains`       | Contains (no special chars)  | String                     |
| `not_contains`   | Not Contains                 | String                     |
| `exists`         | Field has a value            | *None*                     |
| `not_exists`     | Field is missing or null     | *None*                     |
| `range`          | Value falls in a range       | Object `{ gte, lte }`      |

---

## 🔗 Related Resources

- [HighLevel API Filter Reference (ClickUp Doc)](https://doc.clickup.com/8631005/d/h/87cpx-277156/93bf0c2e23177b0/87cpx-379336)
- [Validate your JSON](https://jsonlint.com)

---

💡 **Tip**: If your filter doesn't seem to work, test your JSON at [jsonlint.com](https://jsonlint.com) and make sure you're using valid property names from your custom object or business schema.
