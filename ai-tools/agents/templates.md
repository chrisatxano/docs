# Templates

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="image"></th></tr></thead><tbody><tr><td><strong>Agent History &#x26; Debugging Mode</strong></td><td>Monitors, analyzes, and debugs your agent’s behavior by logging every run, step, and tool call. Includes a dashboard for performance stats and run details, plus automated logging to capture inputs, outputs, and execution history.</td><td><a href="templates.md#agent-history-and-debugging-mode">#agent-history-and-debugging-mode</a></td><td><a href="../../.gitbook/assets/YT (1).png">YT (1).png</a></td></tr><tr><td><strong>Conversation History</strong></td><td><p>Install this snippet to manage and persist user interactions. It's the perfect starting point for any chatbot or conversational agent.</p><p><br></p></td><td><a href="templates.md#conversation-history">#conversation-history</a></td><td><a href="../../.gitbook/assets/YT (3).png">YT (3).png</a></td></tr></tbody></table>

## Agent History & Debugging Mode

**Agent History & Debugging**

Install this snippet to monitor, analyze, and debug your agent's behavior. Gain critical insight into every agent run.

* **Logging Database Tables**: Includes agents and agent\_runs, agent\_steps, agent\_tool\_calls tables to store detailed execution history.
* **Automated Logging Function**: A dedicated function to easily log the inputs, outputs, and steps of each agent run.
* **Monitoring Dashboard**: A utility API endpoint that provides a simple dashboard to review agent performance statistics and debug individual runs.

**Configuration Instructions**

{% stepper %}
{% step %}
### Install the snippet into you workspace by clicking the card below

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="image"></th></tr></thead><tbody><tr><td><strong>Agent History &#x26; Debugging Mode</strong></td><td>Monitors, analyzes, and debugs your agent’s behavior by logging every run, step, and tool call. Includes a dashboard for performance stats and run details, plus automated logging to capture inputs, outputs, and execution history.</td><td><a href="../../.gitbook/assets/YT.png">YT.png</a></td></tr></tbody></table>
{% endstep %}

{% step %}
### Go to the Agent History API group that was created during installation, and copy the group's Base URL

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-08 at 13.13.09.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### In the Dashboard API within the Agent History group, paste the Base URL into the api\_group\_base\_url variable, and then Publish the endpoint.

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-08 at 13.21.42.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### In your database, add a record to the Agents table for the agent you want to monitor.

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-08 at 13.22.28.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### In the agent\_user table, add a new user. This will provide secure access to the monitoring dashboard.

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-08 at 13.22.44.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### In any function stack, after your Call Agent statement, add the log\_agent custom function to capture the agent's response.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-08-08 at 13.25.45.png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

**Accessing the Dashboard**

Each agent run will be recorded in your database.

To view the monitoring dashboard:

* Open your browser and navigate to the URL of the dashboard endpoint.

Log in using the credentials you created in the agent\_user table.

## Conversation History

Install this snippet to manage and persist user interactions. It's the perfect starting point for any chatbot or conversational agent.

This snippet includes:

* Authentication endpoints (auth/login and auth/me)
* Database tables (conversations and messages, agent\_user)
* Chatbot API group
*   A chabot UI that you can use to test your agents.\


    <figure><img src="../../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

**Prerequisites**

* Agent must be configured with prompt type set to "Messages"
* Agent messages value must be set to: `{{ $args.messages|json_encode() }}`

<figure><img src="../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

**Configuration Instructions**

{% stepper %}
{% step %}
### Install the snippet to your workspace by clicking the card below

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th><th data-hidden data-card-cover data-type="image"></th></tr></thead><tbody><tr><td><strong>Conversation History</strong></td><td>Install this snippet to manage and persist user interactions. It's the perfect starting point for any chatbot or conversational agent.</td><td><a href="https://www.xano.com/snippet/pRD1obTe">https://www.xano.com/snippet/pRD1obTe</a></td><td><a href="../../.gitbook/assets/YT.png">YT.png</a></td></tr></tbody></table>
{% endstep %}

{% step %}
### Navigate to the Chatbot API group


{% endstep %}

{% step %}
### Copy the API group's base URL

<figure><img src="../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Navigate to the /chatbot endpoint


{% endstep %}

{% step %}
### Update the api\_group\_base\_url variable with the copied URL

<figure><img src="../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Navigate to the /conversation endpoint


{% endstep %}

{% step %}
### Add your agent using a Call AI Agent function within the group located at step 4

<figure><img src="../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### In step 5, update the agent\_response variable to use the Call AI Agent statement's output


{% endstep %}
{% endstepper %}

**Accessing the Chatbot Example**

To view the chatbot example:

* Open your browser and navigate to the URL of the chatbot endpoint.
