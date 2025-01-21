---
description: Perform actions on multiple records at once.
---

# Bulk Operations

## Bulk Operations

Using bulk operations in Xano is largely the same between operation types. Each function expects an array of data or a custom query that it will use to apply the bulk operation, with the exception of Clear All Records.

For operations like Bulk Delete, use the custom query expression to determine which records to delete.

<div align="left"><figure><img src="../../../.gitbook/assets/image (6).png" alt="" width="294"><figcaption></figcaption></figure></div>

{% include "../../../.gitbook/includes/expression-builder.md" %}

For operations that expect an array, this array just needs to contain JSON objects with the ID of the record to target, and any associated data, such as each field to be edited in or added to the record.

<div align="left"><figure><img src="../../../.gitbook/assets/CleanShot 2025-01-09 at 16.30.09.png" alt="" width="291"><figcaption></figcaption></figure></div>

## Clear All Records

Clear All Records will delete every record in the table.
