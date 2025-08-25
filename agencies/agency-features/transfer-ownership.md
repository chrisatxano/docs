# Transfer Ownership

## Transferring a Workspace to a Client Instance

{% stepper %}
{% step %}
### From the left-hand menu of your instance selection screen, click ![](<../../.gitbook/assets/CleanShot 2025-03-13 at 16.05.37.png>)


{% endstep %}

{% step %}
### Choose the workspace you'd like to transfer, and the instance to transfer it to.

<figure><img src="../../.gitbook/assets/CleanShot 2025-03-13 at 16.07.20.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you don't see your client's instance available, make sure they've accepted their [client-invite.md](client-invite.md "mention") and purchased the suggested plan.
{% endhint %}

This will create a **copy** of the workspace and transfer that copy to your client's instance.

You should proceed with any additional work by accessing the client's instance directly, as any further changes you make on your own copy of the workspace will not transfer.
{% endstep %}
{% endstepper %}



{% hint style="warning" %}
For larger workspaces, transferring this way may not be possible. If you run into trouble, please reach out to support so we can process the migration for you.
{% endhint %}

## Downtime and Migration

Once the workspace is transferred, all API endpoints for that transferred workspace will resolve using your client instance's Xano domain. You'll need to update the API base URL for every connection (such as your frontend) to your client's instance.

Transferring a workspace creates a copy of it as it stands at that moment, so there should not be any downtime during this process.
