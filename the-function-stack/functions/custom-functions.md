# Custom Functions

## What are custom functions?

Custom functions are pieces of reusable logic that you can insert into other function stacks. This is most useful when you have a set of steps that remain the same, but need to be executed in multiple places. Placing those steps inside of a custom function allows you to quickly use those steps in other function stacks, while only needing to maintain them in one place.

### Using Custom Functions

{% @arcade/embed flowId="VGexEWGI0KkHspK9BMQH" url="https://app.arcade.software/share/VGexEWGI0KkHspK9BMQH" %}

{% stepper %}
{% step %}
**From the left-side navigation, click Library to access the Library section, and choose Functions from the submenu that appears.**
{% endstep %}

{% step %}
**To create a custom function, click &#x20;**<mark style="background-color:$primary;">**+ Add Function**</mark>&#x20;

Building a custom function is just like building an API. Refer to [that documentation](../building-with-visual-development/) for specific instructions on building the function stack.
{% endstep %}

{% step %}
**Publish your changes**

You can Publish the custom function to ensure that every place it is called uses the same version.

{% hint style="info" %}
**Hint**

When using Run & Debug, you have the option of running draft versions of functions as well, so you don't have to publish changes until you are ready.
{% endhint %}
{% endstep %}

{% step %}
**Insert the custom function any place you need to use it.**

In the functions panel, you'll see an option labeled Custom Functions, shown below. Just click it to see a list of your custom functions and add them to other function stacks.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-01-14 at 07.24.07.png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
**When you make changes to the custom function, the changes populate across everywhere it is used.**
{% endstep %}
{% endstepper %}

***

## Async Execution <a href="#async" id="async"></a>

{% include "../../.gitbook/includes/async-functions.md" %}
