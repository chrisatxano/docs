# Arrays

An array, or list, may contain a single item or many items. Arrays behave differently than other data types; you will typically iterate through them to transform data. These iterations can be performed with loops, or you can perform more wide-sweeping changes using [expressions](broken-reference).

We have several array functions that you can use to extract and manipulate the array quickly.

Before you dive in, let's review a key concept specific to arrays: index

The **index** is the number that corresponds to the item in the list, starting at 0. You won't see this reflected in your data, but it's how arrays keep track of their defined order of items.

## Add to End of Array

Adds an item to the end of an array

## Add to Beginning of Array

Adds an item to the beginning of an array

## Remove from End of Array

Removes the item at the end of the array

## Remove from Beginning of Array

Removes the item at the beginning of the array

## Merge

Merges two arrays together

## Find First Element

Uses the expression builder to find the first matched element of an array

## Find First Element Index

Uses the expression builder to find the index of the first matched element of an array

## Has Any Element

Returns a true or false based on if the array has any elements that meet the conditions outlined in the expression builder

## Has Every Element

Returns a true or false based on if the array has **all** elements that meet the conditions outlined in the expression builder

## Find All Elements

Uses the expression builder to find all matching elements in the array

## Get Element Count

Uses the expression builder to find the count of all matching elements in the array

## Array: Map

#### What it does

**Array: Map** transforms each element in a collection using a mapping rule and returns a new array of the transformed values. Use it for formatting, calculations, or reshaping array data.

#### Example — Format numbers as USD currency

**Before**

```json
[11124.12, 235632.12, 393938.52]
```

**After**

```json
["$11,124.12", "$235,632.12", "$393,938.52"]
```

**How it works:** For each number (`$this`):

1. `number_format($this, 2, ".", ",")` produces a string with two decimals, `.` as decimal separator, and `,` as the thousands separator.
2. `concat("$", …)` prefixes the dollar sign.

| UI Field                     | Example value                                    | Notes                                                        |
| ---------------------------- | ------------------------------------------------ | ------------------------------------------------------------ |
| **Collection**               | `json_decode('[11124.12,235632.12,393938.52]')`  | If you already have an array variable, reference it instead. |
| **Output type**              | `Array of Values`                                | We output strings such as `"$11,124.12"`.                    |
| **Mapping function → Value** | `concat("$", number_format($this, 2, ".", ","))` | `$this` is the current element.                              |
| **Result as**                | `x1`                                             | Variable name to store the mapped array.                     |

<figure><img src="../../../.gitbook/assets/CleanShot 2025-08-08 at 09.34.22@2x.png" alt=""><figcaption></figcaption></figure>

***

## Array: Partition

#### What it does

**Array: Partition** splits a list into two buckets based on a boolean expression you define. Items where the expression returns **true** go under the `true` key; the rest go under `false`.

#### Example — Separate an array that contains different data types, such as text and n

**Before**

```json
[1,2,"hello",3,4,"goodbye"]
```

**After**

```json
{
    "true": ["hello","goodbye"],
    "false":[1,2,3,4]
}
```

**How it works:** For each number (`$this`), evaluate `$this`.is a text string.&#x20;

| UI Field       | Example value           | Notes                                            |
| -------------- | ----------------------- | ------------------------------------------------ |
| **Array**      | `[1,2,3,4,5]`           | Your input list.                                 |
| **Expression** | `$this\|is_text=true`   | Any expression that returns boolean.             |
| **Result as**  | `variable_name`         | Stores an object with `true` and `false` arrays. |

<figure><img src="../../../.gitbook/assets/CleanShot 2025-08-08 at 09.32.55@2x.png" alt=""><figcaption></figcaption></figure>

***

## Array: Group By

#### What it does

**Array: Group By** organizes items into an object keyed by a value you compute from each item. Each key maps to an array of items that share that key.

#### Example — Group people by age

**Before**

```json
[
  {"name":"Alice","age":25},
  {"name":"Bob","age":30},
  {"name":"Eve","age":25}
]
```

**After**

```json
{
  "25": [
    {"name":"Alice","age":25},
    {"name":"Eve","age":25}
  ],
  "30": [
    {"name":"Bob","age":30}
  ]
}
```

**How it works:** For each person (`$this`), the grouping key is `$this.age`.

| UI Field                     | Example value                                                                 | Notes                                                               |
| ---------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Collection**               | `[{"name":"Alice","age":25},{"name":"Bob","age":30},{"name":"Eve","age":25}]` | Your array of objects.                                              |
| **Mapping function → Value** | `$this.age`                                                                   | Determines the group key for each item.                             |
| **Result as**                | `grouped_people`                                                              | Stores an object keyed by age; values are arrays of matching items. |

<figure><img src="../../../.gitbook/assets/CleanShot 2025-08-08 at 09.35.18@2x.png" alt=""><figcaption></figcaption></figure>

***

## Array: Difference

#### What it does

**Array: Difference** returns elements that are present in the **first** array but **not** in the **second**, comparing items by an optional mapping function.

#### Example — Students who didn’t submit homework

**Before**

* First array: `["Amy", "Bob", "Eve"]`
* Second array: `["Amy", "Eve"]`

**After**

```json
["Bob"]
```

**How it works:** Map each item to a comparable value (here, just the item itself via `$this`). Return only items from the first array whose mapped value does not appear in the second array.

| UI Field                     | Example value         | Notes                                                                   |
| ---------------------------- | --------------------- | ----------------------------------------------------------------------- |
| **Collections → First**      | `["Amy","Bob","Eve"]` | The “source” list.                                                      |
| **Collections → Second**     | `["Amy","Eve"]`       | Items to exclude.                                                       |
| **Mapping function → Value** | `$this`               | Compare on the item itself. For objects, use something like `$this.id`. |
| **Result as**                | `missing_students`    | Array of elements found only in the first array.                        |

<figure><img src="../../../.gitbook/assets/CleanShot 2025-08-08 at 09.36.34@2x.png" alt=""><figcaption></figcaption></figure>

***

## Array: Intersection

#### What it does

**Array: Intersection** returns elements that are present in **both** arrays, comparing by an optional mapping function.

#### Example — Customers who bought both products

**Before**

* Buyers of A: `["Alice","Bob","Eve"]`
* Buyers of B: `["Eve","Charlie","Bob"]`

**After**

```json
["Bob", "Eve"]
```

**How it works:** Map each item to a comparable value (here, the item itself with `$this`). Keep only values that appear in both arrays.

| UI Field                     | Example value             | Notes                                                    |
| ---------------------------- | ------------------------- | -------------------------------------------------------- |
| **Collections → First**      | `["Alice","Bob","Eve"]`   | First list.                                              |
| **Collections → Second**     | `["Eve","Charlie","Bob"]` | Second list.                                             |
| **Mapping function → Value** | `$this`                   | For objects, use a key like `$this.email` or `$this.id`. |
| **Result as**                | `shared_customers`        | Array of common elements.                                |

<figure><img src="../../../.gitbook/assets/CleanShot 2025-08-08 at 09.37.28@2x.png" alt=""><figcaption></figcaption></figure>

***

## Array: Union

#### What it does

**Array: Union** merges two arrays and returns an array of **unique** elements from both, comparing by an optional mapping function.

#### Example — Merge mailing lists without duplicates

**Before**

* List 1: `["Alice","Bob"]`
* List 2: `["Bob","Charlie"]`

**After**

```json
["Alice", "Bob", "Charlie"]
```

**How it works:** Combine both arrays, then deduplicate based on the mapped value (here using `$this` to compare raw values).

| UI Field                     | Example value         | Notes                                          |
| ---------------------------- | --------------------- | ---------------------------------------------- |
| **Collections → First**      | `["Alice","Bob"]`     | First list.                                    |
| **Collections → Second**     | `["Bob","Charlie"]`   | Second list.                                   |
| **Mapping function → Value** | `$this`               | For objects, use a stable key like `$this.id`. |
| **Result as**                | `all_unique_contacts` | Array of unique values from both inputs.       |

<figure><img src="../../../.gitbook/assets/CleanShot 2025-08-08 at 09.38.14@2x.png" alt=""><figcaption></figcaption></figure>

## Using the Expression Builder

{% include "../../../.gitbook/includes/expression-builder.md" %}





















