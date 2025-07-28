---
title: database triggers
---

You can find database triggers on each table by clicking the settings icon in the top-right corner.

Click <mark style="background-color:blue;">+ Add Database Trigger</mark> to create a new database trigger.

You can specify what [data-sources.md](../../the-database/database-basics/data-sources.md "mention") the trigger will execute on. If no data source is set, then it will execute on all data sources.

Select the **actions** that will activate this trigger.

**Inserts**\
Any time a record is added to the table

**Updates**\
Any time a record is edited

**Deletes**\
Any time a record is deleted

**Truncates**\
When the content of the database table is cleared

Finally, you can set up custom filters so that the trigger only runs if the record matches certain conditions. For example, if you only want the trigger to run if a new order is created for a user, or a new user is created with a certain role.

***

Database triggers have predefined inputs that contain all of the information you'll need to build a workflow based on the database event.

**`new`**\
This is the contents of the new record — if you're adding a record, this will contain the contents of the new record, and if you're updating a record, this will contain the contents of the updated record. On deletes and truncates, this will be empty.

**`old`**\
This is the contents of the old record — if you're deleting or editing a record, this will contain the contents of the record before the change. On inserts and truncates, this will be empty.

**`action`**\
The action that activated the trigger. Valid options are `insert`  `update`  `delete`  `truncate`

**`data source`**\
The datasource this trigger has been executed against
