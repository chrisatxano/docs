# Microservices

{% hint style="success" %}
The Microservice feature is an additional add-on. Please contact your Xano representative or support for details.&#x20;
{% endhint %}

Xano can host 3rd party microservices using Kubernetes, which is the same infrastructure and architecture that powers Xano and makes it possible to scale.&#x20;

Xano provides an [admin panel](microservices.md#microservice-management-center) to configure all aspects of these microservices, including CPU/RAM/GPU resources, persistent storage, load balancing, and network port mapping. Each microservice is isolated internally within the Xano instance and accessible through the Xano function stack.

The following details include how to [create a deployment](microservices.md#deployments-deploy-a-microservice) a microservice and how you can [interact with a microservice](microservices.md#using-a-microservice-in-the-function-stack) via the Function Stack.

## Microservice Management Center

When the microservice feature is enabled, click the menu icon on the instance to access the microservice management center.

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-28 at 14.48.08.png" alt=""><figcaption></figcaption></figure>

From the Microservice Management Center, you can manage:&#x20;

* [Deployments](microservices.md#deployments-deploy-a-microservice)
* [Persistent Volumes](microservices.md#persistent-volumes)
* [Configs](microservices.md#configs)
* And monitor the [Status](microservices.md#status) of deployed microservices

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.21.51.png" alt=""><figcaption></figcaption></figure>

### Deployments: Deploy a Microservice

To create a deployment a Docker Image is required; Docker Images are either publicly available or through a private repository.&#x20;

In the below example, a public Docker Image is shown. The example uses an echo server, which like its name allows you to send something to it and it will send it back.&#x20;

#### Deployment

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.32.43.png" alt=""><figcaption></figcaption></figure>

* **Name** - the name of the microservice deployment (this will be used to identify the microservice in the Function Stack).
* **Replicas -** number of copies of the docker image - a Replica tends to be considered equivalent to a server. Replicas are load balanced, which means that if you have the same API request more than once, it will be distributed to different Replicas. Your application must be tolerant of such a configuration. (_Typically, it is recommended to keep Replicas to 1 to get things working_).
* **Docker Config** - Public or private. (Private configs are shown when configured in the [Configs](microservices.md#configs) section).
* **Strategy** - how updates are handled and their downtimes: **RollingUpdate** - bring up another Replica first with the new update, and then remove the old one. **Recreate** - take the existing one down right away and then create a new one.

#### Containers

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.40.20.png" alt=""><figcaption></figcaption></figure>

* **Name** - often the same name as the deployment but since a deployment can have multiple containers, this gives you the ability to identify additional containers.
* **Docker Image** - The URL to the actual Docker Image: either public or private.

{% hint style="info" %}
You can have multiple containers when your deployment needs more than one container. For example, a PHP container for an API layer and a PostgreSQL container for a database that needs to be treated as a single deployment.
{% endhint %}

#### Ports

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.40.53.png" alt=""><figcaption></figcaption></figure>

* **Container Port** - the port that the Docker Image uses.
* **Service Port** - the port that the Function Stack uses.

{% hint style="info" %}
Both ports can be the same, but if you have multiple containers, you will need to use different ports because you can't have more than one of the same Service Port.
{% endhint %}

#### Environment Variables

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.41.16.png" alt=""><figcaption></figcaption></figure>

Environment Variables allow you to include basic variables for the container. If there are a lot of these, then it tends to be more useful to use a [Config](microservices.md#configs) file.&#x20;

{% hint style="info" %}
The possible values for the Environment Variables would be defined by the Docker Image - otherwise, Environment Variables can be ignored.
{% endhint %}

#### Volumes

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.44.50.png" alt=""><figcaption></figcaption></figure>

* **Name** - the name of the Volume.
* **Type** -&#x20;
  * **Scratch**: temporary storage that disappears when the container restarts.&#x20;
  * **Persistent Volume**: commonly used for database storage.&#x20;
  * **Config File**: the configuration for the Docker Image - the contents of this file would be determined by the Docker Image.
    * **Config** - a reference to the configuration in the [Config](microservices.md#configs) panel.
* **Mount Path** - the path to the config file within the Docker Image as specified by the Docker Image.

#### Resources

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.50.13.png" alt=""><figcaption></figcaption></figure>

Resources are the min/max for CPU and RAM. Also, the GPU, which is used for Machine Learning applications.

#### Docker Entrypoint

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.52.21.png" alt=""><figcaption></figcaption></figure>

Docker Entrypoint Command and Argument are advanced settings to override Docker Entrypoints.

#### Affinity and Tolerations

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.54.13.png" alt=""><figcaption></figcaption></figure>

Affinity and Tolerations are advanced Kubernetes concepts that allow your containers to use the appropriate resources provided by servers. For example, you may need a container on a server with a 16core CPU. Another example is you need a container on a server with a GPU but you don't want other containers to take that spot.



### Persistent Volumes

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 11.57.14.png" alt=""><figcaption></figcaption></figure>

Persistent Volumes are commonly used for a microservice that is a database. This is because typically database storage needs to stick around, or in other words, be persistent. So in the event, the server crashes and reboots the Persistent Volume is still there.&#x20;

### Configs

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-29 at 12.00.17.png" alt=""><figcaption></figcaption></figure>

Configs allow for an easy way to have configuration files for your microservice application. Microservices may often have a standard configuration that you may want to customize. For example, Postgres would come with a standard config file but their may be some customization that you specifically need to tailor to your application's needs.&#x20;

There are various different types of Config files. Docker Config will allow you to interact with a private repository if your Docker Image lives there.&#x20;

### Status

The status of the deployment can be monitored by clicking on Status of the Microservice Management Center.

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-28 at 15.21.34.png" alt=""><figcaption></figcaption></figure>

By selecting the name, you can confirm all the different settings.

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-28 at 15.47.41.png" alt=""><figcaption><p>View the various settings of the deployed microservice.</p></figcaption></figure>

And retrieve logs.

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-28 at 15.49.14.gif" alt=""><figcaption><p>Retrieve the logs of the deployed microservice. </p></figcaption></figure>

### Using a Microservice in the Function Stack

Once deployed, you can interact with the microservice in the Xano Function Stack.

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-28 at 15.58.50.png" alt=""><figcaption></figcaption></figure>

The Microservice function will be similar to an [external API request](broken-reference) function. Although the settings of the function are similar, it's important to call out that the **microservice is all internal traffic, making the interaction secure**.

<figure><img src="../../.gitbook/assets/CleanShot 2022-12-28 at 16.00.37.png" alt=""><figcaption></figcaption></figure>

* **Import Curl** - allows Xano to automatically build the microservice call via a curl command.
* **Host** - Select from a list of your deployments.&#x20;
* **Path** - define the microservice URL path here.
* **Method** - HTTP method just like an API call (GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS)
* **Params** - Any parameters or request body required.
* **Headers** - Define any custom headers.
* **Timeout** - Defines how long the Function Stack will wait in seconds before it considers the Function to be timed out.
* **Follow\_location -** determines if you wish to automatically follow the redirects (if there are any) in the microservice.

For more on Import Curl, Method, Params, Headers, Timeout, and Follow\_location check out the [External API Request](broken-reference) page.

