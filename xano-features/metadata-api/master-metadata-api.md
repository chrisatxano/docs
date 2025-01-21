# Master Metadata API

The master Metadata API allows you to browse and retrieve Instances of an account associated with a Personal Access Token. It is especially useful for displaying an account's different Instances in a UI.

The master Metadata API Swagger documentation can be accessed by the following URL:

{% hint style="info" %}
**https://app.xano.com/api:meta**
{% endhint %}

### Instance

<figure><img src="../../.gitbook/assets/CleanShot 2023-05-22 at 14.28.26.png" alt=""><figcaption></figcaption></figure>

#### GET /instance/{name} - Get Single Instance

The GET request will provide details of a specific instance when provided the instance name

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/instance/{name}" method="get" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}

#### GET /instance - Browse Instances

The GET request will provide a list of Instances associated with an account.

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/instance" method="get" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}

* The response provides both the Xano domain and the custom domain (if applicable).
* The meta\_api value will provide access to the Metadata API for the given Instance.
* The JSON of the Metadata API Swagger for the Instance is also provided.

### Snippet / Token

These endpoints provide functionality for managing private snippet access tokens.

<figure><img src="../../.gitbook/assets/CleanShot 2023-05-22 at 14.30.39.png" alt=""><figcaption></figcaption></figure>

For reference, the **canonical ID** of your snippet is found at the end of the URL.&#x20;

```
https://www.xano.com/snippet/abC123Zx/
```

In this example URL, **abC123Zx** is our canonical.

#### POST /snippet/{canonical}/token/{token]

Use this endpoint to update a token's allowed number of installations.

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/snippet/{canonical}/token/{token}" method="post" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}

#### DELETE /snippet/{canonical}/token/{token}

Use this endpoint to delete an access token from a snippet.

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/snippet/{canonical}/token/{token}" method="delete" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}

#### GET /snippet/{canonical}/token

Use this endpoint to get a list of tokens for a snippet.

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/snippet/{canonical}/token" method="get" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}

#### POST /snippet/{canonical}/token

Use this endpoint to create a new token for a snippet.

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/snippet/{canonical}/token" method="post" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}

### Snippets

#### GET /snippet/{canonical}

Retrieve a specific snippet by its canonical ID

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/snippet/{canonical}" method="get" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}

#### POST /snippet/{canonical}

Update settings on the snippet, such as the access method and access description.

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/snippet/{canonical}" method="post" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}

#### GET /snippet

List all snippets owned by the authenticated user.

{% swagger src="../../.gitbook/assets/apispec_meta.json" path="/snippet" method="get" %}
[apispec_meta.json](../../.gitbook/assets/apispec_meta.json)
{% endswagger %}
