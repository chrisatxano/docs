---
description: Audit Logs provide clear and searchable logging of all workspace changes
---

# Audit Logs

{% hint style="info" %}
## Quick Summary

Audit Logs provide detailed and searchable information about any changes or activity inside of a Xano workspace.&#x20;
{% endhint %}

## What's included in Audit Logs?

{% tabs fullWidth="true" %}
{% tab title="Workspace" %}
### Workspace

* **Create Workspace** - Create new workspaces
* **Update Workspace** - Modify workspace settings
* **Reset Workspace** - Reset workspace to default state
* **Read Workspace** - View workspace information
* **Delete Workspace** - Remove workspaces

### Data Sources

* **Create Data Source** - Set up new data connections
* **Update Data Source** - Modify data source settings
* **Delete Data Source** - Remove data sources

### Branch Management

* **Create Branch** - Set up new development branches
* **Update Branch** - Modify branch settings
* **Delete Branch** - Remove branches
* **Merge Branch** - Combine branches
* **Set Live Branch** - Designate the active production branch
{% endtab %}

{% tab title="Environment Variables" %}
* **Read Environment Variable** - View environment variable details
* **Create Environment Variable** - Create new environment variable
* **Update Environment Variable** - Modify environment variable
* **Delete Environment Variable** - Remove environment variabl
{% endtab %}

{% tab title="Tenants" %}
* **Read Tenant Environment Variable** - View tenant environment variables
* **Create Tenant Environment Variable** - Create tenant environment variable
* **Update Tenant Environment Variable**  - Modify tenant environment variable
* **Delete Tenant Environment Variable**  - Remove tenant environment variable
* **Create Tenant** - Set up new tenants
* **Update Tenant** - Modify tenant settings
* **Delete Tenant** - Remove tenants
* **Read Tenant License** - View tenant licensing information
* **Update Tenant License** - Modify tenant licenses
* **Impersonate Tenant** - Act on behalf of a tenant

### Backup & Restore

* **Create Tenant Backup** - Generate tenant backups
* **Restore Tenant Backup** - Restore from tenant backups

### Release Management

* **Create Release** - Generate new releases
* **Update Release** - Modify release information
{% endtab %}

{% tab title="Database" %}
### Table Activity

* **Create Table** - Set up new database tables
* **Update Table** - Modify table structure and settings
* **Delete Table** - Remove tables
* **Restore Table** - Recover deleted tables
* **Truncate Table** - Clear all data from tables
{% endtab %}

{% tab title="Function Stacks" %}
### API Groups

* **Create API Group** - Set up new API endpoint groups
* **Update API Group** - Modify API group settings
* **Delete API Group** - Remove API groups
* **Restore API Group** - Recover deleted API groups

### APIs

* **Create Query** - Build new API
* **Update Query** - Modify existing API
* **Delete Query** - Remove API
* **Restore Query** - Restored a previous version
* **Run Query** - Execute database queries

### Functions

* **Create Function** - Build new custom functions
* **Update Function** - Modify existing functions
* **Delete Function** - Remove functions
* **Restore Function** - Restored a previous version

### Add-ons

* **Create Add-on** - Install new add-ons
* **Update Add-on** - Modify add-on settings
* **Delete Add-on** - Remove add-ons
* **Restore Add-on** - Restored a previous version
* **Run Add-on** - Execute add-on functionality

### Tasks

* **Create Task** - Set up new automated tasks
* **Update Task** - Modify task settings
* **Delete Task** - Remove tasks
* **Restore Task** - Restored a previous version
* **Run Task** - Execute tasks
{% endtab %}
{% endtabs %}

## Audit Log Retention

Depending on your plan, you'll be able to retain different amounts of audit logs.

* Free/Build: `24h`
* Launch, Starter, Starter+ : `7 days`
* Scale, Pro, Pro +: `28 days`
* Enterprise/Custom: `Unlimited`

## Accessing and Using Audit Logs

{% hint style="info" %}
You can also view Audit Logs for an entire instance at once by accessing the settings from the Workspace selection screen.
{% endhint %}

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-08 at 09.41.42.png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
Please note that if your instance has [rbac-role-based-access-control.md](../../enterprise/enterprise-features/rbac-role-based-access-control.md "mention") enabled, any users that you want to be able to view the logs need to have the **Workspace Logs** permission applied.
{% endhint %}

{% stepper %}
{% step %}
### From the workspace dashboard, click the three dots in the top-right corner, and choose Audit Logs


{% endstep %}

{% step %}
### Viewing Audit Logs

From the main view, you'll be presented with a list of all available logs.

<figure><img src="../../.gitbook/assets/CleanShot 2025-06-30 at 09.22.00.png" alt=""><figcaption></figcaption></figure>

Click on a log to view more details about that event.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-06-30 at 09.45.57.png" alt="" width="223"><figcaption></figcaption></figure></div>

On some event types, you'll have a <mark style="background-color:blue;">Go To</mark> button to quickly navigate to where the change took place. The JSON playload can be useful for your own external data collection.
{% endstep %}

{% step %}
### Searching and Filtering Audit Logs

You can search your Audit Logs from the search panel above the list.

<figure><img src="../../.gitbook/assets/CleanShot 2025-06-30 at 09.24.29.png" alt=""><figcaption><p>Please note that the search only looks at the summary title of each event currently.</p></figcaption></figure>

You can also use the filters to quickly narrow down specific event types, users, and labels.

<figure><img src="../../.gitbook/assets/CleanShot 2025-06-30 at 09.34.19.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Exporting Audit Logs

#### Exporting to CSV

From the top-right corner of your screen, click the three dots and choose <mark style="background-color:blue;">Export CSV</mark> to export the current batch of logs as a CSV.

#### Using the Metadata API

There are four new endpoints available via the [metadata-api](../metadata-api/ "mention") to retrieve Audit Logs.


{% endstep %}
{% endstepper %}

{% openapi-operation spec="dev-r170" path="/audit_log" method="get" %}
[OpenAPI dev-r170](https://gitbook-x-prod-openapi.4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/raw/67f2e77b0e710d4ae46160823f1586d8cf0a96623cb8ab0bac804827c8416ca9.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20250812%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20250812T195612Z&X-Amz-Expires=172800&X-Amz-Signature=b16ec0ce61e5fab66f15502c26355dcba5e068a262e2dab80b3adb956b8ee420&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="dev-r170" path="/audit_log/search" method="post" %}
[OpenAPI dev-r170](https://gitbook-x-prod-openapi.4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/raw/67f2e77b0e710d4ae46160823f1586d8cf0a96623cb8ab0bac804827c8416ca9.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20250812%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20250812T195612Z&X-Amz-Expires=172800&X-Amz-Signature=b16ec0ce61e5fab66f15502c26355dcba5e068a262e2dab80b3adb956b8ee420&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
