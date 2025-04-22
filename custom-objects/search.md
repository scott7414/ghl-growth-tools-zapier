# HighLevel Filters Reference for Zapier App

This guide shows how to format filters for the **Filters** field in your custom Zapier app.  
The app automatically handles `locationId`, `pageLimit`, `page`, `query`, and `sort`, so you only need to provide the **filter object** (starting with `{` and ending with `}`).

---

## 📌 How to Use

- Only pass the contents of the `filters` array.
- You can pass **a single filter object**, or **wrap multiple filters in an array or group**.
- Do **not** include `locationId`, `page`, or any other outer fields.

---

## ✅ Example: Single Filter

```json
{
  "field": "properties.year",
  "operator": "eq",
  "value": 2022
}
```

---

## ✅ Example: Filter by Multiple Related Records

```json
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
```

---

## ✅ Example: AND Group with Two Filters

```json
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
```

---

## ✅ Example: OR Group

```json
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
```

---

## ✅ Example: Range Filter

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

## ✅ Example: Field Exists

```json
{
  "field": "properties.trade_status",
  "operator": "exists"
}
```

---

## ✅ Example: Field Does Not Exist

```json
{
  "field": "properties.description",
  "operator": "not_exists"
}
```

---

## ✅ Example: Contains Text

```json
{
  "field": "properties.notes",
  "operator": "contains",
  "value": "pending"
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
- [Validate your JSON](https://jsonlint.com/)

---

💡 **Tip**: If your filter doesn't seem to work, test your JSON first in [jsonlint.com](https://jsonlint.com/) and double-check the `field` names from the object schema in HighLevel.

