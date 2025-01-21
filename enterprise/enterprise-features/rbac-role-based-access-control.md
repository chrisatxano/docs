# RBAC (Role-based Access Control)

{% hint style="success" %}
Security Policy Control is a premium add-on. Please contact your Xano representative or support for details.&#x20;
{% endhint %}

Xano gives you control to specify Security Policy enforcement across the Instance and all team members of the Instance.

Easily control Security requirements for anyone accessing your Xano Instance such as Inactivity Logout, Authentication Services, 2FA, and SSO.

### Security Policy Control Panel

The Security Policy Control Panel is accessible from the Instance menu. First, open the Instance Settings Panel:

&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2023-06-02 at 15.02.46.png" alt=""><figcaption><p>Open the Instance settings.</p></figcaption></figure>

Next, select Security Policy to open the Security Policy Control Panel.

<figure><img src="../../.gitbook/assets/CleanShot 2023-06-02 at 15.03.46.png" alt=""><figcaption><p>Select Security Policy.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/CleanShot 2023-08-16 at 09.56.38.png" alt=""><figcaption></figcaption></figure>

Set the Instance's Security Policy by choosing or enforcing inactivity logout, authentication services, 2FA, or SSO for all team members of the Instance.&#x20;

{% hint style="info" %}
_Custom SSO is a separate paid feature that includes Security Policy Control; However, Custom SSO is not included in the Security Policy feature._
{% endhint %}

**Inactivity Logout Time** -- enables automatic logout of Xano due to inactivity for all team members. If enabled options range between 1 to 24 hours.&#x20;

**Require 2FA** -- enforces all team members of your Instance to authenticate using 2FA when logging into Xano.

**Authentication Enforcement** -- optionally enforce which authentication service(s) team members can authenticate with.

**Allowed SSO Hosts** -- enforces the email address domains allowed when team members log in. For example, if we wanted team members to only authenticate using Github accounts that use a xano.com email address, we would check Github under Authentication Enforcement and add xano.com as an allowed SSO host.

**IP Address Allowlist** -- enforces certain IPs allowed to access your Xano instance and call your APIs

**IP Address Denylist** -- enforces denying IPs allowed to access your Xano instance and call your APIs

### Login Events

With the Compliance addon, you have access to Login History.&#x20;
