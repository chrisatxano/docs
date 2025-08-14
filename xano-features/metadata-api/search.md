# Search

This section is broken down into Browse Content and Search. [Browse Content](search.md#browse-content) is a simple method of getting or reading the content of a database table. It can be optionally combined with paging.

[Search](search.md#search) is an advanced method of filtering, sorting, and paging database content. It is flexible and powerful and enables you to return content based on the parameters you define.

{% hint style="info" %}
Please note that the Metadata APIs for browsing content do not react to API Access settings. All fields will be returned regardless of this setting.
{% endhint %}

## Browse Content

Browse table content is a simple method of getting content (database records) in a database table.  It requires a workspace ID and table ID, while paging is optional.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-12 at 17.29.24.png" alt=""><figcaption></figcaption></figure>

Example response body:

```
{
  "items": [
    {
      "id": 1,
      "created_at": 1681336868222,
      "name": "Basketball",
      "description": "round ball to shoot hoops",
      "category_id": 1
    },
    {
      "id": 2,
      "created_at": 1681336868456,
      "name": "French Press",
      "description": "Make delicious coffee with this",
      "category_id": 2
    },
    {
      "id": 3,
      "created_at": 1681336868658,
      "name": "Bluetooth Speaker",
      "description": "Portable music player",
      "category_id": 3
    },
    {
      "id": 4,
      "created_at": 1681336868931,
      "name": "Camera",
      "description": "Take photos with this",
      "category_id": 3
    }
  ],
  "itemsReceived": 4,
  "curPage": 1,
  "nextPage": null,
  "prevPage": null,
  "offset": 0,
  "itemsTotal": 4,
  "pageTotal": 1
}
```

## Search

The `search` parameter in the Xano Metadata API allows you to filter query results using **structured search conditions**.\
\
It accepts an **array** of objects that describe logical expressions, comparisons, and groupings — similar to SQL `WHERE` clauses.

***

### Basic Structure

Each search item can be either:

* **Statement** → A single condition comparing two values.
* **Group** → A collection of statements combined with AND/OR logic.

**Statement Format:**

```json
{
  "type": "statement",
  "left": {
    "tag": "col",         
    "operand": "name"     
  },
  "op": "==",             
  "right": {
    "operand": "chris"    
  }
}
```

**Common `tag` values for operands:**

* `"col"` → Refers to a column in the table (e.g., `"name"`, `"user.id"`).
* `"const"` → A constant string.
* `"const:int"` → A constant integer.
* `"const:bool"` → A constant boolean.
* `"const:date"` → A date constant.

**Common `op` values:**

* `"="` or `"=="` → Equal to
* `"!="` → Not equal to
* `"<"`, `"<="`, `">"`, `">="` → Numeric/date comparisons
* `"like"` → Pattern match (SQL-like `%` wildcards supported)
* `"in", "not in"` → Value's existence in a provided list

***

### Logical Operators

You can combine statements using the `"or"` property:

* `false` (default) → Conditions are combined with AND.
* `true` → Condition is combined with OR.

Example:

```json
[
  {
    "type": "statement",
    "left": { "tag": "col", "operand": "name" },
    "op": "==",
    "right": { "operand": "chris" }
  },
  {
    "type": "statement",
    "or": true,
    "left": { "tag": "col", "operand": "id" },
    "op": "==",
    "right": { "operand": 2 }
  }
]
```

Meaning:\
`name == "chris" OR id == 2`

***

### Grouping Conditions

Groups allow nested expressions:

```json
{
  "type": "group",
  "group": {
    "expression": [
      {
        "type": "statement",
        "statement": {
          "left": { "operand": "user.name", "tag": "col" },
          "op": "=",
          "right": { "operand": "chris", "tag": "const" }
        }
      },
      {
        "type": "statement",
        "statement": {
          "left": { "operand": "user.id", "tag": "col" },
          "op": "=",
          "right": { "operand": "1", "tag": "const:int" }
        }
      }
    ]
  }
}
```

Meaning:\
`(user.name = "chris" AND user.id = 1)`

***

### Using Filters

Operands can have `filters` applied before comparison.\
Example with `concat` filter:

```json
{
  "operand": "true",
  "tag": "const:bool",
  "filters": [
    {
      "name": "concat",
      "disabled": false,
      "arg": [
        { "value": "or not true", "tag": "const" }
      ]
    }
  ]
}
```

Filters modify the operand value before it’s compared.

***

### Example: Complex Search

```json
[
  {
    "type": "statement",
    "left": { "tag": "col", "operand": "status" },
    "op": "in",
    "right": { "operand": ["active", "pending"], "tag": "const" }
  },
  {
    "type": "group",
    "or": true,
    "group": {
      "expression": [
        {
          "type": "statement",
          "statement": {
            "left": { "operand": "created_at", "tag": "col" },
            "op": ">=",
            "right": { "operand": "2025-01-01", "tag": "const:date" }
          }
        },
        {
          "type": "statement",
          "statement": {
            "left": { "operand": "priority", "tag": "col" },
            "op": "=",
            "right": { "operand": "high", "tag": "const" }
          }
        }
      ]
    }
  }
]
```

Meaning:\
`status IN ("active", "pending") AND (created_at >= 2025-01-01 OR priority = "high")`

***

### Tips

* Always send `"search"` as an array, even for a single condition.
* Use `"or": true` to connect conditions with OR logic.
* Use groups for nested AND/OR combinations.
* Match `tag` to the correct data type to avoid mismatches.
* Filters can preprocess values before comparison.

## Sort

Sort is flexible, like search, in the sense that it accepts a single object or an array for a single sort parameter. It also supports multiple sorts, which require an array format.

#### Single Sort

In this example, we will sort the category table by the name in ascending order.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-12 at 18.49.41@2x.png" alt=""><figcaption></figcaption></figure>

Example request body:

```
{

  "sort": {
    "name": "asc"
  }
}
```

Also acceptable:

```
{

  "sort": [{
    "name": "asc"
  }]
}
```

Example response body:

```
{
  "items": [
    {
      "id": 5,
      "created_at": 1681350452709,
      "name": "Decor",
      "rating": 3
    },
    {
      "id": 3,
      "created_at": 1681337773911,
      "name": "Electronics",
      "rating": 5
    },
    {
      "id": 2,
      "created_at": 1681337772998,
      "name": "Kitchen",
      "rating": 4
    },
    {
      "id": 4,
      "created_at": 1681350451208,
      "name": "Outdoor",
      "rating": 4
    },
    {
      "id": 1,
      "created_at": 1681337772458,
      "name": "Sports equipment",
      "rating": 4
    }
  ],
  "itemsReceived": 5,
  "curPage": 1,
  "nextPage": null,
  "prevPage": null,
  "offset": 0,
  "itemsTotal": 5,
  "pageTotal": 1
}
```

#### Multi-Sort

In this example, we will first sort the content by rating in descending order, then the name in ascending order.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-12 at 18.53.35@2x.png" alt=""><figcaption></figcaption></figure>

Example request body:

```
{

  "sort": [{
    "rating": "desc"
  },
  {
    "name": "asc"
  }
]
}
```

Example response body:

```
{
  "items": [
    {
      "id": 3,
      "created_at": 1681337773911,
      "name": "Electronics",
      "rating": 5
    },
    {
      "id": 2,
      "created_at": 1681337772998,
      "name": "Kitchen",
      "rating": 4
    },
    {
      "id": 4,
      "created_at": 1681350451208,
      "name": "Outdoor",
      "rating": 4
    },
    {
      "id": 1,
      "created_at": 1681337772458,
      "name": "Sports equipment",
      "rating": 4
    },
    {
      "id": 5,
      "created_at": 1681350452709,
      "name": "Decor",
      "rating": 3
    }
  ],
  "itemsReceived": 5,
  "curPage": 1,
  "nextPage": null,
  "prevPage": null,
  "offset": 0,
  "itemsTotal": 5,
  "pageTotal": 1
}
```
