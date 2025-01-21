# Airtable to Xano

### Why migrate from Airtable to Xano?

#### Performance and Scalability

Many of our users have migrated from Airtable to Xano because of their need for higher scalability and performance requirements. Scaling in Airtable can be difficult with record limits, and performance issues within large bases.

Xano is designed to handle high traffic and scale as your application grows. Our tiered plans offer features like automatic scaling, caching, dedicated server locations, and load balancing, ensuring optimal performance even under heavy usage. If you anticipate your application to have significant traffic or require high scalability, Xano can provide a more robust infrastructure.

Xano’s easy-to-use functions enable performative business logic by relying on concepts used in software engineering. Unlike Airtable and other spreadsheet-based backends, you do not need to create new columns each time you want to change data (eg: to apply a formula).

In Xano you can instead use [variables](https://docs.xano.com/working-with-data/variables) to create an update container of information rather than affecting or writing to tables. This is great for complex business logic that won’t increase database storage and size.

#### Security and Compliance

In some cases, you may need to store your data in a specific server region, such as to comply with specific data privacy laws. On any of our paid plans, Xano allows you to choose from several regions to deploy your back-end from.&#x20;

Xano offers both a DPA for GDPR requirements, and a BAA for HIPAA compliance.

Read more about our security and compliance certifications [here](airtable-to-xano.md#security-and-compliance).&#x20;

#### What does migrating to Xano look like?

Xano includes a [native Airtable importer](broken-reference) that will move your data to Xano, including support for specific views. We also offer the option to [import via CSV](broken-reference).

### Rebuilding Automations

While there is no direct migration of your automations from Airtable to Xano, we want to make it as easy as possible to rebuild. Please see the table and linked resources below for common Airtable -> Xano functionality translations. Click on the Xano Function name to be taken to Xano's documentation, or review the video examples provided.

| Airtable Function      | Xano Function                                                                                    | Video Example                                 |
| ---------------------- | ------------------------------------------------------------------------------------------------ | --------------------------------------------- |
| Create Record          | [Add Record](../../the-function-stack/functions/database-requests/add-record.md)                 | [Video Example](https://youtu.be/k0GpUdsRkL0) |
| Update record          | [Edit record](../../the-function-stack/functions/database-requests/edit-record.md)               | [Video Example](https://youtu.be/rTeJamc_MYE) |
| Find records           | [Query all records](../../the-function-stack/functions/database-requests/query-all-records.md)   | [Video Example](https://youtu.be/-XjcXEtPNmk) |
| Conditional logic      | [Conditional statement](../../the-function-stack/functions/data-manipulation/conditional.md)     | [Video Example](https://youtu.be/QR4UJ2GpYDo) |
| Repeating group        | [For each loop](../../the-function-stack/functions/data-manipulation/loops.md)                   | [Video Example](https://youtu.be/AGe5JN0rZ2M) |
| At scheduled time      | [Background task](../../the-function-stack/building-with-visual-development/background-tasks.md) | [Video Example](https://youtu.be/SDXWVhBGKmQ) |
| Link to another record | [Table reference](../database-basics/field-types.md#table-reference)                             | [Video Example](https://youtu.be/z-TwxiQOIBs) |
| Lookup                 | [Addons](../../the-function-stack/functions/database-requests/query-all-records.md#using-addons) | [Video Example](https://youtu.be/z-TwxiQOIBs) |
