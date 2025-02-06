# Compliance Center

{% hint style="success" %}
The Compliance Center is included with **Scale** and **Enterprise** plans. Certain plans may not contain all of the available features of the Compliance Center.
{% endhint %}

The Compliance Center tracks all changes made to each Workspace object, the team member that made the change, the time the change was made, and on which Branch the change was made.

Workspace objects include Database tables and schema, API groups, API endpoints, Addons, Custom Functions, and Background Tasks. They do not include changes to Database records.

#### Where to find the Compliance Center

To access the Compliance Center navigate to the Settings tab of the Workspace, open the menu icon in the top right, and select Compliance.

<figure><img src="../../.gitbook/assets/CleanShot 2023-01-31 at 13.49.28.png" alt=""><figcaption><p>Access the Compliance Center from the Settings page.</p></figcaption></figure>

Inside the Compliance Center, you can access various reporting areas for different types of activity in your workspace.

<figure><img src="../../.gitbook/assets/CleanShot 2024-01-22 at 08.54.39.png" alt=""><figcaption></figcaption></figure>

#### Middleware Reporting

<figure><img src="../../.gitbook/assets/CleanShot 2024-01-22 at 08.58.12.png" alt=""><figcaption></figcaption></figure>

Middlware Reporting allows you to audit your APIs, functions, and tasks to ensure that they are all using the expected [middleware](../../the-function-stack/building-with-visual-development/middleware.md). From this view, you can also review when APIs have customized middleware, meaning they have been given different settings than what is applied at the parent object level.

#### Version History

Version History is an aggregated dashboard of all schema changes across tables, APIs, functions, addons, and tasks.

<figure><img src="../../.gitbook/assets/CleanShot 2024-01-22 at 09.02.54.png" alt=""><figcaption></figcaption></figure>

You can click on any one of these records and immediately navigate to the item that was changed to review further as necessary.

Each change to a Workspace object is recorded in the Compliance Center:

**ID** - the unique ID of a specific change.

**Object** - the Workspace Object that was changed.&#x20;

**Branch** - which Branch the change occurred on.&#x20;

**Author** - the team member that made that change.

**Date** - the time the change occurred.&#x20;

### Instance Activity

The Compliance Center add-on also includes Instance Activity, available from your instance selection screen. To access, click the :gear: icon that appears to the right side of the instance selector, and on the panel that appears, choose Instance Activity.

<figure><img src="../../.gitbook/assets/CleanShot 2023-06-20 at 07.37.04.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/CleanShot 2023-06-20 at 07.38.02.png" alt="" width="375"><figcaption></figcaption></figure>

Instance Activity offers administrators history on access to the instance. This includes login events and instance access activity, as well as team member management and permission updates. This includes time and date, user name, their location, IP address, and user agent.

<figure><img src="../../.gitbook/assets/CleanShot 2023-06-20 at 07.40.18.png" alt=""><figcaption></figcaption></figure>

