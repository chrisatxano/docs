# Maintenance

## How do I perform maintenance on my Xano instance?

All paid plans include access to the Maintenance panel, accessible via your instance settings. There are different maintenance operations you can perform to help troubleshoot issues you might be having in Xano, or to manage your database storage.

## Accessing the Maintenance Panel

Head to your instance settings from your instance selection screen and choose Maintenance.

<figure><img src="../../.gitbook/assets/CleanShot 2023-05-22 at 11.50.15.png" alt=""><figcaption></figcaption></figure>

From the next panel that appears, you can choose between several maintenance options.

## **Clear Internal Cache**

This maintenance action clears the internal cache within the instance. This does not affect any drafts or redis storage. You should use this option first if you are experiencing any or multiple of the following symptoms:

* Slow loading in Xano or function stacks not loading
* APIs not responding or responding with strange errors such as "invalid app"

## **Database Maintenance**

* [**Analyze**](maintenance.md#analyze)
* [**Vacuum**](maintenance.md#vacuum)

Database maintenance is automatically done daily but Xano does offer ways to manually run PostgreSQL analyze and vacuum commands through the Instance Maintenance panel.\
\
PostgreSQL's VACUUM and ANALYZE functions are essential maintenance tasks for optimizing database performance. \
\
Together, VACUUM and ANALYZE help keep the database running smoothly by managing storage and providing accurate statistics for optimal query planning and execution.

### Analyze

ANALYZE gathers statistics about the data distribution in tables, enabling the query optimizer to generate efficient execution plans. It updates the query planner's knowledge of the data, improving query performance by enabling better index selection and join strategies.

### Vacuum

VACUUM reclaims storage space by removing obsolete or dead data that remains after updates or deletions. It helps prevent performance degradation caused by fragmentation and frees up disk space.

#### Partial VACUUM

This command analyzes and cleans up the database, but it does not necessarily reclaim all available disk space. It marks the space previously occupied by deleted rows as reusable for future inserts and updates. VACUUM also updates statistics used by the query planner to improve query performance.

#### Full VACUUM

{% hint style="warning" %}
**Full VACUUM requires at least 50% free storage space before continuing. Proceeding with a Full VACUUM without enough free storage can fail or cause instance downtime.**
{% endhint %}

This command performs a more thorough cleanup compared to partial. It reclaims all available disk space by rewriting the entire table and indexes from scratch. This process can be more resource-intensive and time-consuming, as it involves copying the data to a new file and rebuilding the indexes. Full VACUUM can significantly improve disk space utilization but **may cause downtime** for larger tables.
