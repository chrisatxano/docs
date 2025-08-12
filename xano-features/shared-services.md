---
description: >-
  Share and install Shared Services to reuse functions and middleware across
  Workspaces.
hidden: true
noIndex: true
icon: share-nodes
---

# Shared Services

{% embed url="https://youtu.be/omw4LRej4M4" %}

## What is a Shared Service?

Shared Services allow you to develop [custom-functions](../the-function-stack/building-with-visual-development/custom-functions/ "mention") and [middleware.md](../the-function-stack/building-with-visual-development/middleware.md "mention") in one workspace, and share them across your entire instance, allowing them to be used in other workspaces.

Shared Services adopt a traditional build-test-deploy architecture, which means you can build, iterate, and choose when to deploy new versions of your shared services, as well as choose which versions to install into each workspace.&#x20;

## Creating and Deploying Shared Services

{% stepper %}
{% step %}
### Select the function(s) or middleware you want to deploy as a Shared Service, and click Manage Sharing

<div align="left"><figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 09.19.17@2x.png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Select the option to add what you've chosen to a Shared Service&#x20;

<div align="left"><figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 09.20.31@2x (1).png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### From the left-hand menu, choose <mark style="color:blue;">Library</mark> > <mark style="color:blue;">Shared Services</mark>&#x20;


{% endstep %}

{% step %}
### Click the three dots next to your newly created Shared Service and choose <mark style="color:blue;">Share Service to Instance</mark>

<figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 09.24.55@2x.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Configure your Shared Service

| <div><figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 09.25.43@2x.png" alt=""><figcaption></figcaption></figure></div> | <p>From this panel, you can configure the following options whether you are deploying a new Shared Service, or editing an existing one.<br><br><strong>Name</strong> - Make sure your Shared Service has a recognizable name<br><br><strong>Description</strong> - Let the rest of your instance know what this Shared Service is for / contains<br><br><strong>Functions / Middleware</strong> - You can remove shared Functions and Middleware from here, or review what's included<br><br><strong>Update Status</strong> - Update the status and version number of the shared service</p> |
| ---------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
{% endstep %}
{% endstepper %}

## Using a Shared Service

{% stepper %}
{% step %}
### Head to the workspace where you want to use a Shared Service


{% endstep %}

{% step %}
### From the left-hand menu, choose <mark style="color:blue;">Library</mark> > <mark style="color:blue;">Shared Services</mark>&#x20;


{% endstep %}

{% step %}
### Click <mark style="color:blue;">Shared Services with You</mark>

<div align="left"><figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 09.58.57@2x.png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Click the Install button to begin using the desired Shared Service

<div align="left"><figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 09.59.21@2x.png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Use the shared functions and middleware

From the Library > Functions or Library > Middleware, you'll see the items that have been shared with you through this Shared Service.

<div align="left"><figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 10.02.25@2x.png" alt="" width="375"><figcaption></figcaption></figure></div>

#### Functions

Functions are made available in the Add Function menu when building your function stacks.

<figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 10.00.27@2x.png" alt=""><figcaption></figcaption></figure>

#### Middleware

You'll find any shared Middleware in the Add Middleware menus from the settings of your workspace, API groups, or specific function stacks.

<div align="left"><figure><img src="../.gitbook/assets/CleanShot 2025-08-04 at 10.03.26@2x.png" alt="" width="375"><figcaption></figcaption></figure></div>

{% hint style="info" %}
When using a Shared Service inside of another workspace, you will not be able to edit the function stack of that service's functions or middleware.
{% endhint %}
{% endstep %}
{% endstepper %}

## Shared Service Statuses

#### Staged

Ready to be deployed across the instance

#### Shared

Has been deployed across the instance

#### Deprecated

Typically indicates that this service should not be used going forward, but is not being removed to ensure continued functionality of existing implementations

#### Deactivated

Removes the Shared Service from wherever it is installed.

{% hint style="warning" %}
Removing an item from a Shared Service does not uninstall it from any of the other workspaces. Deactivating is the only way for forcibly remove a Shared Service and its items from another workspace.
{% endhint %}
