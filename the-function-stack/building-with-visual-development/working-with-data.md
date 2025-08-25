# Working with Data

## Understanding Working with Data

When we talk about working with data in Xano, we are referring to anything that touches a piece of data in your workflows — whether it is an API, custom function, task, or anything else. Data will typically always be passing through these workflows, and it's important to understand the various ways you can access and interact with this data.

## Database vs Variables

The **database** is used to store information that you will need to recall again later, and across workflows, such as:

* User accounts
* Product and order information
* Blog posts or comments

**Variables** are used inside of individual workflows to store information temporarily that you only need to finish the set of functions being executed, such as:

* The current date / time
* Data from a database that needs temporary manipulation or transformation, such as combining a first and last name or calculating a discount
* The output of individual functions in a function stack, like getting a record from a database table

**Dot Notation** is how you'll reference keys inside of objects, or specific items in an array, inside of Xano. You may have done this previously in other tools using a format like the ones listed in the table below.

Xano's dot notation uses periods to represent traversal in an object. For example, if you have an object called `product` with a key called `price`, you'd use `product.price`

| Platform / Tool         | Example Object                               | How to Reference "price"                              | Notes                                                                                    |
| ----------------------- | -------------------------------------------- | ----------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **Xano**                | `{"product": {"name": "apple", "price": 5}}` | `product.price`                                       | Standard dot notation.                                                                   |
| **Bubble**              | `{"product": {"name": "apple", "price": 5}}` | `Current cell's product's price`                      | Bubble uses a "drill-down" syntax with apostrophes and natural language style.           |
| **Airtable (formula)**  | `{"product": {"name": "apple", "price": 5}}` | `product.price` (in scripts) OR `{Price}` (in tables) | In scripts, it’s dot notation. In formulas/views, it’s field reference wrapped in `{ }`. |
| **Zapier (JSON paths)** | `{"product": {"name": "apple", "price": 5}}` | `product__price`                                      | Nested keys are flattened with `__`.                                                     |
| **Integromat / Make**   | `{"product": {"name": "apple", "price": 5}}` | `product[price]`                                      | Uses bracket notation inside functions/macros.                                           |
| **n8n**                 | `{"product": {"name": "apple", "price": 5}}` | `{{$json["product"]["price"]}}`                       | Requires explicit JSON path inside double-braced expression.                             |
| **Retool**              | `{"product": {"name": "apple", "price": 5}}` | `product.price`                                       | Standard JavaScript dot notation since Retool runs JS under the hood.                    |
| **Glide**               | `{"product": {"name": "apple", "price": 5}}` | `product.price` OR use computed column                | Glide inherits Google-Sheets style, but in computed columns it follows dot notation.     |
| **Appsmith**            | `{"product": {"name": "apple", "price": 5}}` | `{{product.price}}`                                   | JS evaluation inside double braces.                                                      |

## Data in Functions

Most functions that you can add to a function stack will have some kind of output available. The output of these functions are stored in a **variable**.

In the screenshot shown below, we are using a get record function to retrieve a record from our `author` table. On the right side of that function, take note of return as <mark style="color:orange;">**author1**</mark>. This is the variable that the record we retrieve is stored in, and what we will use to get that data in subsequent functions.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-10 at 09.45.20.png" alt=""><figcaption></figcaption></figure>

When we add another function, we can reference <mark style="color:orange;">**author1**</mark> as shown below.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-02-10 at 09.49.14.png" alt="" width="334"><figcaption></figcaption></figure></div>

## Data in Filters

Filters are like mini-functions that can ride alongside other functions in your function stack. They are used to perform a wide array of tasks against a piece of data.

Our current function stack does nothing but retrieve a record from our `author` table.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-10 at 09.51.30.png" alt=""><figcaption></figcaption></figure>

Let's transform this data by changing the author's name to uppercase. The simplest of data transformation happens in an **Update Variable** function. Try it for yourself below.

{% @arcade/embed flowId="uyjNpHs3rAIK0XAkko84" url="https://app.arcade.software/share/uyjNpHs3rAIK0XAkko84" %}

## Changing Variable Names

As you build your function stacks, you'll want to ensure you are naming variables appropriately, so you can understand what they contain.

When adding a function, you'll usually have the option to set the variable name.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-02-10 at 10.12.32.png" alt="" width="396"><figcaption></figcaption></figure></div>

If you need to change the variable name after you've already referenced the data elsewhere, Xano will ask you if you want to update the references to that variable. In the below screenshot, after changing the <mark style="color:orange;">**author1**</mark> variable name, Xano lets us know that the variable is already referenced in an **Update Variable** step, and in our response. Click ![](<../../.gitbook/assets/CleanShot 2025-02-10 at 10.15.14.png>)to automatically change all of these to reflect the new variable, or click <mark style="color:red;">Skip</mark> to leave them the same. If you aren't sure which option to choose, more often than not, you'll want to update the references.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-02-10 at 10.14.08.png" alt=""><figcaption></figcaption></figure></div>
