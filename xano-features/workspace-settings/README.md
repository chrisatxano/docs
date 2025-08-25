---
description: An explanation of all available workspace settings
icon: gear
---

# Workspace Settings

{% hint style="info" %}
## Before you begin

Please note that this page provides only a general overview of some settings. When relevant, each section will contain a link to that feature specific documentation, which is recommended reading before adjusting anything
{% endhint %}

## General Settings

> This panel is accessible by heading to your workspace dashboard and clicking the ⋮ icon > Settings

<table><thead><tr><th width="186.49993896484375">Setting</th><th>Purpose</th></tr></thead><tbody><tr><td><p>Name<mark style="color:red;">*</mark></p><p><sup>text</sup></p></td><td>Give your workspace a unique name</td></tr><tr><td><p>Description</p><p><sup>text</sup></p></td><td>A description of your workspace</td></tr><tr><td>Use Internal Documentation Tool <sup>checkbox</sup></td><td>Enables the Internal Documentation Tool for your function stacks--a plain text input typically used to house information such as example inputs</td></tr><tr><td>Show Start</td><td>Enables the Start Page, which offers beginner guidance on working in Xano</td></tr><tr><td>Show Marketplace</td><td>Enables the Marketplace, which contains snippets and extensions available for import into your Xano workspace</td></tr><tr><td>AI Preferences</td><td>Accept AI specific license terms to use certain AI-powered features, such as our <a data-mention href="../../xano-ai/ai-database-assistant.md">ai-database-assistant.md</a></td></tr></tbody></table>

## Data Sources

> [data-sources.md](../../the-database/database-basics/data-sources.md "mention") allow you to maintain separate databases with the same schema. Useful for maintaining things like separate production and testing data sets.

<table><thead><tr><th width="157.3333740234375">Setting</th><th>Purpose</th></tr></thead><tbody><tr><td>Manage</td><td>Quick access to managing your data sources, such as browsing or adding new ones</td></tr><tr><td>Migrate</td><td>Allows you to migrate data from one data source to another</td></tr></tbody></table>

{% include "../../.gitbook/includes/branch-defaults.md" %}

## Middleware

> Provides quick access to [middleware.md](../../the-function-stack/building-with-visual-development/middleware.md "mention") settings

## Clone Workspace

> Creates a clone of your workspace

Cloning a workspace will copy all database table schema, API groups, APIs, functions, addons, and tasks into another workspace. It will **not** copy the database table records.

## Export Workspace

> Exports a copy of your workspace

Exporting your data is done in the background and may take a significant amount of time to process depending on the amount of data in your workspace.

You may also include media attachments, but this may increase the export size and time significantly depending on the number of files.

**Once the export is complete, you will receive an email notification as well as a notification in Xano that your data is ready to be downloaded. This export will be available for 12 hours.**

## Xano Link

> [xano-link.md](../advanced-back-end-features/xano-link.md "mention") is a premium addon for syncing branches and database schema from one workspace to others.

## Triggers

> [triggers.md](../../the-function-stack/building-with-visual-development/triggers.md "mention") allow you to build workflows that run based on when certain events happen, such as when a database record is added or when certain branch actions take place.

## Statement Explorer

> The [statement-explorer.md](../../maintenance-monitoring-and-logging/statement-explorer.md "mention") allows you to search for instances of specific statements across your workspace, such as finding all Query All Records functions. This is useful for things like security audits and making sweeping changes or improvements across multiple workflows.

## Realtime Settings

> Access your [realtime-in-xano.md](../../realtime/realtime-in-xano.md "mention") settings from here

## Reset Drafts

> Resets all drafts in the current workspace

Sometimes, you may want to clear out all drafts and revert fully back to published versions of your function stacks. This option allows you to quickly do so. It can also be useful in the rare circumstance that you have functions that are in draft state or have been recently published and are not behaving correctly.

This action is **not reversible**, so if you have questions, reach out to our support chat before proceeding.

## Compliance Center

> Offers quick access to the [compliance-center.md](../../enterprise/enterprise-features/compliance-center.md "mention"), which is a premium feature that enables advanced auditing of the state of your workspace and actions of your team members

## Table Format

{% include "../../.gitbook/includes/table-format.md" %}

{% include "../../.gitbook/includes/table-names.md" %}
