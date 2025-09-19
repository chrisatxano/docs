# External Filtering Examples

## **Basic Equals Operation**

Checking if a user ID equals 1:

```json
{
  "expression": [{
    "statement": {
      "left": {
        "tag": "col",
        "operand": "users.id"
      },
      "op": "=",
      "right": {
        "operand": "1"
      }
    }
  }]
}
```

## **Between Operation**

Finding transactions with amount between 100 and 1000:

```json
{
  "expression": [{
    "statement": {
      "left": {
        "tag": "col",
        "operand": "transactions.amount"
      },
      "op": "between",
      "right": {
        "operand": ["100", "1000"]
      }
    }
  }]
}
```

## **Contains Operation**

Finding users with email containing '@company.com':

```json
{
  "expression": [{
    "statement": {
      "left": {
        "tag": "col",
        "operand": "users.email"
      },
      "op": "contains",
      "right": {
        "operand": "@company.com"
      }
    }
  }]
}
```

## **Multiple Conditions Example**

Finding active premium users who have made at least 5 purchases:

```json
{
  "expression": [
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.status"
        },
        "op": "=",
        "right": {
          "operand": "active"
        }
      }
    },
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.account_type"
        },
        "op": "=",
        "right": {
          "operand": "premium"
        }
      }
    },
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.purchase_count"
        },
        "op": ">=",
        "right": {
          "operand": "5"
        }
      }
    }
  ]
}
```

## **Case-Insensitive Pattern Matching (ilike)**

Finding products with names starting with 'phone', regardless of case:

```json
{
  "expression": [{
    "statement": {
      "left": {
        "tag": "col",
        "operand": "products.name"
      },
      "op": "ilike",
      "right": {
        "operand": "phone%"
      }
    }
  }]
}
```

## **Array Membership (in)**

Finding orders with specific status values:

```json
{
  "expression": [{
    "statement": {
      "left": {
        "tag": "col",
        "operand": "orders.status"
      },
      "op": "in",
      "right": {
        "operand": ["pending", "processing", "shipped"]
      }
    }
  }]
}
```

## **Complex Multiple Conditions**

Finding high-value transactions (>1000) made in the last 30 days by premium users:

```json
{
  "expression": [
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "transactions.amount"
        },
        "op": ">",
        "right": {
          "operand": "1000"
        }
      }
    },
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "transactions.date"
        },
        "op": ">=",
        "right": {
          "operand": "2024-12-29"
        }
      }
    },
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.account_type"
        },
        "op": "=",
        "right": {
          "operand": "premium"
        }
      }
    }
  ]
}
```

## Using And/Or

{% hint style="info" %}
By default, all statements will be considered an 'and' statement, and nothing needs to be specified. You'll only need to specify whether `or` is `true` when you want to use it.

For readability purposes, however, you can specify `or` is `false` if you'd like.

The two examples below demonstrate this and would return the same result.
{% endhint %}

```json
{
  "expression": [
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.id"
        },
        "op": "=",
        "right": {
          "operand": "1"
        }
      }
    }
  ]
}
```

```json
// Verbose specification of "or"

{
  "expression": [
    {
      "or": false,
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.id"
        },
        "op": "=",
        "right": {
          "operand": "1"
        }
      }
    }
  ]
}
```

### Two Conditions Combined with OR

This example filters for users whose status is 'inactive' OR whose account type is 'basic'.

```json
{
  "expression": [
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.status"
        },
        "op": "=",
        "right": {
          "operand": "inactive"
        }
      }
    },
    {
      "or": true,
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.account_type"
        },
        "op": "=",
        "right": {
          "operand": "basic"
        }
      }
    }
  ]
}
```

### Three Conditions with AND and OR

This example filters for active users AND (whose purchase count is less than 10 OR whose last login is before a specific date).

```json
{
  "expression": [
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.status"
        },
        "op": "=",
        "right": {
          "operand": "active"
        }
      }
    },
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.purchase_count"
        },
        "op": "<",
        "right": {
          "operand": "10"
        }
      }
    },
    {
      "or": true,
      "statement": {
        "left": {
          "tag": "col",
          "operand": "users.last_login"
        },
        "op": "<",
        "right": {
          "operand": "2024-01-01"
        }
      }
    }
  ]
}
```

### Using And/Or Groups - (Condition A AND Condition B) OR (Condition C AND Condition D)

Here's how the logic `(a = 1 AND b = 2) OR (a = 4 AND b = 5)` would be represented:

```json
{
    "expression": [
      {
        "or": false,
        "type": "group",
        "group": {
          "expression": [
            {
              "or": false,
              "statement": {
                "left": { "operand": "your_table.a" },
                "op": "=",
                "right": { "operand": "1" }
              },
              "type": "statement"
            },
            {
              "or": false,
              "statement": {
                "left": { "operand": "your_table.b" },
                "op": "=",
                "right": { "operand": "2" }
              },
              "type": "statement"
            }
          ]
        }
      },
      {
        "or": true,
        "type": "group",
        "group": {
          "expression": [
            {
              "or": false,
              "statement": {
                "left": { "operand": "your_table.a" },
                "op": "=",
                "right": { "operand": "4" }
              },
              "type": "statement"
            },
            {
              "or": false,
              "statement": {
                "left": { "operand": "your_table.b" },
                "op": "=",
                "right": { "operand": "5" }
              },
              "type": "statement"
            }
          ]
        }
      }
    ]
  }
```

## Using Joins <a href="#joins" id="joins"></a>

{% hint style="info" %}
Joins must first be defined inside of the Query All Records function.
{% endhint %}

In this example, we have a `user` table and a `books` table. Certain books belong to specific users, defined by a table reference field inside of the `books` table.

First, we define our join inside of the Query All Records function.

<figure><img src="../../../../.gitbook/assets/CleanShot 2025-09-19 at 12.15.18.png" alt=""><figcaption></figcaption></figure>

<details>

<summary>Quick Joins Explainer</summary>

#### What’s Going On

You have **two different tables**:

| Table     | What it Stores                                                                           |
| --------- | ---------------------------------------------------------------------------------------- |
| **books** | Each row is a book. It includes a `user_id` column to remember which user owns the book. |
| **user**  | Each row is a person, with their `id`, name, email, etc.                                 |

Right now these tables are separate.

* The _books_ table knows **which user number** owns the book,
* but it doesn’t know the user’s name or email.
* The _user_ table knows **all the user info**, but nothing about their books.

***

#### The Join in Plain Language

The **join** is a way to _link_ those two tables together on a shared piece of information.\
In this case, we tell Xano:

> “Match rows where `books.user_id` equals `user.id`.”

When Xano sees a book with `user_id = 17`, it looks in the user table for the row with `id = 17` and pulls those details in.

***

#### Why “Inner” Join Matters

An **inner join** says:

> “Only give me results when there’s a match in both tables.”

* If a book points to a user that doesn’t exist, that book won’t appear.
* If a user doesn’t own any books, that user won’t appear either.\
  This keeps the results _clean_—you only get rows where the relationship is valid.

</details>

Using external filtering for joins does not add much additional complication to writing your statements — the key is to ensure that you are specifying the table name inside of your statements.

**Example**: Find me all books owned by "test-user", who has a user ID of 20

```json
{
      "expression": [
        {
          "statement": {
            "left": {
              "tag": "col",
              "operand": "books.user_id"
            },
            "op": "=",
            "right": {
              "operand": "user.id"
            }
          }
        }
      ]
    }
```

**Example**: Find me all books that were created in 2024, that belong to a user with an ID of 20

```json
{
      "expression": [
        {
          "statement": {
            "left": { "tag": "col", "operand": "books.created_at" },
            "op": ">=",
            "right": { "operand": 1704067200000 }
          }
        },
        {
          "statement": {
            "left": { "tag": "col", "operand": "books.created_at" },
            "op": "<=",
            "right": { "operand": 1735689599000 }
          }
        },
        {
          "statement": {
            "left": { "tag": "col", "operand": "books.user_id" },
            "op": "=",
            "right": { "operand": 20 }
          }
        }
      ]
    }
```
