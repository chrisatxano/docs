---
description: >-
  Agents are used to perform 'fuzzy logic', or perform workflows that require
  intricate decision making powered by an AI model
icon: robot
---

# Agents

{% hint style="success" %}
#### **Not looking for Agents, and just want to connect to your favorite AI models, like ChatGPT?**

**Check out this resource instead:** [chatbots.md](../../building-backend-features/chatbots.md "mention")
{% endhint %}

{% hint style="info" %}
## Quick Summary

AI agents in Xano refer to autonomous entities designed to perform tasks by leveraging artificial intelligence. Your Xano Agents can integrate with your database, APIs, tasks, and functions, as well as external systems.

These agents can process data, make decisions, and execute actions without human intervention. AI agents in Xano can efficiently handle a variety of applications, from chatbots to data analysis tools, enhancing automation and productivity.
{% endhint %}

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th data-hidden data-card-cover data-type="files"></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/yt (3).png" alt="" data-size="line"> <strong>Introduction to AI Agents</strong></td><td><a href="../../.gitbook/assets/ai agents.png">ai agents.png</a></td><td><a href="https://youtu.be/iEn20cy5LUw?feature=shared">https://youtu.be/iEn20cy5LUw?feature=shared</a></td></tr><tr><td><img src="../../.gitbook/assets/yt (3).png" alt="" data-size="line"> <strong>Tools for Agents &#x26; MCP Servers</strong></td><td><a href="../../.gitbook/assets/ai tools.png">ai tools.png</a></td><td><a href="https://youtu.be/D1HtzC6yiO4">https://youtu.be/D1HtzC6yiO4</a></td></tr></tbody></table>

{% embed url="https://youtu.be/iEn20cy5LUw?refresh=yes" %}

## What are Agents?

AI agents in Xano serve as integral components for building intelligent, automated systems as a part of your backend. These agents are designed to function autonomously, interacting with various elements of your app such as your APIs and database, as well as external systems, to streamline operations and enhance efficiency. AI agents can intelligently interpret inputs, process data, and deliver actionable outputs, all without the need for continuous human oversight.

Agents in Xano can leverage any of the most popular AI models once you provide an API key, such as:

* OpenAI
* Grok
* Anthropic / Claude
* Google Gemini

You can leverage the same visual builder you're used to using today to create workflows and functions that enable the agents to interact seamlessly with databases and external systems. With these foundational elements in place, AI agents can execute complex tasks, perform data analysis, or even serve as intelligent chatbots, making them versatile tools for a wide range of applications.

## Building Agents in Xano

{% stepper %}
{% step %}
### From the left-hand navigation, click AI, then <mark style="background-color:blue;">Agents</mark>&#x20;


{% endstep %}

{% step %}
### Click <mark style="background-color:blue;">+ Add Agent</mark>&#x20;


{% endstep %}

{% step %}
### Fill out the necessary information

{% hint style="danger" %}
## Note

Please note that **not all models support certain features** such as:

* Structured outputs
* Reasoning
* Tool calls

In addition, some models may support individual features, but not **combinations of features**, such as:

* Structured outputs with tool calls
* Tool calls with reasoning

This is not an issue with Xano or with your agent builds — this is dictated by the model you're using. If you encounter errors when testing your Agents, try using a different model and check to make sure that your model supports the feature(s) you have enabled, especially if you are using more than one of these features together.
{% endhint %}

{% hint style="success" %}
Use the **Prompt Assistant** to help you build the best system prompts for your Agents!

![](<../../.gitbook/assets/CleanShot 2025-08-07 at 14.01.00.png>)
{% endhint %}

<table><thead><tr><th width="173.0833740234375">Parameter Name</th><th>Purpose</th><th>Example</th></tr></thead><tbody><tr><td>Name</td><td>Give your agent a name that describes its role or primary function</td><td>Order Processing Agent</td></tr><tr><td>Description</td><td>Internal only field for describing what your agent does</td><td>Analyzes incoming orders, decides on fulfillment priority, and triggers shipping workflows</td></tr><tr><td>Agent Settings</td><td>Define dynamic inputs the Agent can accept from Function Stack workflows and reference environment variables</td><td>Configure placeholders with <code>{{ $args.propertyName }}</code> for workflow inputs, and <code>{{ $env.variableName }}</code> for environment variables</td></tr><tr><td>Model Host</td><td>Select the AI model host for the agent</td><td>Anthropic (Claude)<br>OpenAI<br>Google Gemini</td></tr><tr><td>Max Steps</td><td>Define how many steps the Agent can execute to complete its task.</td><td>5</td></tr><tr><td>System Prompt</td><td>The core instructions that define your Agent's role, capabilities, and behavior</td><td>You are a helpful AI Agent that completes tasks accurately. When you need additional information to complete a task, use the available tools. Never make assumptions.</td></tr><tr><td>Prompt Type</td><td>The type of prompt that is being provided to the Agent. This can be either <code>messages</code>, which is a list of previous messages from another conversation, or <code>prompt</code>, which is just a standard prompt.</td><td><code>messages</code> or <code>prompt</code></td></tr><tr><td>Prompt</td><td>Additional context and instructions sent with each request</td><td>Please help the customer with their inquiry: {{ $args.customer_message }}. Their account ID is {{ $args.account_id }}.</td></tr><tr><td>Structured Outputs</td><td>Configure your Agent to return responses in a specific JSON format using structured outputs and your predefined schema</td><td>Checkbox to enable/disable</td></tr><tr><td>Output Schema</td><td>Define the JSON structure for structured outputs</td><td>text, user_email</td></tr><tr><td>Tags</td><td>Categories for organizing your Agents</td><td>contact, messaging</td></tr><tr><td>Request History</td><td>Controls logging of requests to<a data-mention href="../../maintenance-monitoring-and-logging/request-history.md">request-history.md</a></td><td><p>Inherit Settings: Uses workspace logging settings</p><p>Disabled: No logs recorded</p><p>Enabled: Logs requests with options for storage limits</p></td></tr></tbody></table>


{% endstep %}

{% step %}
### Add some tools to your Agent

An Agent needs tools to function — the tools are essentially single functions that the Agent can perform, such as looking up user data or cancelling a subscription.

{% include "../../.gitbook/includes/ai-tools.md" %}
{% endstep %}
{% endstepper %}

## Running your Agent

Your Agents will be called as a part of another function stack using the **Call AI Agent** function.

{% stepper %}
{% step %}
### Add the Call AI Agent function to your function stack

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-11 at 12.57.35.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Select your Agent from the list

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-11 at 12.58.06.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Configure your Agent's arguments and options

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-11 at 12.59.44.png" alt=""><figcaption></figcaption></figure>

In the **`args`** section, define a JSON object by typing `{}` into the box.

{% hint style="info" %}
You can also just copy and paste an entire JSON object here to speed up the process, if you have that available.
{% endhint %}

Use the Set filter by clicking Set when hovering over the value box.

Set requires a key and a value — the key is essentially "this is the type of data" and the value is the data itself. These are going to correspond to the arguments you defined when setting up your agent.

For example, if my system prompt looks like this:

`Please use the customer data here: {{$args.customer_info}} to answer the customer question`

Your args would look like this, replacing the value with actual customer information.

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-11 at 13.03.37.png" alt=""><figcaption></figcaption></figure>

In the **`allow_tool_execution`** section, you can decide whether or not this run should allow execution of any tools the agent has access to using a `true` or `false` value.
{% endstep %}
{% endstepper %}

## Structured Outputs

Structured Outputs are used for providing a specific format that you need your agent to return its result as. This is especially useful when you are calling agents from other agents and want to ensure that the output from Agent 1 is clear and easy to understand for Agent 2.

You can add structured outputs to your Agent in the settings by checking the Structured Outputs checkbox, and then clicking <mark style="background-color:blue;">+ Add Output Schema</mark> to build your output schema.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-06-30 at 17.02.11.png" alt="" width="432"><figcaption></figcaption></figure></div>

## Example Agents

### :robot: Customer Support Agent

**Purpose**

This Agent is designed to handle customer inquiries that don't typically need human interaction.

**Tools**

An Agent designed for this purpose might have the following tools available:

* **Get User Information**
  * Retrieves user information from the database
* **Update User Information**
  * Retrieves existing user information from the database, and updates it per a user's request, such as changing their phone number or address
* **Send Verification Code**
  * This tool could be used as a secondary security measure to verify that the request is coming from the user that the data belongs to
* **Change Subscription**
  * Based on the user's request, this could be used to stop an upcoming renewal, or cancel a subscription immediately. Because Agents excel at 'fuzzy logic' depending on certain circumstances, this could also be used for things like churn prevention — dynamically offering the user a discount to stay, for example
* **Search Documentation**
  * Calls an external API from your chosen documentation platform to search your product documentation in an attempt to solve the user's query without human intervention
* **Create Support Ticket**
  * In the case that the Agent does not have the necessary tools to solve the user's concerns, create a support ticket for human intervention

### Agent Configuration

| Parameter Name     | Purpose                                                                                                      | Example                                                                                                                                                                                                                                                                                                                                         |
| ------------------ | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name               | Give your agent a name that describes its role or primary function                                           | Customer Support Agent                                                                                                                                                                                                                                                                                                                          |
| Description        | Internal only field for describing what your agent does                                                      | Handles customer inquiries that don't typically need human interaction. Can retrieve user information, update accounts, send verification codes, manage subscriptions, search documentation, and escalate to human support when needed.                                                                                                         |
| Agent Settings     | Define dynamic inputs the Agent can accept from Function Stack workflows and reference environment variables | `{{ $args.customer_message }}`, `{{ $args.user_id }}`, `{{ $args.ticket_priority }}`, `{{ $env.SUPPORT_API_KEY }}`                                                                                                                                                                                                                              |
| Model Host         | Select the AI model host for the agent                                                                       | Claude Sonnet 4                                                                                                                                                                                                                                                                                                                                 |
| Max Steps          | Define how many AI requests the Agent can execute to complete a task                                         | 8                                                                                                                                                                                                                                                                                                                                               |
| System Prompt      | The core instructions that define your Agent's role, capabilities, and behavior                              | You are a helpful Customer Support Agent that resolves customer inquiries efficiently. Always verify user identity before making account changes. Use available tools to gather information and resolve issues. If you cannot resolve an issue, create a support ticket for human intervention. Be polite, professional, and solution-oriented. |
| Prompt             | Additional context and instructions sent with each request                                                   | Customer inquiry: `{{ $args.customer_message }}`. User ID: `{{ $args.user_id }}`. Account status: `{{ $args.account_status }}`. Please help resolve this customer's issue while following security protocols.                                                                                                                                   |
| Structured Outputs | Configure your Agent to return responses in JSON format using structured outputs and your predefined schema  | ✅ Enabled                                                                                                                                                                                                                                                                                                                                       |
| Output Schema      | Define the JSON structure for agent responses                                                                | response\_message, action\_taken, ticket\_created, follow\_up\_required                                                                                                                                                                                                                                                                         |
| Tags               | Categories for organizing your Agents                                                                        | customer-service, support, automation                                                                                                                                                                                                                                                                                                           |
| Request History    | Controls logging of tool requests                                                                            | Enabled: Logs requests with options for storage limits                                                                                                                                                                                                                                                                                          |

### Example Interaction Flowcharts

#### 1. Account Information Request

_"What's my current subscription plan?"_

```mermaid
flowchart TD
    A[Customer asks about subscription] --> B[Get User Information]
    B --> C[Retrieve account details]
    C --> D[Format response with plan details]
    D --> E[Send subscription info to customer]
    
    style A fill:#e1f5fe
    style E fill:#e8f5e8
```

#### 2. Address Change Request

_"I need to update my shipping address"_

```mermaid
flowchart TD
    A[Customer requests address change] --> B{User identity verified?}
    B -->|No| C[Send Verification Code]
    C --> D{Code valid?}
    D -->|No| E[Create Support Ticket]
    D -->|Yes| F[Identity confirmed]
    B -->|Yes| F
    F --> G[Update User Information]
    G --> H[Save new address]
    H --> I[Confirm changes to customer]
    
    style A fill:#e1f5fe
    style I fill:#e8f5e8
    style E fill:#ffebee
```

#### 3. Billing Question

_"Why was I charged twice this month?"_

```mermaid
flowchart TD
    A[Customer reports billing issue] --> B[Get User Information]
    B --> C[Review billing history]
    C --> D{Simple explanation?}
    D -->|Yes| E[Explain charges to customer]
    D -->|No| F[Search Documentation]
    F --> G{Found billing policy info?}
    G -->|Yes| H[Provide policy explanation]
    G -->|No| I[Create Support Ticket]
    I --> J[Escalate to billing team]
    
    style A fill:#e1f5fe
    style E fill:#e8f5e8
    style H fill:#e8f5e8
    style J fill:#ffebee
```

#### 4. Technical Issue

_"The app keeps crashing on my phone"_

```mermaid
flowchart TD
    A[Customer reports app crash] --> B[Search Documentation]
    B --> C{Found troubleshooting steps?}
    C -->|Yes| D[Provide step-by-step guide]
    D --> E[Ask if issue resolved]
    E -->|Yes| F[Mark as resolved]
    E -->|No| G[Create Support Ticket]
    C -->|No| G
    G --> H[Escalate to technical team]
    
    style A fill:#e1f5fe
    style F fill:#e8f5e8
    style H fill:#ffebee
```

