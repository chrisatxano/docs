# Query All Records

## What is Query All Records?

Query All Records is used to retrieve records from a database table. You can set various filters and other options to determine exactly which records to retrieve.

## Function Options

Query All Records offers three panels for various settings: **filter**, **output**, and **external**.

{% tabs %}
{% tab title="Filter" %}
The Filter tab is used to determine what records will be returned from the database.

### By Custom Query

This is the section you'll use to determine what records to return. If you leave it blank, all records will be returned.

Click the ![](<../../../.gitbook/assets/CleanShot 2025-01-06 at 12.19.42.png>) icon to edit the custom query, and choose **Add A Conditional** from the panel that opens.

{% @arcade/embed flowId="nOHbeTAkqES5hLELWelD" url="https://app.arcade.software/share/nOHbeTAkqES5hLELWelD" %}

{% include "../../../.gitbook/includes/expression-builder.md" %}

### By Joins

Joins are an advanced concept that allows you to find matching records between tables. For example, let's say you have a table of **`orders`**, and each of those orders contain products of a specific color. We want to determine how many orders each customer made with products matching their favorite color.

You have two tables with the following data:

**`Customers`**: Names and their favorite color\
&#xNAN;**`Orders`**: Color and price of items sold

When you join these tables using the color as the connection point, you can see which customers bought items matching their favorite color.

There are different ways to combine these lists:

* Inner join: Only shows matches (like customers who bought their favorite color)
* Left join: Shows all customers, even if they haven't bought anything
* Right join: Shows all orders, even if no customer likes that color

So if Sarah likes blue and there's a blue sweater order, an inner join would connect them. But if Tom likes green and he hasn't placed any orders with green items, he'd only appear in a left join.

Joins are useful because they allow you to consolidate all of this into a single database operation, instead of querying multiple tables and manually matching the data in several additional steps.
{% endtab %}

{% tab title="Output" %}
The output tab contains all options related to the return, once the records have been queried. You can change options like determining what fields to show, the sort order, and more.

{% include "../../../.gitbook/includes/response-customization.md" %}

### Return Settings

Under Return Settings, you can adjust sorting and pagination settings.

{% include "../../../.gitbook/includes/query-return-types.md" %}

#### Sorting

Click ![](<../../../.gitbook/assets/CleanShot 2025-01-06 at 14.55.36.png>)to apply a sort to the returned records. You can apply multiple sorts for further customization.

#### Paging

Check ![](<../../../.gitbook/assets/CleanShot 2025-01-06 at 14.54.31.png>) to enable pagination for this query. You can specify which page to return, and how many records should be returned for each page.

Check ![](<../../../.gitbook/assets/CleanShot 2025-01-06 at 14.54.49.png>) if you want to include paging metadata, as shown below, in your return. You can also opt to include the total item count, which is the total number of records in the table.

```json
{
    "itemsReceived": 4,
    "curPage": 1,
    "nextPage": 2,
    "prevPage": null,
    "offset": 0,
    "perPage": 4...
```

#### Return As

Set the variable name that will contain the result

#### Lock

When used with a database transaction
{% endtab %}

{% tab title="External" %}
The external tab in a [Query all Records](broken-reference) Function enables external manipulation of your filtering, sorting, and paging. Once you link up the variable, you can pick and choose which options can be configured externally.

The features present in the External tab are essential for any of the following scenarios:

* You need to enable pagination of the results on your front-end
* You want your users to have more control over search parameters
* You want to otherwise define how the Query All Records function behaves with parameters coming in from your front-end.

<div align="left"><figure><img src="../../../.gitbook/assets/CleanShot 2025-01-07 at 08.46.03.png" alt="" width="298"><figcaption></figcaption></figure></div>

### External Query Options

You will notice that as you explore the various options for externally manipulating your query, there are two different modes, **simple** and **classic**.

You should be using **simple** mode especially if you are constructing a brand new query. Simple mode offers an ease of use advantage when compared to classic mode. We continue to make classic mode available to ensure that queries that were constructed prior to simple mode existing still continue to function.

#### External Sorting

External sorting allows you to define sorting parameters outside of the Query All Records function. For example, maybe your users can switch between ascending and descending sort, or they can sort by different or multiple fields.

To use external sorting, you need a JSON array that defines the sort in the following format. The object can either be constructed by your front-end and provided to Xano via a JSON input, or your front-end can just send the sort parameters and you can construct the array in the function stack with a Create Variable function.

You can copy the JSON below and paste it into the value of a Create Variable step, and then choose "Import JSON" on the pop-up that displays to let Xano construct this for you automatically.

```json
[
      {
            "orderBy": "",
            "sortBy": ""
      }
]
```

You can define multiple sorts by adding additional objects to the array.

**orderBy** will either be 'asc' or 'desc' for ascending or descending order

**sortBy** will contain the table name and the column name to sort by. As an example, if you have a table called "transactions" and you want to sort by the column "amount", your **sortBy** would be "_transactions.amount_"

#### External Filtering

External filtering enables you to define specific query conditions outside of what you have built into your function. For example, maybe you want to enable your users to filter by 'amount' or 'user' and want to ensure that you are prepared for any combination of search.

External filtering allows you to define specific query conditions via an input. To use external filtering, you need to construct a JSON array defining the conditions of the search in the following format. This format is the same as if you were to read a condition you built in Query All Records, from left to right.

```json
{
  "expression": [
    {
      "statement": {
        "left": {
          "tag": "col",
          "operand": ""
        },
        "op": "==",
        "right": {
          "operand": ""
        }
      }
    }
  ]
}

```

In this example, we are doing a simple search to check if a field contains a specific value. The left, op, and right values match exactly what we would see in the Query All Records expression builder.&#x20;

<figure><img src="../../../.gitbook/assets/CleanShot 2023-06-12 at 09.53.52.png" alt=""><figcaption></figcaption></figure>

If you want to define multiple search conditions, you can add additional objects to the "expression" array.

#### External Paging

External paging is essential if you are displaying results in pages on your front-end, as your front-end will typically send the information about what page to display back to Xano so your API knows which page to return.

Using Simple Mode for external paging, you can easily set variables or values for the following options as pertains to paging:

**Page**\
The current page of results

**Per Page**\
The amount of results per page

**Offset**\
Offset is available if you need to manually define an offset for the set of records returned.\
The following example, assuming your record IDs start at 1, will return records 1 - 10

> Page: 1\
> Per Page: 10\
> Offset: 0

The following example, assuming your record IDs start at 1, will return records 2 - 11

> Page: 1\
> Per Page: 10\
> Offset: 1

{% embed url="https://www.loom.com/share/3296855494f34b739a3f0305e8ec8dca" %}
Video Example of Using External Paging (Simple mode)
{% endembed %}

To define your external parameters using simple mode, just specify your desired values or variables in the External tab:

<div align="left"><figure><img src="../../../.gitbook/assets/CleanShot 2023-01-17 at 16.46.54@2x.png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endtab %}
{% endtabs %}



## Using Addons

Addons are a way for you to enrich a query's result with related data from other tables, such as getting product information and orders together. This is usually facilitated by using [table reference fields](../../../the-database/database-basics/field-types.md#table-reference).

{% @arcade/embed flowId="nfASxadnsB4PjVoo4L2s" url="https://app.arcade.software/share/nfASxadnsB4PjVoo4L2s" %}

{% stepper %}
{% step %}
### Click the ![](<../../../.gitbook/assets/CleanShot 2025-01-07 at 08.25.57.png>) button in the Output tab of your Query All Records function.

You'll see this attached to the base level of the response, table reference fields, and list fields. It's important to choose the correct Addon button based on the data you're trying to enhance.

In this example, we have an Order table that just contains product IDs, and we want to see actual product information instead.

<div align="left"><figure><img src="../../../.gitbook/assets/CleanShot 2025-01-07 at 08.26.38.png" alt="" width="440"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Click ![](<../../../.gitbook/assets/CleanShot 2025-01-07 at 08.28.28.png>) to create a new addon.

You can also select from already created addons from here.
{% endstep %}

{% step %}
### Select the table you want to add to the response.

For this example, we're adding product data to our orders, so we'll choose product.

<div align="left"><figure><img src="../../../.gitbook/assets/CleanShot 2025-01-07 at 08.34.23.png" alt="" width="335"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Choose how you want the data returned.

Similar to return types on a Query All Records step, you can adjust how the data is returned here.

{% include "../../../.gitbook/includes/query-return-types.md" %}

For this example, because we are only returning one product per product ID, we'll choose **single**.
{% endstep %}

{% step %}
### Select the field(s) from the table you are adding that match the data from the original query.

Our orders table contains product IDs in a field called `product_id`, so we'll choose that field. Xano will try and make the right choice for you automatically, so you may not have to make any changes here.

<div align="left"><figure><img src="../../../.gitbook/assets/CleanShot 2025-01-07 at 08.38.40.png" alt="" width="335"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Give your addon a name, and click ![](<../../../.gitbook/assets/CleanShot 2025-01-07 at 08.39.17.png>)

This name is just for you, so you can find the addon you're creating later.
{% endstep %}

{% step %}
### Give the data a name, which is the key it will reside in inside of the parent object.

Our parent object in this case is each product ID. The parent object is just whatever you are adding on to — think back to a few steps ago when we clicked the Addon button inside of product\_id.

We want each product to be nested under a key called product\_info, so that's what we'll put here.

<div align="left"><figure><img src="../../../.gitbook/assets/CleanShot 2025-01-07 at 08.40.34.png" alt=""><figcaption></figcaption></figure></div>

You can also click ![](<../../../.gitbook/assets/CleanShot 2025-01-07 at 08.42.21.png>) to change the response if you only want certain fields returned.
{% endstep %}
{% endstepper %}

