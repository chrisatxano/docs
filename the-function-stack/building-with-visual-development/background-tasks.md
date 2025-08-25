---
description: Build and run workflows on a set schedule
---

# Background Tasks

{% hint style="info" %}
## Quick Summary

Background tasks, or sometimes referred to as "cron jobs" are workflows that run on a set schedule. Background tasks are great for things like sending out marketing emails, report generation, analytics, and large data processing jobs.

Background Tasks are available on our **Starter plan** and higher.
{% endhint %}

## Building and Using Background Tasks

{% stepper %}
{% step %}
### Click ![](<../../.gitbook/assets/CleanShot 2024-12-27 at 15.03.15 (2).png>) in the left-hand menu to access your background tasks.
{% endstep %}

{% step %}
### Click ![](<../../.gitbook/assets/CleanShot 2024-12-27 at 15.03.59.png>) to create a new background task.

Fill in your desired options, such as **name**, **description**, **tags**, [**request history**](../../maintenance-monitoring-and-logging/request-history.md), and the preferred [**data source**](../../the-database/database-basics/data-sources.md).
{% endstep %}

{% step %}
### Build your background task.

Background tasks are a little different from APIs and custom functions, in that they do not have inputs or deliver a response. Tasks have two sections that require your attention.

{% include "../../.gitbook/includes/function-stack.md" %}

{% include "../../.gitbook/includes/schedule.md" %}
{% endstep %}

{% step %}
### Set your task to active.

Once you have built your function stack and your task schedule, click Enable Task to set it as active, and publish your changes.

<figure><img src="../../.gitbook/assets/CleanShot 2024-12-27 at 15.09.18.png" alt=""><figcaption></figcaption></figure>


{% endstep %}
{% endstepper %}



## Task Data Sources

In the Task settings, you can specify what [data-sources.md](../../the-database/database-basics/data-sources.md "mention")the task targets when running. You can only specifiy a single data source per task.

If you need your task to run on multiple data sources, you can:

{% stepper %}
{% step %}
### Duplicate the task and set each version to run on separate data sources


{% endstep %}

{% step %}
### Use the Set Data Source function to target multiple data sources inside of the same task.

{% embed url="https://www.loom.com/share/e1dc64f0156c4aed8929f31c6e9ae7b4" %}
{% endstep %}
{% endstepper %}

