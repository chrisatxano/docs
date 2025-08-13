---
icon: gears
---

# Instance Settings

## Custom Domain

Xano has support for users on any of our paid plans to set up a custom domain to be used for the URLs of their API endpoints.&#x20;

{% embed url="https://youtu.be/St_sqV5VWRI" %}

{% stepper %}
{% step %}
### Head to the instance selection page and click the :gear:icon next to your instance


{% endstep %}

{% step %}
### Choose 'Custom Domain' from the panel that opens


{% endstep %}

{% step %}
### Update the DNS records with your domain registrar

For more information on this process, consult your registrar's documentation. Quick links are provided below for your convenience.

* [GoDaddy](https://www.godaddy.com/help/manage-dns-records-680)
* [Namecheap](https://www.namecheap.com/support/knowledgebase/article.aspx/767/10/how-to-change-dns-for-a-domain/)
* [Cloudflare](https://developers.cloudflare.com/dns/manage-dns-records/how-to/create-dns-records/)
* [Squarespace (formerly Google Domains)](https://support.squarespace.com/hc/en-us/articles/205812348-Accessing-your-Squarespace-managed-domain-s-DNS-settings)
* [Hover](https://support.hover.com/support/solutions/articles/201000064728-managing-dns-records)
* [Network Solutions](https://www.networksolutions.com/help/article/manage-dns-adns-records)
* [1&1 IONOS](https://www.ionos.com/help/domains/dns-settings/)
* [Bluehost](https://www.bluehost.com/help/article/dns-management-add-edit-or-delete-dns-entries)
* [HostGator](https://www.hostgator.com/help/article/changing-dns-records)
* [Porkbun](https://kb.porkbun.com/article/68-how-to-edit-dns-records)
* [Dynadot](https://www.dynadot.com/community/help/question/set-up-DNS)
* [Name.com](https://www.name.com/support/articles/206127137-adding-dns-records-and-templates)
* [Gandi](https://docs.gandi.net/en/domain_names/common_operations/dns_records.html)
{% endstep %}

{% step %}
### Check for propagation and update the domain in Xano once complete

Once you add the DNS record, those changes need to propagate across the globe to various DNS servers. You can check the status of propagation at whatismydns.net.

The more green checkmarks you see here, the better. You are free to proceed at any time, but please note that in areas where propagation has not completed, your APIs may not be accessible.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-07-24 at 13.34.43.png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Add your custom domain to the configuration panel

Add your domain and save your changes. They will be immediately applied, and your APIs and /Xano instance will be available at your new custom domain.
{% endstep %}
{% endstepper %}

### Connect via Xano Domain

In some cases, you may still want to connect to your Xano instance via the original Xano domain. To connect through your Xano domain, head to your instance selection screen. Click the three dots when hovering over your instance, and choose "Connect Via Xano Domain".

<figure><img src="../../.gitbook/assets/CleanShot 2023-03-15 at 09.31.14.png" alt=""><figcaption></figcaption></figure>

## Database Connector

{% hint style="info" %}
The Database Connector requires an add-on to our **Starter plan** or is included with the **Pro plan**.
{% endhint %}

You have the option to connect your Xano instance's PostgreSQL database directly with an external application or service. This can be useful if there is a platform for manipulating your database that you prefer to use over the Xano interface, creating custom backup and restore solutions, or even performing data analytics.

{% hint style="warning" %}
Use care when accessing your database directly. This type of connection removes a significant portion of normal checks and balances for data validity that using Xano directly provides.&#x20;

**Proceed with caution.**
{% endhint %}

#### How to Access the Database Connector

On your instance selection screen, click the ⚙️ icon, and in the panel that opens, choose Database Connector.

<figure><img src="../../.gitbook/assets/CleanShot 2023-08-16 at 13.18.14.png" alt=""><figcaption></figcaption></figure>

<div data-full-width="false"><figure><img src="../../.gitbook/assets/CleanShot 2023-08-16 at 13.21.19.png" alt="" width="329"><figcaption></figcaption></figure></div>

The panel that opens is split into two sections, Details and Settings.

<figure><img src="../../.gitbook/assets/CleanShot 2023-08-16 at 13.22.58.png" alt=""><figcaption></figcaption></figure>

Details allows you to retrieve the access information for a direct database connection.

Settings allows you to enable and use an allow list, to limit direct database connections to specific IP addresses.

1. Get your database's public IP
2. Get your database credentials
3. Settings Panel
4. Add an IP address to your allow list

Clicking both of the "Get" buttons will provide us with the database IP and two sets of credentials, full-access and read-only.

<figure><img src="../../.gitbook/assets/CleanShot 2023-08-21 at 07.47.08.png" alt=""><figcaption></figcaption></figure>

From this panel, you can also **revoke and re-generate** your database credentials, should the need arise.

#### Establishing a Database Connection (Example)

You can use any application you'd like that is capable of connecting to a PostgreSQL database. In this example, we'll be using Navicat.

Select 'Connection' in the top-left, and fill in your credentials and the IP recieved from Xano.

<figure><img src="../../.gitbook/assets/CleanShot 2023-08-16 at 13.39.09.png" alt=""><figcaption></figcaption></figure>

Click 'Save' to save the connection. We can now navigate the PostgreSQL database from Xano using Navicat. We can even add / update data, run queries, etc...

<figure><img src="../../.gitbook/assets/CleanShot 2023-08-16 at 13.41.35.gif" alt=""><figcaption></figcaption></figure>



## FAQ

**Why should you upgrade?**\
Free accounts come with **one workspace that shares resources with other Xano customers**. It also is limited on capabilities such as storage, database records, and processing power.  You'll easily be able to prototype most of your application in this type of account, but upgrading to a paid plan will give you a more powerful instance that can scale with your needs. [View plan pricing and details](http://www.xano.com/pricing).

**How long does upgrading take?**\
Upgrading an instance takes seconds to complete.

### **Does upgrading happen automatically once I pay?**

**You will need to update your API URL ORIGIN if:**

* You are adding certain features to your plan, such as Static IP
* You are upgrading from **free** to **paid**
* You are changing your server region

**You do not need to update your API URL ORIGIN if:**\
&#x20;\- You are upgrading from a PAID to PAID instance and not changing your server location.

## How to Upgrade <a href="#upgrading-an-instance" id="upgrading-an-instance"></a>

{% stepper %}
{% step %}
### Getting to the Upgrade screen

While on our free Build plan, you'll see a number of different places prompting you to upgrade whenever you're ready in the left-hand navigation, and in a banner at the top of the screen.

You can also navigate to your Billing screen by clicking your name in the bottom-left and choosing Billing.

<div align="left"><figure><img src="../../.gitbook/assets/CleanShot 2025-08-13 at 10.49.06.png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
### Pick your plan

Find the plan you'd like to upgrade to, and click **Upgrade**

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-13 at 10.52.35.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### Choose any add-ons or other options

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-13 at 10.54.33.png" alt=""><figcaption></figcaption></figure>

1. Set your server region. It's best to choose a region that is closest to a majority of your user base.
2. Select any add-ons that you'd like from here. You can always adjust these later, as well.

{% hint style="success" %}
## Get more CPU power with CPU Boost

CPU Boost supercharges your Xano instance, and is a great way to ensure that you're providing the best experience for your users.

Not sure if the Boost is for you? Feel free to reach out to our Support team for more information. You can always add or remove it later.
{% endhint %}

3. Click **Final Review & Checkout** whenever you're ready
4. Switch to an Annual plan to save more from here
{% endstep %}

{% step %}
### Fill out your information and click Subscribe

{% hint style="warning" %}
## You're not done yet!

Continue with step 5 after you click Subscribe to ensure your upgrade is complete.
{% endhint %}

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-13 at 10.58.15.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
### After completing checkout, you'll be taken to the Upgrade screen

Depending on the upgrade you're performing, we don't process the upgrade immediately. We do this to ensure a seamless transition for your users. The following scenarios will prompt a manual upgrade process:

* Switching server regions
* Upgrading from a free to a paid plan
* Adding Static IP

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-13 at 10.59.40.png" alt=""><figcaption></figcaption></figure>

If you've already connected a frontend or other external services to your Xano workspace, you'll likely need to update those URLs to match your new instance. You'll find your new instance URL by clicking **Start Update** on the panel that opens. (Don't worry, you'll still need to confirm once more before the process begins.)

<figure><img src="../../.gitbook/assets/CleanShot 2025-08-13 at 11.02.21.png" alt=""><figcaption></figcaption></figure>

Just look for the **NEW URL ORIGIN.** That's your new instance URL. You'll need to replace any instances of the EXISTING URL ORIGIN on your frontend or external connections with the **NEW URL ORIGIN**.

Whenever you're ready, type "I UNDERSTAND" in the Confirm box and click **Start Update Now**

{% hint style="warning" %}
## Drafts

Make sure you publish any drafts before continuing; all drafts will be discarded when upgrading.
{% endhint %}
{% endstep %}

{% step %}
### Congratulations!

Your upgrade will process in just a few moments, and you're now on your newly upgraded Xano instance.

{% hint style="info" %}
## Need help using any of the new features?

Our Support team and the [Xano Community](https://community.xano.com/) are always here to help.
{% endhint %}
{% endstep %}
{% endstepper %}





