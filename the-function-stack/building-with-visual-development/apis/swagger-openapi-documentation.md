# Swagger (OpenAPI Documentation)

{% hint style="info" %}
**Quick Summary**

Swagger documentation provides a standardized way to describe and visualize APIs, showing what requests they accept and what responses they return - like a detailed menu that shows all available options. It allows developers to understand, test, and integrate with APIs without needing to read through pages of technical documentation.
{% endhint %}

Xano automatically generates documentation for your APIs using [Swagger](https://swagger.io/docs/), which provides the information in a standardized format called [OpenAPI](https://www.openapis.org/). The documentation contains information like the API name, description, inputs, and expected response.

Using these standardized methods allows for easy import of your API information into other platforms, such as your frontend of choice, as well as AI chatbots and large-language models for development assistance. In addition, it provides you an easy way to send API specifications to other developers you might be working with, without giving them access to the rest of your Xano workspace.

{% hint style="warning" %}
Please note that customized response structures may not be accurately displayed in your Swagger documentation. You can still use Swagger to its full extent in spite of this.
{% endhint %}

## Accessing the Documentation

Documentation is generated for each API group. At the top of the API group page, just click ![](<../../../.gitbook/assets/CleanShot 2024-12-26 at 09.16.30.png>) to access the auto-generated documentation for that group.

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-26 at 09.17.13.png" alt=""><figcaption><p>Locating the Swagger documentation</p></figcaption></figure>

## Using the Documentation

{% @arcade/embed flowId="QDBGCvxr0Jf6Fq6Uqtar" url="https://app.arcade.software/share/QDBGCvxr0Jf6Fq6Uqtar" %}

{% stepper %}
{% step %}
### Review the API information shown.

Each API will show you the method, the API name, and the description on the left side.\
![](<../../../.gitbook/assets/CleanShot 2024-12-26 at 11.48.54.png>)

On the right, you'll see a :unlock: icon if that API requires authentication.\
![](<../../../.gitbook/assets/CleanShot 2024-12-26 at 11.48.20.png>)

Click the **`V`** to interact with your API of choice.
{% endstep %}

{% step %}
### Sending Authenticated Requests

If any of the API(s) you want to interact with require authentication, click ![](<../../../.gitbook/assets/CleanShot 2024-12-26 at 11.51.24.png>)at the top of the page to supply an authentication token.
{% endstep %}

{% step %}
### Click ![](<../../../.gitbook/assets/CleanShot 2024-12-26 at 11.52.33.png>)to send a request to that API.


{% endstep %}

{% step %}
### Fill in any request body values or parameters necessary.

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-26 at 11.53.57.png" alt="" width="468"><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Click ![](<../../../.gitbook/assets/CleanShot 2024-12-26 at 11.54.39.png>) to send the test request.

You can review the response given below.

<figure><img src="../../../.gitbook/assets/CleanShot 2024-12-26 at 11.55.32.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

## Additional Features

### Copy / Copy as cURL

Throughout the documentation, you'll see ![](<../../../.gitbook/assets/CleanShot 2024-12-26 at 11.56.34.png>) icons. These will let you quickly copy the contents of that element, and in the presence of a cURL command, copy that command to quickly paste into a terminal or other API / testing platform of choice, such as [Postman](https://www.postman.com/).

### JSON OpenAPI Spec

<div align="left"><figure><img src="../../../.gitbook/assets/CleanShot 2024-12-26 at 11.58.03.png" alt="" width="218"><figcaption></figcaption></figure></div>

You can click the link at the top of the page to access a JSON-formatted version of your API spec. This is useful for other external platforms that rely on this type of standardized information about your APIs or providing to AI chatbots / LLMs.
