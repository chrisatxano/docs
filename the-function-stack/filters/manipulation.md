# Manipulation

## fill

Creates an array of a certain size with a default value.

<figure><img src="../../.gitbook/assets/CleanShot 2025-01-14 at 08.55.41.png" alt=""><figcaption></figcaption></figure>

## fill\_keys

Creates an array of a certain size with a default value and a list of keys.

<figure><img src="../../.gitbook/assets/CleanShot 2025-01-14 at 08.57.09.png" alt=""><figcaption></figcaption></figure>

## first\_notempty

Applies the first value that is not **empty** (0, null, "", empty string)

Useful if you need to determine a value to apply based on what is provided, such as editing a database record and being uncertain if an input will be provided to replace a value.

## first\_notnull

Applies the first value that is not **null**

Useful if you need to determine a value to apply based on what is provided, such as editing a database record and being uncertain if an input will be provided to replace a value.

## get

Gets a piece o data at a specified path, and returns a default value if it is not defined.

As an example, let's use the following object, stored in a variable called <mark style="color:orange;">**author**</mark>

```
{
    "name": "John Smith"
    }
```

We can see that this author does not have a defined genre, but maybe we are searching for books that are in the same genre this author writes.

If we try and retrieve the genre, we will encounter an error.

Instead, we can use the Get filter to specify a default value to work with.

<figure><img src="../../.gitbook/assets/CleanShot 2025-01-14 at 09.05.36.png" alt=""><figcaption></figcaption></figure>

## has

Similar to **get**, this checks if a value is present, but only returns a true or false

## set

Use **set** to set a value at a specific location inside of an object.

<figure><img src="../../.gitbook/assets/CleanShot 2025-01-14 at 09.12.18.png" alt=""><figcaption></figcaption></figure>

## set\_conditional

Use set\_conditional to set a new value in an object based on whether a condition evaluates as true.

{% @arcade/embed flowId="CxgMoWBBckff0sO4P3ik" url="https://app.arcade.software/share/CxgMoWBBckff0sO4P3ik" %}

## set\_ifnotempty

Sets a new value in an object if the value provided is not empty. An empty value can be 0, `null`, or an empty string.

## set\_ifnotnull

Sets a new value in an object if the value provided is not `null`

## transform

{% hint style="info" %}
This filter is similar to the [map filter](../functions/apis-and-lambdas/lambda-functions/#what-are-lambda-functions), except it can bind to all data - not just an array.
{% endhint %}

The `transform` filter is universal way to transform data. It works with arrays, objects, and scalar values.

Arguments

* expression - the expression being used to transform `$$`.&#x20;

Context  Variables

* **\$$** - the context variable that represents the element of the array being processed.

Read more about expressions and Xano Transform below.

{% content-ref url="../data-types/expression.md" %}
[expression.md](../data-types/expression.md)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}



#### Examples

```json
[1,2,3]|transform:($$|count)          // 3
[1,2,3]|transform:($$|count)+($$|sum) // 9

{first:Alpha,last:Beta}|transform:$$.first~" "~$$.last
// Alpha Beta
```

## unset

Removes a key from an object.























