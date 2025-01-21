# Conditional

Conditional statements are used to determine what functions to run based on the outcome of an expression, or a set of expressions.

{% @arcade/embed flowId="FhWQsqxH5UlL7y89PGzV" url="https://app.arcade.software/share/FhWQsqxH5UlL7y89PGzV" %}

{% stepper %}
{% step %}
### Add a Conditional step to your function stack.


{% endstep %}

{% step %}
### Click <mark style="color:blue;">Add Condition</mark> to add a condition.

You can add multiple conditions to a single function stack if you want to check multiple values.

{% include "../../../.gitbook/includes/expression-builder.md" %}
{% endstep %}

{% step %}
### Once you have your conditions defined, add additional functions into your Then and Else blocks.

If the condition(s) evaluate as **true**, it will run the steps in the Then block.

If the condition(s) evaluate as **false**, it will run the steps in the Else block.

You can also leave either of these blocks empty if you only want to utilize one of them.
{% endstep %}
{% endstepper %}

