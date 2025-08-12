# Triggers

{% hint style="info" %}
**Quick Summary**

Triggers are workflows that can run based on other events that happen in your workspace. Xano offers triggers for:

* Database operations (adds, edits, deletes)
* Realtime events
* Workspace events (currently limited to branching operations)
* MCP Server connections

Triggers are available on our **Starter plan** and higher.
{% endhint %}

## What are triggers?

Triggers in Xano are workflows that will run only when triggered by another event. You can build triggers for the following events.

| Event Type     | Event                                 |
| -------------- | ------------------------------------- |
| **Database**   | New records                           |
|                | Record edits                          |
|                | Record deletes                        |
|                | Table truncate (deleting all records) |
| **Realtime**   | Channel events                        |
| **Workspace**  | New branch                            |
|                | Branch merge                          |
|                | Live branch change                    |
| **MCP Server** | Client Connect                        |

## Accessing and Creating Triggers

{% stepper %}
{% step %}
### Database Triggers

{% include "../../.gitbook/includes/database-triggers.md" %}

***
{% endstep %}

{% step %}
### Realtime Triggers

Realtime triggers are created for each channel. Once you've created a realtime channel, click the <mark style="background-color:blue;">+ Add Channel Trigger</mark> button to create a new channel trigger.

Select the **actions** that will activate the trigger.

**Message**\
Any time a new message is sent to the channel

**Join**\
Any time a new connection is made to the channel

***

Realtime triggers have predefined inputs that contain all of the information you'll need to build a workflow based on the realtime event.

**`Action`** and ~~**Command**~~\
This will be either 'join' or 'message' depending on what was responsible for executing the trigger.

_**Action** and **Command** currently have the same values, but behind the scenes, the values do not come from the same source. We maintain two separate inputs for the purpose of expanding this functionality in the future._

**`Channel`**\
The channel that this command or message is being sent to

**`commandOptions`**\
Any options that are provided with the command being sent to the channel

**`payload`**\
The contents of the command, such as the message body

**`client`**\
An internal client ID

***
{% endstep %}

{% step %}
### Workspace Triggers

Workspace triggers can be created to execute workflows based on certain workspace-wide events. Currently, these are limited to branch changes.

You can find workspace triggers by clicking the settings icon in the top-right corner of your workspace dashboard.

Click <mark style="background-color:blue;">+ Add Workspace Trigger</mark> to create a new workspace trigger.

Select the **action(s)** that will execute this trigger.

**Branch Live**\
Any time a branch status is set to live

**Branch Merge**\
When a branch is merged

**Branch New**\
When a new branch is created
{% endstep %}

{% step %}
### MCP Triggers <a href="#mcp" id="mcp"></a>

MCP triggers can be created to run any time a client connects to the MCP server. This is useful for functions like:

* Logging connections to the MCP server
* Dynamically adjusting server instructions based on other data, such as the user who is connecting
* Restricting tools per connection

You can find MCP triggers by clicking the settings icon in the top-right corner of your MCP server.

Click <mark style="background-color:blue;">+ Add MCP Server Trigger</mark> to create a new MCP server trigger.

MCP Server triggers offer the following inputs:

**`toolset`** \
Contains the server information, such as the name and instructions.

**`tools[]`** \
An array that contains each tool.
{% endstep %}

{% step %}
### AI Agent Triggers

Agent triggers are similar to MCP triggers. They can be used when an agent is called to perform tasks such as:

* Logging connections
* Dynamically adjusting available functions and tools
* Adjusting the system prompt based on user or other data

You can find Agent Triggers in the settings for your Agent.

**`toolset`** \
Contains the server information, such as the name and instructions.

**`tools[]`** \
An array that contains each tool.
{% endstep %}
{% endstepper %}
