---
icon: key
---

# User Authentication & User Data

{% embed url="https://youtu.be/h8fGGaZInbo" %}

## How does authentication work in Xano?

Authentication in Xano is powered by industry-standard JWE (JSON Web Encryption) tokens.

Once a token is generated (typically after login or signup), your app or website will send that token back to Xano for requests that require authentication.

A token is generated using the [**Create Authentication Token**](../../the-function-stack/functions/security.md#create-authentication-token) function, and is typically used in conjunction with a standard login or signup authentication flow.

## How do I use authentication in Xano?

### Using Pre-generated Auth Endpoints

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

### Add Authentication Manually

{% stepper %}
{% step %}
### Enable Authentication on a Table

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
{% endstep %}

{% step %}
### Enable Authentication on an API

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
{% endstep %}
{% endstepper %}

## What do typical sign-up and login APIs look like?

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

## Extras

The extras payload is an optional setting that allows you to store additional information securely inside the token, such as a user role or other additional information.

{% hint style="info" %}
When testing endpoints with authentication enabled, the quick token generator will not include extras or any other customization present in your login or signup endpoints.
{% endhint %}

Extras are added as a part of the Create Authentication Token function, and are typically stored inside of a JSON object, shown below.

<figure><img src="../../.gitbook/assets/CleanShot 2025-07-23 at 10.34.05.png" alt="" width="323"><figcaption></figcaption></figure>

## Refresh Tokens

Refresh tokens are like spare keys for your online accounts. When a user logs in, they are issued an authentication token. This token eventually expires for security reasons, assuming you've specified an expiry time in your Create Authentication Token functions.

Once this token expires, additional user requests will fail and your frontend would probably redirect them back to the login screen. You can utilize refresh tokens to avoid having your users log in again, while maintaining the shorter expiry that is standard for an authentication token. It's a dance of logic between your backend and frontend to make this work as expected.

Below, you'll find a flowchart that details this process, and an interactive tutorial for how to add refresh token support to your Xano backend.

{% @arcade/embed flowId="R4QKSn4i8piWp5ZSIcar" url="https://app.arcade.software/share/R4QKSn4i8piWp5ZSIcar" %}

```mermaid
flowchart TD
    A[User Login] --> B{Valid Credentials?}
    B -->|No| C[Login Failed]
    B -->|Yes| D[Backend Generates Access Token and Refresh Token]
    D --> E[Frontend Stores Both Tokens]
    
    E --> F[User Makes API Request]
    F --> G[Frontend Sends Access Token]
    G --> H{Auth Token Close to Expiring?}
    
 
    
    H -->|Yes| K[Need New Auth Token]
   H -->|No| I[API Request Successful]
    I --> J[Continue Using App]
    J --> F

    K --> M[Frontend Sends Refresh Token to /refresh Endpoint]
    M --> N{Refresh Token Valid?}

    N -->|No - Expired| O[Redirect to Login]
    O --> A
    N -->|Yes| D
  

    

    
    style D fill:#e1f5fe
    style K fill:#ffebee
    style O fill:#ffebee
```

## Additional Notes

#### Alternative Authentication Headers

If you need to provide a secondary authentication header that takes precedence over the original Xano authentication, you can do so by sending the **X-Xano-Authorization-Only** header along with your requests. This will allow you to move the Xano authentication token to its own header, keeping the original standard **Authorization** header for something else.

You would want to utilize the **X-Xano-Authorization-Only** header if you are sending requests to your Xano APIs from another source that uses the **Authorization** header key for something else on both public and authentication required endpoints that are using the **Authorization** header for something other than Xano authentication.

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
