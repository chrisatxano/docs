# Using the Xano Database

## :man\_factory\_worker: Create a Database Table

{% @arcade/embed flowId="lYQQDmkQE0whqrIzhV98" url="https://app.arcade.software/share/lYQQDmkQE0whqrIzhV98" fullWidth="false" %}

{% stepper %}
{% step %}
### Head to the database

Click ![](<../../.gitbook/assets/CleanShot 2024-12-14 at 12.19.51.png>)in the left hand menu.
{% endstep %}

{% step %}
### Add a new table

Click ![](<../../.gitbook/assets/CleanShot 2024-12-14 at 12.20.52.png>)in the top right corner.

Choose **Import Data** to [import data from a CSV file](../migrating-your-data/csv-import-and-export.md), or **Enter Data Manually** to start with an empty table.

In the panel that opens, give your table a name[^1] and a descript[^2]
{% endstep %}

{% step %}
### Give your table a name and a description.

&#x20;When naming your table, it's considered best practice to use camelCase for multiple words, and to not use plurals in the table name. For example, a table of dog breeds would be named `dogBreed`

The description is just for you to make notes on what this table will contain, notable data constraints, or any other information you'd like to store.
{% endstep %}

{% step %}
### Choose your primary key type.

The primary key is the ID of each record. Xano offers two types of primary keys to choose from.

<details>

<summary>Sequential (1, 2, 3...)</summary>

A sequential identifier is just a sequence of whole numbers (1, 2, 3, etc...).

Think of sequential IDs like numbered tickets at a deli counter. They start at 1 and count up one by one (2, 3, 4...). Just like how the first customer gets ticket #1, the first row in your database gets ID #1. This system is straightforward but requires coordination - just as you can't have two deli counters giving out the same numbers (it would confuse customers), you need to ensure you're not creating duplicate IDs across different parts of your system.

</details>

<details>

<summary>UUID</summary>

A UUID is like the serial number on your electronics - something like "550e8400-e29b-41d4-a716-446655440000". It's longer and looks random, similar to how no two iPhone serial numbers are alike, even if they were made in different factories. This makes UUIDs particularly useful when you have data coming from multiple sources or need to merge databases - you don't have to worry about ID conflicts, just like how Apple doesn't need to check with Samsung about what serial numbers they're using.

Some users feel that using UUIDs is also more secure. UUIDs do provide some security benefits through obscurity - you can't easily guess other valid IDs by simply incrementing a number. If a website shows you order #1234, you might guess that order #1235 exists. But if you see order 550e8400-e29b-41d4-a716-446655440000, you can't easily guess other valid orders.

However, it's crucial to understand that using UUIDs is not a replacement for proper security measures. You should never rely on the difficulty of guessing IDs as your only security mechanism. Proper authentication and authorization should be in place regardless of ID type.

</details>
{% endstep %}

{% step %}
### Add some tags.

Tags in Xano can be applied to any object (tables, APIs, functions, etc...) and are used to easily find related objects when searching your workspace.
{% endstep %}

{% step %}
### Choose to add basic CRUD endpoints.

Xano can provide you with some standard pre-built APIs for basic operations against this table. If you choose this option, you'll also want to supply an **API Group** for those endpoints to live in. You can always choose to generate these endpoints later, too.
{% endstep %}

{% step %}
### Confirm your choices.

Once you've confirmed all of your settings are as you want them to be, click **Add Table**.
{% endstep %}
{% endstepper %}

***

## :information\_source: Navigating the Table View

Let's start with the top control bar.

<figure><img src="../../.gitbook/assets/CleanShot 2024-12-14 at 22.02.58.png" alt=""><figcaption></figcaption></figure>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f9ed">🧭</span> Navigation Controls</summary>

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.03.27 (1).png>)Table name, ID, description, and tags

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.05.07.png>) Go back to your list of database tables.

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.04.35 (1).png>) Refresh the list of records

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.06.50.png>) Change the [database view](#user-content-fn-3)[^3]

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f50e">🔎</span> Searching, Filtering, and Sorting</summary>

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.09.18.png>) Search for specific records

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.09.43.png>) Filter your records by certain conditions, such as "all records with an ID greater than 100"

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.10.38 (1).png>) Sort your database records

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.11.07.png>) Hide database fields from view

</details>

<details>

<summary><span data-gb-custom-inline data-tag="emoji" data-code="1f9f0">🧰</span> Tools and Advanced Controls</summary>

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.14.59.png>) Cut, Copy, Paste, Undo, and Redo

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.15.31.png>) Show Schema[^4]

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.16.43.png>) Show References[^5]

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.17.36.png>) Indexes[^6]

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.19.05.png>) Review available keyboard shortcuts for the database view

</details>

Just below the control bar, you'll see your database records.

<figure><img src="../../.gitbook/assets/CleanShot 2024-12-14 at 22.32.26.png" alt=""><figcaption></figcaption></figure>

Use your mouse or arrow keys to navigate between records and individual cells.

<figure><img src="../../.gitbook/assets/CleanShot 2024-12-14 at 22.34.26.gif" alt=""><figcaption></figcaption></figure>

To modify data, just select the cell and make your desired changes. They will be saved automatically.

<figure><img src="../../.gitbook/assets/CleanShot 2024-12-14 at 22.35.42.gif" alt=""><figcaption></figcaption></figure>

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.37.07.png>) Select one or more records by checking these boxes

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.38.28.png>) Open a card view of the selected record

![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.39.20.png>) Add a new field

***

## :heavy\_plus\_sign: Adding a new field

Click the ![](<../../.gitbook/assets/CleanShot 2024-12-14 at 22.57.46.png>) to add a new field, and choose the [type of field](field-types.md) you want to add from the panel that opens.

After you've selected your desired field type, you will be presented with a number of options. You can review each one of them and what they mean below.

<table><thead><tr><th width="199">Setting</th><th width="127" data-type="checkbox">Required?</th><th>Description</th></tr></thead><tbody><tr><td>Name</td><td>true</td><td>The name of the field you are creating</td></tr><tr><td>Description</td><td>false</td><td>Add additional details here</td></tr><tr><td>Data Structure</td><td>true</td><td><strong>Single</strong> - Each record will only store one value in this field. This is the more common selection.<br><strong>List</strong> - Each record can hold multiple values in this field. For example, if this was a table of authors, we might have a field that can store multiple books for each author.</td></tr><tr><td>Allow Nullable Values</td><td>false</td><td>A <code>null</code> value is similar to an empty value in that it represents "nothing is here", but it's still an actual value written to the record. Useful if you need to specifically check whether or not that field has data stored.</td></tr><tr><td>Format</td><td>false</td><td>For some field types, you can specify a format. This does not change the actual data being stored and is only used to enable easier viewing and editing for you inside of the table view.</td></tr><tr><td>Default Value</td><td>false</td><td>When adding new records, you can automatically populate a default value</td></tr></tbody></table>

{% hint style="info" %}
**Note**

The settings listed below only impact your API endpoints that utilize the [database link ](#user-content-fn-7)[^7]feature. This means that it is possible to make changes that break these rules via the database table view.
{% endhint %}

<table><thead><tr><th width="199">Setting</th><th width="127" data-type="checkbox">Required?</th><th>Description</th></tr></thead><tbody><tr><td>Required</td><td>false</td><td>Determines whether or not this field is required when adding a record</td></tr><tr><td>Sensitive Data</td><td>false</td><td>Hide the contents of this field from certain areas, such as request history</td></tr><tr><td>Column Visibility</td><td>false</td><td><strong>Public</strong> - The field will be available as an input<br><strong>Private</strong> - This field will not appear in inputs<br><strong>Internal</strong> - Hide this field from API inputs and responses</td></tr><tr><td>Custom Rules &#x26; Filters</td><td>false</td><td>See below.</td></tr></tbody></table>

#### Custom Rules & Filters

For each field, you can apply various rules and filters to ensure that the data is stored in the format that you expect.

<table><thead><tr><th width="179">Filter Name</th><th>Purpose</th></tr></thead><tbody><tr><td>min</td><td>Enforces a minimum number of required characters</td></tr><tr><td>max</td><td>Enforces a maximum number of required characters</td></tr><tr><td>startsWith</td><td>Enforces a prefix</td></tr><tr><td>endsWith</td><td>Enforces a suffix</td></tr><tr><td>prevent</td><td>Blacklists phrases</td></tr><tr><td>lower</td><td>Stores the value in all lowercase</td></tr><tr><td>upper</td><td>Stores the value in all uppercase</td></tr><tr><td>alphaOk</td><td>Whitelist certain alphanumeric characters</td></tr><tr><td>digitOk</td><td>Whitelist certain numbers</td></tr><tr><td>ok</td><td>Whitelist certain characters</td></tr><tr><td>pattern</td><td>Enforce a <a data-footnote-ref href="#user-content-fn-8">regex pattern</a></td></tr></tbody></table>

***

## :gear: Field Options

Right-click on the header of a field to access field-related settings and make adjustments to the options already detailed above, as well as some additional controls.

![](<../../.gitbook/assets/CleanShot 2024-12-15 at 11.48.25.png>) Rename this field

{% hint style="warning" %}
Please note that renaming a field should be handled with care, as it may impact any function steps that reference that field.

You can click ![](<../../.gitbook/assets/CleanShot 2025-02-10 at 11.18.05.png>) when viewing a database table to open **Referenced By** and view any database operations that utilize that column first to understand where changes need to be made. In the screenshot below, we know we want to update the name column, so we can use **Referenced By** to find where it's used beforehand.

![](<../../.gitbook/assets/CleanShot 2025-02-10 at 11.24.08.png>)
{% endhint %}

![](<../../.gitbook/assets/CleanShot 2024-12-15 at 11.50.54.png>) Access field settings (the options detailed earlier in this document)

![](<../../.gitbook/assets/CleanShot 2024-12-15 at 11.51.29.png>) Make a copy of this column

![](<../../.gitbook/assets/CleanShot 2024-12-15 at 11.51.51.png>) Insert a new column directly after the selected column

![](<../../.gitbook/assets/CleanShot 2024-12-15 at 11.52.26 (1).png>) Change the data type of the column

{% hint style="danger" %}
Xano will attempt to convert the data in the column to the new data type, but because of potential variations between data types, and the specific data being converted, this may not always be successful. It is **always** recommended to create a new column instead.
{% endhint %}

![](<../../.gitbook/assets/CleanShot 2024-12-15 at 11.53.38.png>) Delete the column

{% hint style="danger" %}
Deleting a column is irreversible. Proceed with caution.
{% endhint %}

***

## Adding Data

## :gear: Additional Table Settings

Click ![](<../../.gitbook/assets/CleanShot 2024-12-15 at 12.14.22.png>)to access table settings after creation, including both settings detailed earlier in this document, as well as some additional options.

<table><thead><tr><th width="183">Setting Name</th><th>Description</th></tr></thead><tbody><tr><td>Authentication</td><td>Determines whether or not this table is used for <a href="../../building-backend-features/user-authentication-and-user-data/">user authentication</a>.</td></tr><tr><td>Security</td><td>Change the table <a data-footnote-ref href="#user-content-fn-9">GUID</a>.</td></tr><tr><td>Versions</td><td>Xano maintains a version history of your table schema. You can roll back to a previous version of your schema if you've made changes that you want to undo.<br><br><strong>Note</strong>: This does not change the data in your table, only the fields. If you need to restore a backup of your table data, see <a href="../../xano-features/instance-settings/backup-and-restore.md">this document</a>.</td></tr><tr><td>Triggers</td><td>Access your <a data-footnote-ref href="#user-content-fn-10">database triggers</a>. </td></tr><tr><td>Auto-complete</td><td>Access your <a data-footnote-ref href="#user-content-fn-11">auto-complete</a> settings.</td></tr><tr><td>Clear all records</td><td>Deletes all records in the table. You can also choose to reset the primary ID back to 1 on tables that use a sequential ID.</td></tr><tr><td>Clone table</td><td>Cloning copies the table schema. Cloning <strong>does not</strong> copy existing data.</td></tr><tr><td>Export data</td><td>Export your table data using the current view as a CSV</td></tr><tr><td>Import data</td><td>Import records from a CSV <span data-gb-custom-inline data-tag="emoji" data-code="1f4d6">📖</span><a href="../migrating-your-data/csv-import-and-export.md"> <strong>Learn More</strong></a></td></tr></tbody></table>

f

[^1]: When naming your table, it's considered best practice to use camelCase for multiple words, and to not use plurals in the table name.\
    \
    For example, a table of dog breeds would be named `dogBreed`

[^2]: The description is just for you to make notes on what this table will contain, notable data constraints, or any other information you'd like to store.

[^3]: Database views are the same records in your table, but filtered and/or sorted in a certain way, or have hidden fields. Views are a great tool to use if you quickly need to review specific data, or share a table view with someone else that only contains certain information.\
    \
    :book:[ **Learn More**](database-views.md)

[^4]: Schema is just a way to refer to your database fields and their data types, such as:\
    \
    `id` integer\
    `name` text

[^5]: This option will show you all of the other objects that your table is referenced in, such as APIs, functions, and more.

[^6]: Indexes are an advanced concept, but crucial to maintaining a performant database.\
    \
    :book: [**Learn More**](../database-performance-and-maintenance/indexing.md)

[^7]: Database Link is an easy way to make sure your function stacks always have the most up to date inputs, with all of the right settings, taken straight from the table itself. It's great if you want to ensure complete parity between your database fields and inputs in a function stack.

[^8]: A regex pattern is an advanced topic, and in most cases is not required. It is a flexible string of characters that you can use to get incredibly specific about how you want data stored in this field.\
    \
    :book: [**Learn More**](https://regexone.com/)

[^9]: The GUID is an internal, unique identifier for this table. You will almost never have to change this, and should only do so under express direction from our support team.

[^10]: Database Triggers are operations that run based on changes that occur in that table, such as a record being added or updated.\
    \
    :book: [**Learn More**](broken-reference)

[^11]: **Auto-complete** is used to determine what data appears in the database view when other tables reference this one.\
    \
    For example, maybe you're referencing an author table inside of a book table, and you want to see the author name when viewing the books.\
    \
    :book: [**Learn More**](relationships.md#using-the-table-reference-field-type)
