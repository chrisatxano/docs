# When a single workflow feels slow

## When a single API Endpoint feels slow

### 1. Look at the response times in the Debugger

**Start by finding the API endpoint that is causing issues.**

When the Function stack is executed within Xano, you'll be able to see each statement's response time.

**Example**

This API endpoint takes a Star Wars planet name and returns information about the planet using the Star Wars API (swapi.dev). They don't have an API that searches a planet by name so this function stack has to recursively loop through the returned planets and match up the user's request.&#x20;

#### **Debugging the screenshot below** <a href="#functionvstatement" id="functionvstatement"></a>

A. There are technically **three (3)** items in the function stack.

B. After you click **Run & Debug**, click the debugger tab to see the results and response times.

C. You'll see that while there were only three functions, **14 statements got executed.** This is because Function 3 is a For Each loop that goes through each result of what is returned by the API and creates a variable.

D. You'll see that the total response time is **5.39s** which is quite long for a response, however you can also see in Line 1 of the Debugger that the Star Wars API request is taking 5.37 seconds to return a response. Xano's execution of the request happens much faster.



<figure><img src="../../.gitbook/assets/CleanShot 2022-09-12 at 15.26.54.png" alt=""><figcaption></figcaption></figure>

If you have already addressed efficiency concerns in your database and function stacks as detailed in [how to improve your API response time](function-stack-performance.md), the next step is to upgrade your Xano plan for improved performance.

## Contacting Support
