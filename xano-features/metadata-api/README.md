# Metadata API

{% hint style="info" %}
The Metadata API is in beta and is subject to changes including access.
{% endhint %}

The Metadata API (Beta) enables you to interact with your Xano workspace schema and content programmatically. The Metadata API includes a comprehensive collection of API endpoints designed to add and modify database tables, schemas, and more.

To find the Metadata API Swagger Documentation, select the style to open the Instance settings panel and select **Metadata API**.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 15.16.20.png" alt=""><figcaption><p>Open Instance settings.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 15.17.24.png" alt=""><figcaption><p>Select Metadata API.</p></figcaption></figure>

It can be accessed by entering your Instance domain appended by **/api:meta**. For example:

Instance domain:

<pre><code><strong>https://xabc-1yz2-abcd.xano.io
</strong></code></pre>

Metadata API Swagger documentation:

```
https://xabc-1yz2-abcd.xano.io/api:meta
```

Using the Metadata API will update your Xano database in real time. For example, if you modify content in a database table via the Metadata API, the change will be reflected immediately without needing to refresh.

The Metadata API is flexible regarding sending input values. It allows you to not need to send everything when making an update. For example, if you are updating a schema and want to just update the name then you can only send the updated name and the other metadata of the schema will remain unchanged.&#x20;

{% hint style="success" %}
For implementations wanting an easier way to integrate, it may be useful to start out with the Master Metadata API below. This way the only prompt from the user will be to get their access token, and then you use the Master Metadata API to get the Metadata API for the chosen instance.
{% endhint %}

## Master Metadata API

The [Master Metadata API](./#master-metadata-api) is useful for listing Instances of an account in a UI. It has the ability to browse Instances or retrieve a specific Instance. The Swagger documentation can be accessed at the following URL:

```
https://app.xano.com/api:meta
```

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-21 at 09.57.47.png" alt=""><figcaption><p>Master Metadata API for browsing and retrieving Instances.</p></figcaption></figure>

## Authentication

### Personal Access Token

The Metadata API requires a Personal Access Token to authenticate.&#x20;

You can create up to 10 Personal Access Tokens, which can be given different [scopes](./#scopes) to create, read, update, or delete via the Metadata API. Personal Access Tokens will also obey permissions from [RBAC](../../team-collaboration/role-based-access-control-rbac.md) settings (premium add-on). For example, if you don't have access to the database via RBAC then neither will your Personal Access Token. A read-only scope is available, which is especially useful for a 3rd party application you want to give access to but need to restrict edits, deleting, or creating content.&#x20;

{% hint style="warning" %}
Personal Access Tokens represent your account. Make sure use the appropriate [scopes](./#scopes) are used. Do not give out Personal Access Tokens without ensuring proper intent for them to be used.
{% endhint %}

Personal Access Tokens can be created from the [Account page](https://app.xano.com/admin/account) by selecting **Manage Access Tokens**.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 15.19.06.png" alt=""><figcaption><p>Select Manage Access Tokens from the Account page.</p></figcaption></figure>

Next, click **+ New Access Token**.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 15.22.02.png" alt=""><figcaption><p>Create a New Access Token.</p></figcaption></figure>

Provide the token with a name and optionally deactivate scopes. [Scopes](./#scopes) are like permissions for the tokens, by default, the token will have full access.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-21 at 09.47.26.png" alt=""><figcaption><p>Optional scopes for the token.</p></figcaption></figure>

{% hint style="warning" %}
Once created, the token will be shown. **The token will only be shown once, so be sure to copy it and store it securely.**&#x20;
{% endhint %}

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 15.27.02.png" alt=""><figcaption><p>Copy the token and secure it in a safe place.</p></figcaption></figure>

### Scopes

Scopes are like permissions for the token. They define what access the token has with the Metadata API. By default, all scopes are selected meaning the token has full access. The scopes can be customized for the following objects:

**Workspace Content** - Database records. (API Endpoints in the **table/content** group.)

**Workspace Database** - Database tables, schema, and indexes.

**Workspace Files** - Files and media.

**Workspace Request History** - API Request History.

The scope permissions for each object include:

* Create - permission for the token to create the specified object.
* Read - permission for the token to read the specified object.
* Update - permission for the token to update or modify the specified object.
* Delete - permission for the token to delete the specified object.

### Authorize

Once you have an access token, use the Authorize button in Swagger to enter the token and authenticate in order to use the Metadata API.

#### Swagger

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-12 at 14.36.21.png" alt=""><figcaption></figcaption></figure>

Enter the token and select Authorize.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-12 at 14.37.20.png" alt=""><figcaption></figcaption></figure>

#### Header - Authorization: Bearer

When setting up the calls to the various API Endpoints of the Metadata API outside of Swagger, authentication follows the Authorization: Bearer method in the request header. For example:

```
Authorization: Bearer <PERSONAL_ACCESS_TOKEN>
```

### /auth/me

Validate the Access Token and identify the account details.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 19.07.21@2x.png" alt=""><figcaption></figcaption></figure>

## File

Interacts with the files and media of a workspace.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-21 at 11.01.11.png" alt=""><figcaption></figcaption></figure>

## Request History

Interacts with the API Request History of a workspace.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-21 at 10.17.47.png" alt=""><figcaption></figcaption></figure>

## Table/Content

Interacts with the content (database records) of a database table.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-21 at 10.14.43.png" alt=""><figcaption></figcaption></figure>

## Table/Index

Interacts with the indexes of a database table.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 19.02.10@2x.png" alt=""><figcaption></figcaption></figure>

## Table

Interacts with database tables of a workspace.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 19.03.50@2x.png" alt=""><figcaption></figcaption></figure>

## Table/Schema/Type

Creates the various schema types available for a workspace table.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-21 at 10.15.47.png" alt=""><figcaption></figcaption></figure>

## Table/Schema

Reads, updates, and deletes the schema of a database table.

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-11 at 19.06.10@2x.png" alt=""><figcaption></figcaption></figure>
