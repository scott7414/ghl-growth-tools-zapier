# Search Custom Object Records by Related Contacts and Field Value

These examples demonstrate how to query a custom object for records related to specific contacts, with and without an additional property condition.

## Example 1: Get All Records Related to Two Specific Contacts

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

## Example 2: Filter by Contacts and Purchased Year

```json
{
  // This query returns only records related to the same contacts where the year field is 2022.
  // Useful for filtering purchase history, past ownership, or similar custom data.
  "filters": [
    {
      "field": "properties.year",
      "operator": "eq",
      "value": 2022
    },
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

## Notes

- The `recordId` field in the `relations` filter is used to target related records (like Contacts or Businesses).
- You can combine `relations` with any other supported filters (e.g. properties, tags, timestamps).
- Make sure the object you're querying supports associations.

For more information on supported operators and field types, refer to [the documentation](https://doc.clickup.com/8631005/d/h/87cpx-277156/93bf0c2e23177b0/87cpx-379336).

