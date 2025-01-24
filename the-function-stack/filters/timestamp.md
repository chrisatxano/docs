# Timestamp

{% hint style="info" %}
For information on how Xano stores, reads, and formats timestamps, visit the [Timestamp](broken-reference) page.
{% endhint %}

### **to\_timestamp**

In this example, the timezone UTC is important because 'last Monday' means different things depending on timezone.

t's important to specify a timezone for 'last Monday' because it could 'last Monday' at 00:00:00 PST is different than 'last Monday at 00:00:00 UTC (or any other timezone). Xano stores it in Unix timestamps which is a specific number in milliseconds.

However, if the timezone was present like in this example, then the timezone would not have any effect.&#x20;

In this example 'now' would be the same Unix timestamp, regardless of timezone. Therefore, a specified timezone like UTC, is not necessary.

***

### **add\_ms\_to\_timestamp**

Add milliseconds to a timestamp, (negative values are ok).

***

### **add\_secs\_to\_timestamp**

Add seconds to a timestamp, (negative values are ok).

***

### **format\_timestamp**

Converts a timestamp into a human-readable formatted date based on the supplied format.&#x20;

{% hint style="info" %}
**This format follows the** [**PHP DateTime format**](https://www.php.net/manual/en/datetime.format.php)**: see the** [**full list of formatting options**](https://www.php.net/manual/en/datetime.formats.php#datetime.formats.relative)**.**

[Timezone regions are listed here](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones).
{% endhint %}

**Some common examples:**

* `M` is a short text version of a month, like **Jul,** while `m` is the numeric version like **07**
* `Y` is the 4 digit representation like **2023**, etc. while `y` is the 2 digit version **23**
* To achieve something like **May 4th, 2023,** you would use: `F jS, Y`
* Other tools might use something like `YYYY-MM-DD`, but in Xano, you would use `Y-m-d`





***

### **parse\_timestamp**

Parse a timestamp from a flexible, human-readable format into a Unix timestamp in milliseconds. This filter is sort of like the opposite of format\_timestamp. You can utilize the [PHP DateTime Format](https://www.php.net/manual/en/datetime.format.php)  character list to transform a time format into a Unix timestamp in milliseconds.&#x20;

![In this example, May 4th, 2020 is transformed into a timestamp.](<../../.gitbook/assets/CleanShot 2022-05-05 at 11.51.38.png>)

```
Parse format for May 4th, 2020
F jS, Y
```

![30/03/2024 14:30:00 is parsed into a Unix timestamp in milliseconds](<../../.gitbook/assets/CleanShot 2022-05-05 at 11.58.46.png>)

```
Parse format for 30/03/2024 14:30:00
d/m/Y H:i:s
```

![11-27-22 5:15PM is parsed into a Unix timestamp in milliseconds.](<../../.gitbook/assets/CleanShot 2022-05-05 at 12.02.47.png>)

```
Parse format for 11-27-22 5:15PM
m-d-y g:iA
```

![6/1/22 07:30:00 am will be parsed into a Unix timestamp in milliseconds.](<../../.gitbook/assets/CleanShot 2022-05-05 at 14.00.43.png>)

```
Parse format for 6/1/22 07:30:00 am
n/j/y h:i:s a
```

***

### **transform\_timestamp**

This allows you to use [relative time formats](https://www.php.net/manual/en/datetime.formats.php#datetime.formats.relative) that are anchored around a previous time. Use the link to see various relative time formats that Xano accepts.&#x20;

***

### to\_ time since epoch

#### to\_ms / to\_seconds / to\_mins / to\_hours / to\_days

Converts a regular expression into number of ms / secs / mins / hours / days since the UNIX epoch.

For example, a value of 'yesterday', 'three days ago' or even a date such as 'January 1, 2000' are all valid inputs for these filters and can help for quick timestamp conversions.

