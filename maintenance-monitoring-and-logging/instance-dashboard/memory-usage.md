# Memory Usage

### What's RAM used for in my Xano instance?

RAM is essentially temporary memory that your backend uses to hold on to data it needs to perform a specific task. This could be anything from simply building in Xano, to functions run when an API is called, to loading and editing database tables.

<figure><img src="../../.gitbook/assets/CleanShot 2024-11-21 at 08.59.19.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Remember, you can click the labels at the bottom of the graph to review usage for specific components of your Xano instance, such as only reviewing Database or API usage.
{% endhint %}

### Understanding RAM Usage

It is **vital** to understand that **high RAM usage does not necessarily indicate a problem**.

Think of RAM like a desk surface where you're working. Having most of your desk occupied with papers and materials doesn't mean you're disorganized - you might just be using the space efficiently for your current task. Similarly, your Xano instance is designed to use available RAM to run smoothly, keeping  needed data readily accessible. Just like an empty desk doesn't necessarily mean you're more productive, unused RAM doesn't automatically mean better performance.

Let's look at an example.

<figure><img src="../../.gitbook/assets/image (45).png" alt="" width="563"><figcaption></figcaption></figure>

In this screenshot, we can see a usage graph showing Database RAM is almost at 100%. **This is okay.** What we should be focusing on is the consistency. All this tells us is that the database is using as much RAM as it can to do the job it needs to be doing at a steady pace. Everything looks good!

Let's look at another example where we might have a problem.

<figure><img src="../../.gitbook/assets/image (46).png" alt="" width="563"><figcaption></figcaption></figure>

In this screenshot, we can see that this instance's Lambda RAM isn't showing steady utilization -- there are significant peaks, valleys, and spikes. This tells us that there is sporadic intense load with Lambda functions we are using, and it will likely cause problems such as:

* Temporary system restarts and downtime
* Slow performance
* Failed requests

This is something that should be investigated further.

### Reducing RAM Usage

If you are finding yourself in a situation where you are experiencing symptoms of RAM exhaustion, there are a few things you can to do try and mitigate the situation.&#x20;

It's important to note that in some cases, when mitigation is not possible, that may signal it's time to upgrade your Xano subscription tier to increase your available RAM. You can always reach out to Xano Support for further clarification.

#### Database RAM

Spikes in Database RAM can be caused by one or more of the following:

* Tables that contain fields with large amounts of data, such as JSON payloads or sizable text content
  * Try moving these large fields to a separate table or determining if you can reduce the amount of data stored.
  * Depending on how often the data needs to be accessed, you can also store the large data in text files and store the file path in the table instead.
* Table references to other tables with a high number of fields
  * Use the [Auto Complete](broken-reference) setting on the referenced table to reduce the amount of data loaded when viewing the table
* Running queries with joins on large tables
  * Make sure you are using proper [indexing](broken-reference) on large tables
  * Use pagination on your base query

#### API RAM

Spikes in API RAM can be caused by one or more of the following:

* Function stacks that process large volumes of data
  * Clear the contents of variables as they become unnecessary by updating them to blank values
  * Move large data processing jobs to [background tasks](broken-reference)
  * Use post processing to execute any functions that aren't necessary to deliver a response

#### Lambda RAM

{% hint style="warning" %}
Please note that when using Lambda functions, the contents of **all variables** are loaded into Lambda memory. This is most often the cause of memory issues when using Lambda functions.
{% endhint %}

Spikes in Lambda RAM can be caused by one or more of the following:

* Contents of other variables are too large for the Lambda to handle during processing
* Using file resources in conjunction with Lambdas

To mitigate issues with Lambda RAM, try using [expressions](broken-reference) instead.

#### Redis RAM

Spikes in Redis RAM can be caused by one or more of the following:

* Heavy and/or inappropriate reliance on data caching functions

If you are not using data caching functions and still experiencing spikes in Redis RAM, please reach out to support.

#### Tasks RAM

Spikes in task RAM should be handled as you would handle spikes in API RAM.













