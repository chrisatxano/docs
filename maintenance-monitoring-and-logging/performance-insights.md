---
description: >-
  Analyze the performance of most impactful functions to identify bottlenecks
  and optimize responsiveness
hidden: true
icon: chart-line-up
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Performance Insights

{% embed url="https://youtu.be/k2iH3wpqE9s" %}

## What can I see with Performance Insights?

Performance Insights enable you to analyze performance of specific function stacks or function types across your entire workspace. You'll be able to easily answer questions like:

* How long does a specific Lambda function take to run, on average, over the last 24 hours?
* What are my top 5 most resource intensive database queries?
* How many times did we run a bulk database operation over the last 30 days?

Performance Insights are the answer to every question you might have about how your backend in Xano is performing, and if it's not performing as expected, where to look to make improvements.

## How do I use Performance Insights?

From the **Library** tab in the left-hand navigation, select **Performance Insights**. Use the image below and the table to learn more about each section of the Performance Insights screen.

<figure><img src="../.gitbook/assets/pi (1).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="76.55859375" align="center" valign="middle">Key</th><th>What is it?</th><th>What's it for?</th></tr></thead><tbody><tr><td align="center" valign="middle"><strong>1</strong></td><td><div><figure><img src="../.gitbook/assets/CleanShot 2025-08-07 at 17.55.15@2x.png" alt=""><figcaption></figcaption></figure></div></td><td>Choose a period of time to view data from</td></tr><tr><td align="center" valign="middle"><strong>2</strong></td><td><div><figure><img src="../.gitbook/assets/CleanShot 2025-08-07 at 17.55.54@2x.png" alt="" width="112"><figcaption></figcaption></figure></div></td><td>Refresh available data</td></tr><tr><td align="center" valign="middle"><strong>3</strong></td><td><div><figure><img src="../.gitbook/assets/CleanShot 2025-08-07 at 17.56.27@2x.png" alt=""><figcaption></figcaption></figure></div></td><td>Choose the type of statistics returned.<br><br><strong>Average</strong> - The average execution time of that function or function stack in the selected period of time<br><br><strong>Count</strong> - The number of times the function or function stack was executed<br><br><strong>Total Time</strong> - The total time of all executions of the function or function stack in the selected period of time</td></tr><tr><td align="center" valign="middle"><strong>4</strong></td><td><div><figure><img src="../.gitbook/assets/CleanShot 2025-08-07 at 17.57.50.png" alt=""><figcaption></figcaption></figure></div></td><td>Hover over any part of the chart to see specific statistics about that time period. </td></tr><tr><td align="center" valign="middle"></td><td><div><figure><img src="../.gitbook/assets/CleanShot 2025-08-07 at 17.59.21.png" alt=""><figcaption></figcaption></figure></div></td><td>In some views, you'll be able to split the bar in the graph by function or function stack.</td></tr><tr><td align="center" valign="middle"><strong>5</strong></td><td><div><figure><img src="../.gitbook/assets/CleanShot 2025-08-07 at 17.59.55@2x.png" alt="" width="251"><figcaption></figcaption></figure></div></td><td>Filter the graph and list of data to show either individual function calls, or function stacks.</td></tr><tr><td align="center" valign="middle"><strong>6</strong></td><td><div><figure><img src="../.gitbook/assets/CleanShot 2025-08-07 at 18.04.02@2x.png" alt=""><figcaption></figcaption></figure></div></td><td>Filter the data by function types, or function stack types</td></tr><tr><td align="center" valign="middle"><strong>7</strong></td><td><div><figure><img src="../.gitbook/assets/CleanShot 2025-08-07 at 18.05.40@2x.png" alt=""><figcaption></figcaption></figure></div></td><td>In the list, you can click on the individual function or function stack to jump right to where it is in your workspace.</td></tr></tbody></table>
