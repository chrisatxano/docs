# User Authentication & User Data

## **Enable Authentication for a Table**

Authentication starts with enabling the function on a table that contains user data. Typically, this would just be your `user` table. You can also enable authentication on multiple tables if you want separate authentication methods for different user groups, such as normal users and administrators.

{% stepper %}
{% step %}
### Click the ![](<../../.gitbook/assets/CleanShot 2025-02-05 at 09.07.38.png>) icon in the database table view and choose Settings.


{% endstep %}

{% step %}
### Use the dropdown to enable authentication.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-05 at 09.08.12.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

## **Enable Authentication on an API Request**

Once you've enabled authentication on a table, you can use each API endpoint's settings to note whether or not it requires authentication.

When a request is sent to API endpoints that require authentication, an authorization token is sent in the headers of the request, which Xano checks against the table with authentication enabled, before allowing the request to continue.

{% hint style="info" %}
Still need a primer on the basics of an API? Read more [here](../../before-you-begin/key-concepts.md#api).
{% endhint %}

{% stepper %}
{% step %}
### Click  ![](<../../.gitbook/assets/CleanShot 2025-02-05 at 09.09.10.png>) to access the settings of the API you'd like to enable authentication on.


{% endstep %}

{% step %}
### Enable authentication for the endpoint in the dropdown.

This dropdown will list each table that you have authentication enabled on. Select the table you enabled authentication on.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-05 at 09.16.01.png" alt=""><figcaption></figcaption></figure>

Once an API has authentication enabled, it will require an authentication token to be sent in the headers of the request.
{% endstep %}
{% endstepper %}

## How does authentication work?

Authentication in Xano is powered by industry-standard JWE (JSON Web Encryption) tokens.

Once a token is generated (after login or signup), your app or website will send that token back to Xano for requests that require authentication.

A token is generated using the [**Create Authentication Token**](../../the-function-stack/functions/security.md#create-authentication-token) function, and is typically used in conjunction with a standard login or signup authentication flow.

## Adding Pre-built Authentication Endpoints

{% stepper %}
{% step %}
### Create an API group to hold your authentication endpoints.


{% endstep %}

{% step %}
### Click ![](<../../.gitbook/assets/CleanShot 2025-02-05 at 09.41.29.png>)and choose Authentication to pick from the pre-built API endpoints.


{% endstep %}

{% step %}
### Choose the API that you'd like to add.

* **Login**
  * Accepts an email or username and password, and allows a user to log in
* **Signup**
  * Accepts user information and creates an account for them
* **auth/me**
  * Checks an authentication token and returns user information
{% endstep %}
{% endstepper %}

## Building Sign-up and Login APIs

Below, you can review a **typical** login and signup flow — you are free to modify them to suit your needs. These are the same that Xano can add for you during signup

### Login

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-05 at 09.36.26.png" alt=""><figcaption></figcaption></figure>

{% stepper %}
{% step %}
### Get Record From `user`

First, we need to retrieve the record of the user trying to login.
{% endstep %}

{% step %}
### Precondition: `user ≠ null`

We use a precondition step to check if a user record was returned in step 1. If it wasn't, we return an error and halt execution.
{% endstep %}

{% step %}
### Validate Password

Because passwords stored in a Xano database are hashed and not human readable, we use a Validate Password function to check what the user has submitted against the password stored in the database. This function returns a `true` or `false` depending on the result.
{% endstep %}

{% step %}
### Precondition: `pass_result = true`

We use another precondition step to check if the password was successfully validated. If not, we return an error and halt execution.
{% endstep %}

{% step %}
### Create Authentication Token

Finally, all checks are passed, and we create and return the authentication token.
{% endstep %}
{% endstepper %}

### Signup

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-05 at 10.01.31.png" alt=""><figcaption></figcaption></figure>

{% stepper %}
{% step %}
### Get Record From `user`

Checks if a user record already exists with the provided information.
{% endstep %}

{% step %}
### Precondition: `user = null`

Checks to see if there is a user record returned in step 1. If so, we halt execution and return an error
{% endstep %}

{% step %}
### Add Record In `user`

Add a new record for the user in the `user` table
{% endstep %}

{% step %}
### Create Authentication Token

Creates an authentication token to be used in future API requests.
{% endstep %}
{% endstepper %}

#### **What is an Authentication Token?**

An Authentication token is a JWE (JSON Web Encryption) token. \
In short, this is the industry standard for securely storing information into an encrypted token.

#### How do I Retrieve an Authentication Token?

This happens either by login or signup. The [default login/signup endpoints](broken-reference) verify an email and password, if there is a successful match, then an Authentication token is returned. The business logic on how to enforce proper authentication can be customized to whatever your specific requirements are, but once you have determined the user has validated their account credentials, then the “Create Authentication Token” [Function Stack](broken-reference) statement comes into play.

For example, this Function Stack statement below, Create Authentication Token, has the following inputs:

* **id** - this is the primary key for the table you are using for Authentication. Normally, this is the user table. So, if you just logged in with your account and your account happens to be id = 20, then 20 would be inputted here.
* **dbtable** - this is the actual name of your table being used for Authentication. Normally, this is “user” but if you renamed the table or have multiple tables being used for Authentication, then this needs to match that name exactly.
* **extras** - this is an advanced concept explained below.
* **expiration** - this is the amount of time in seconds that this Authentication token is valid. 86400 would be 1 day in seconds. You can set this value to 0 if you want the token to never expire.

<figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption><p>In this example, the Create Authentication Token Function is displayed. </p></figcaption></figure>

By default the Authentication token stores the id of the object you authenticated against. If you have a user table and authenticate user 20, then inside the token, the number 20 is stored, which you can retrieve through the auth.id variable.

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption><p>In this example, we can see the user id is stored within the Auth variable.</p></figcaption></figure>

#### Extras

The extras payload allows you to store additional information securely inside the token. This allows you to reliably use that data without having to store it in a database. Only once you decode the token, can you have access to the data. \
NOTE: Storing data inside the token causes the token to grow in size, so make sure to use it sparingly.

An example of utilizing extras is whether or not you wanted to restrict access to a specific API endpoint for administrators only. Let’s assume on your user database table, you have a text field called “role”. If the value of that field is “administrator”, then that means you are an administrator.

So, if you wanted to check if the authenticated user was an administrator, then you would need to load the user object and then check. It would be very convenient if you could just skip that step and rely on that “role” field just being available the same way the authenticated user id is available.

Here is how you could use extras to store the user role.&#x20;

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption><p>In this example, in the Create Authentication Token function we updated extras to include the user role in Authentication token.</p></figcaption></figure>

To continue this example, now that the role is stored inside the token, you can access it. Here is a [precondition](broken-reference), which enforces that something is true to continue, enforcing administrator access.

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption><p>Here we are setting the conditions of the precondition statement. This is saying that in the Authentication Token, in the extras payload, find role and it must equal "administrator."</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption><p>Now that we have set the required conditions, we can choose the error type and write an error message for if the precondition is not met. </p></figcaption></figure>

{% hint style="info" %}
_\*The easy authToken retrieval will not include any extras you create in a sign-up or login API endpoint. This is because the easy authToken retrieval does not mimic the logic of these endpoints where the extras are created. But rather it's for quick testing purposes only. If you need to test an authToken containing extras then you must run the endpoint where the extras are created then copy the outputted authToken and paste it in the header of the authenticated endpoint._&#x20;
{% endhint %}

#### Alternative Authentication Headers

If you need to provide a secondary authentication header that takes precedence over the original Xano authentication, you can do so by sending the **X-Xano-Authorization-Only** header along with your requests. This will allow you to move the Xano authentication token to its own header, keeping the original standard **Authorization** header for something else.

You would want to utilize the **X-Xano-Autborization-Only** header if you are sending requests to your Xano APIs from another source that uses the **Authorization** header key for something else on both public and authentication required endpoints that are using the **Authorization** header for something other than Xano authentication.

**Example:**

<pre><code><strong>// For a public Xano endpoint that sends an Authorization header
</strong><strong>curl "http://localhost:9999/api:elnQNVvy:v1/public_test" \
</strong>-H "X-Xano-Authorization-Only: true"

// For a private (authenticated) Xano endpoint that receives an Authorization header
that is not a Xano auth token
curl "http://localhost:9999/api:elnQNVvy:v1/private_test" \
-H "X-Xano-Authorization: Bearer ey...." \
-H "X-Xano-Authorization-Only: true"
</code></pre>
