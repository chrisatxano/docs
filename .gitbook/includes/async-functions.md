---
title: async functions
---

Once you've built your custom function and added it to another function stack, you have the option of running the function **asynchronously**. This just means that the functions will be queued for execution, and the rest of your function stack will continue to execute right away.

{% embed url="https://www.youtube.com/watch?v=-1wxYgc5i0U" %}

Asynchronous functions will utilize your background task resources (unless you are on a Custom or Enterprise plan), so it's important to manage expectations when it comes to execution speed. It would be most appropriate to use asynchronous functions when you need to trigger an operation as part of a larger function stack, but do not need to reference the output in the same stack.

Parallel execution of your async functions (running more than one async function at a time) is handled by **workers**, and the number of **workers** scales with each Xano plan. Async functions are placed into a queue and they get processed by available workers — the more workers you have available, the more parallel executions can run.&#x20;

## Enabling Async Execution

{% stepper %}
{% step %}
Right-click on the custom function in your function stack, and choose Async Settings.

![](https://docs.xano.com/~gitbook/image?url=https%3A%2F%2F3176331816-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-M8Si5XvG2QHSLi9JcVY%252Fuploads%252FTVQwgFKz56wtmn2bRbQQ%252FCleanShot%25202024-09-04%2520at%252009.57.21.png%3Falt%3Dmedia%26token%3D8b8bbf39-f568-4bad-821a-cf9faffe8552\&width=768\&dpr=4\&quality=100\&sign=3a825ef\&sv=2)
{% endstep %}

{% step %}
In the panel that opens, choose your desired execution type.

* **Synchronous** is standard execution. Your function stack will allow the custom function to finish executing before continuing.
* **Async** and **Async (dedicated)** allow for running custom functions in the background while the rest of the function stack continues to execute.

<div align="left"><figure><img src="../assets/image (107).png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

## Types of Async Execution

{% stepper %}
{% step %}
**Async**

This option runs your functions asynchronously using your background task resources. Performance may vary based on other tasks being executed and the Xano plan you are currently on.
{% endstep %}

{% step %}
**Async (dedicated)**

This option is available for our [Custom and Enterprise plans](broken-reference). It enables you to utilize dedicated resources to execute your custom functions asynchronously, and to specify the volume of resources to use. \
\
On a Custom or Enterprise plan, you have enhanced functionality to leverage these on-demand resources (instead of your background task resources) for each worker. Each function gets their own dedicated worker, with no queueing system. This allows you to support scenarios like parallel processing with thousands of workers, if necessary.

When choosing **Async (dedicated)**, you'll have four options of resource allocation:

| <div><figure><img src="../assets/image (106).png" alt=""><figcaption></figcaption></figure></div> | <p></p><ul><li><strong>Small</strong> - Good for small operations with just a few data points or quick transformations</li></ul><ul><li><strong>Medium</strong> - Handles more moderate workloads, such as working with a few hundred data points</li></ul><ul><li><strong>Large</strong> - For larger datasets, such as working with thousands of points of data or database records</li></ul><ul><li><strong>Custom</strong> - Allows you to define your own resource allocation if you have specific requirements</li></ul> |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
{% endstep %}
{% endstepper %}

When using async functions, the function request history will still populate, so you can review the requests once they have finished executing. Each request will be labeled with the execution method.

![](https://docs.xano.com/~gitbook/image?url=https%3A%2F%2F3176331816-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-M8Si5XvG2QHSLi9JcVY%252Fuploads%252F2WwVUhi42A6C64FSwcyz%252FCleanShot%25202024-09-04%2520at%252010.02.02.png%3Falt%3Dmedia%26token%3D03f12d88-c0f9-4db5-a237-c4abb1a534b9\&width=768\&dpr=4\&quality=100\&sign=4910475a\&sv=2)

# Using Async Function Await

This function allows you to retrieve the output of a custom function executed asynchronously.&#x20;

{% stepper %}
{% step %}
## Insert a custom function into your function stack.

If you haven't built any custom functions yet, you can review our documentation on them [here](../../the-function-stack/functions/custom-functions.md).
{% endstep %}

{% step %}
## Click ![](<../assets/CleanShot 2025-02-13 at 08.00.40.png>)on the function to change the execution mode.


{% endstep %}

{% step %}
## If necessary, retrieve the output of the async function.

If a function is set to async, it will return an ID that represents that execution, similar to the value shown below.

```
6f10cc09-d3e0-4ead-9a98-a0bc66bbe673
```

You can use the **Async Function Await** function to retrieve the output of the function once execution completes. Just provide it with an array of the ID(s) returned when the function runs.

<div align="left"><figure><img src="../assets/CleanShot 2025-02-13 at 08.03.59.png" alt="" width="485"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

### &#x20; <a href="#async-function-await" id="async-function-await"></a>
