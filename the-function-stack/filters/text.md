# Text

Text filters enable you to transform and manipulate text.

* [**addslashes**](text.md#addslashes) - Adds a backslash to certain special characters
* [**capitalize**](text.md#capitalize) **-** Converts the first letter of each word to a capital letter.
* [**concat**](text.md#concat) **-** Concatenates two values together.
* [**contains**](text.md#contains) **-** Returns whether or not the expression is found.
* [**convert\_encoding**](text.md#convert_encoding) - Converts a text element's encoding to another
* [**detect\_encoding**](text.md#detect_encoding) - Returns the encoding of a text element
* [**ends\_with**](text.md#ends_with) **-** Returns whether or not the expression is present at the end.
* [**icontains**](text.md#icontains) **-** Returns whether or not the case-insensitive expression is found.
* [**iends\_with**](text.md#iends_with) **-** Returns whether or not the case-insensitive expression is present at the end.
* [**iindex**](text.md#iindex) **-** Returns the index of the case-insensitive expression or false if it can't be found.
* [**index**](text.md#index) **-** Returns the index of the case-sensitive expression or false if it can't be found.
* [**istarts\_with**](text.md#istarts_with) **-** Returns whether or not the case-insensitive expression is present at the beginning.
* [**list\_encodings**](text.md#list_encodings) - Returns available encoding formats for [**convert\_encoding**](text.md#convert_encoding) and [**detect\_encoding**](text.md#detect_encoding)
* [**ltrim**](text.md#ltrim) **-** Trim whitespace or other characters from the left side and return the result.
* [**querystring\_parse**](text.md#querystring_parse) **-** Parses a query string from a URL into its individual key-value pairs.
* [**regex\_get\_all\_matches**](text.md#regex_get_all_matches) **-** Return all matches performed by a regular expression on the supplied subject text.
* [**regex\_get\_first\_match**](text.md#regex_get_first_match) **-** Return the first set of matches performed by a regular expression on the supplied subject text.
* [**regex\_matches**](text.md#regex_matches) **-** Tests if a regular expression matches the supplied subject text.
* [**regex\_quote**](text.md#regex_quote) **-** Update the supplied text value to be properly escaped for regular expressions.
* [**regex\_replace**](text.md#regex_replace) **-** Perform a regular expression search and replace on the supplied subject text.
* [**replace**](text.md#replace) **-** Replace a text phrase with another.
* [**rtrim**](text.md#rtrim) **-** Trim whitespace or other characters from the right return the result.
* [**split**](text.md#split) **-** Splits text into an array of text and returns the result.
* [**sprintf**](text.md#sprintf) **-** formats text with variable substitution.
* [**starts\_with**](text.md#starts_with) **-** Returns whether or not the expression is present at the beginning.
* [**strlen**](text.md#strlen) **-** Returns the number of characters.
* [**substr**](text.md#substr) **-** Extracts a section of text.
* [**to\_lower**](text.md#to_lower) **-** Converts all characters to lower case and returns the result.
* [**to\_upper**](text.md#to_upper) **-** Converts all characters to upper case and returns the result.
* [**trim**](text.md#trim) **-** Trim whitespace or other characters from both sides and return the result.
* [**url\_addarg**](text.md#url_addarg) **-** Parses a URL and returns an updated version with an encoded version of the supplied argument.
* [**url\_delarg**](text.md#url_delarg) **-** Parses a URL and returns an updated version with the supplied argument removed.
* [**url\_getarg**](text.md#undefined) **-** Gets the argument's value from a URL.
* [**url\_hasarg**](text.md#url_hasarg) **-** Returns the existence of a argument in the URL.
* [**strip\_html**](text.md#strip_html) - Parses through raw HTML and removes tags
* [**url\_parse**](text.md#url_parse) **-** Parses a URL into its individual components.

#### addslashes:

Adds a backslash to the following characters: single quote, double quote, backslash, and null character.

<figure><img src="../../.gitbook/assets/CleanShot 2023-08-30 at 09.48.50.png" alt=""><figcaption></figcaption></figure>

#### capitalize:

Converts the first letter of each word to a capital letter.

![Example: we have a text value of hello world and apply the capitalize filter and it becomes Hello World.](<../../.gitbook/assets/CleanShot 2022-01-14 at 11.05.41.png>)

#### concat:

Concatenates 2 text strings together by an optional separator. The value can be any text and the separator can be anything: + , -, \_, a space, etc...

![Example: we have a text value of hello world and apply the concat filter and it becomes hello world+Xano.](<../../.gitbook/assets/CleanShot 2022-01-14 at 11.09.10.png>)



#### contains:

Returns whether or not the expression is found and is case-sensitive. The search term can be any string of text.\
This returns a "true" or "false" response.&#x20;

![Example: we have a text value of hello world and apply the contains filter this returns a value of "true](<../../.gitbook/assets/CleanShot 2022-01-14 at 11.11.43.png>)

#### convert\_encoding

Converts an encoded text element from one type of encoding to another

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-26 at 13.25.14.png" alt=""><figcaption></figcaption></figure>

#### detect\_encoding

Detects the encoding of a text element. Use the Encodings parameter to specify the encodings to check against, or leave blank to auto-detect

<figure><img src="../../.gitbook/assets/CleanShot 2023-04-26 at 13.26.14.png" alt=""><figcaption></figcaption></figure>

#### ends\_with:

Returns whether or not the expression is present at the end. The search term can be any string of text.\
This returns a "true" or "false" response.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.06.49.png" alt=""><figcaption></figcaption></figure>

#### icontains:

Returns whether or not the case-insensitive expression is found. The search term can be any string of text.\
This returns a "true" or "false" response.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.07.30.png" alt=""><figcaption></figcaption></figure>

#### iends\_with:

Returns whether or not the case-insensitive expression is present at the end. The search term can be any string of text.\
This returns a "true" or "false" response.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.08.41.png" alt=""><figcaption></figcaption></figure>

#### iindex:

Returns the index of the case-insensitive expression or false if it can't be found. The search term can be any string of text.\
This returns an integer value of where the character(s) exist in the string. The first character in a text string has an index of 0.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.09.11.png" alt=""><figcaption></figcaption></figure>

#### index:

Returns the index of the case-sensitive expression or false if it can't be found.  The search term can be any string of text.\
This returns an integer value of where the character(s) exist in the string. The first character in a text string has an index of 0.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.09.41.png" alt=""><figcaption></figcaption></figure>

#### istarts\_with:

Returns whether or not the case-insensitive expression is present at the beginning. The search term can be any string of text.\
This returns a "true" or "false" response.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.10.14.png" alt=""><figcaption></figcaption></figure>

#### list\_encodings

Lists the available encodings for [detect\_encoding](text.md#detect_encoding) and [convert\_encoding](text.md#convert_encoding)

#### ltrim:

Trim whitespace or other characters from the left side and return the result. The mask text can be any string of text.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.10.49.png" alt=""><figcaption></figcaption></figure>

#### rtrim:

Trim whitespace or other characters from the right return the result. The mask text can be any string of text.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.10.49 (1).png" alt=""><figcaption></figcaption></figure>

#### querystring\_parse:

Extracts query strings from a URL and places them into separate key/value pairs.\
The example below separates a URL using the **url\_parse** filter, and then uses querystring\_parse to parse the query parameters into separate keys and values.

![The test URL](<../../.gitbook/assets/CleanShot 2022-08-01 at 17.02.24@2x.png>)

![The function and querystring\_parse filter](<../../.gitbook/assets/CleanShot 2022-08-01 at 17.03.20@2x.png>)

![The result](<../../.gitbook/assets/CleanShot 2022-08-01 at 17.03.47@2x.png>)

#### join:

Joins an array of text into text via the separator and returns the result. Theseperator text can be any string of text.\
The array in this example is:\
\[hello, how, are, you]&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.12.23.png" alt=""><figcaption></figcaption></figure>

### Regex (Regular Expression)

Regex or regular expression is a more advance topic that can be useful for finding patterns in text. It is a string of text that allows you to create patterns that help match, locate, and manage text.

Regex typically includes something called delimiters to set the boundaries of the expression. Often times, / will be used as delimiters but almost any character can be used.

{% hint style="info" %}
_Regex filters inside the Query All Records function do not use delimiters._

_Regex filters in any other variable, function, etc. in Xano require delimiters **(meaning you'll need to wrap your expression in / characters)** as shown in the below examples._
{% endhint %}

Regex uses special characters, for example:

```
. is any character
\d is any number
\s is any whitespace
\w is any word character
* means 0 or more
+ means 1 or more

Regex uses additional special characters, these are just to name a few as an example.
```

Some special characters need the \ escape character, which is why [regex\_quote](text.md#regex_quote) can be useful to determine this. For example, . and $ do but @ does not.

You can then use ( ) to group matches. For example:

```
/(\w+)@\w+\.\w+/ this would get name of and full email address


/ is the starting delimiter
(\w+) is a matching group, this group must be at least 1 or more word character
@ is the symbold @
\w+ is at least 1 or more word character
\. is the symbol .
\w+ is at least 1 or more word character
/ is the ending delimiter
```



#### **regex\_get\_all\_matches:**

Return all matches performed by a regular expression on the supplied subject text.

![In this example, we are searching for all matches of /you/ which will return two matches \[you, you\].](<../../.gitbook/assets/CleanShot 2022-01-19 at 15.33.15.png>)

#### **regex\_get\_first\_match:**

Return the first set of matches performed by a regular expression on the supplied subject text.

![In this example, we are searching for the phrase h with one more additional word characters. The result is how and not Hi because this is case-sensitive.](<../../.gitbook/assets/CleanShot 2022-01-19 at 15.42.26.png>)

#### **regex\_matches:**

Tests if a regular expression matches the supplied subject text. Returns a true or false boolean.

![In this example, we are seeing if the subject matches the provided regex. The result will be true because how matches /h\w+/ which is a string starting with h and having one or more word characters after.](<../../.gitbook/assets/CleanShot 2022-01-19 at 15.44.50.png>)

#### **regex\_quote:**

Update the supplied text value to be properly escaped for regular expressions.

![](<../../.gitbook/assets/CleanShot 2022-01-19 at 16.18.00.png>)

![The result using / as a delimiter.](<../../.gitbook/assets/CleanShot 2022-01-19 at 16.21.54.png>)

#### **regex\_replace**

Perform a regular expression search and replace on the supplied subject text.

![In this example, we are using /(\w+)@\w+\\.\w+/ to find an email address and using the replacement to replace it with support@xano.com. The result is please email support@xano.com](<../../.gitbook/assets/CleanShot 2022-01-19 at 16.26.05.png>)

#### replace:

Replace a text phrase with another. Search can be any word in the value and the replacement can be anything.

![Example: we have a text value of hello world and apply the replace filter and it becomes hello Xano.](<../../.gitbook/assets/CleanShot 2022-01-14 at 15.28.10.png>)

#### split:

Splits text into an array of text and returns the result. The separator can be anything the words are separated by, in this example, it is the + symbol.

![Example: we have a text value of hello+world and apply the split filter and it becomes \["hello", "world"\].](<../../.gitbook/assets/CleanShot 2022-01-14 at 15.30.21.png>)

#### Split and trim text into an array example

We can combine multiple filters to format a text string into an array.

For example, we have the string "a , b,c,  d"

Notice the inconsistent spaces. If all we do is use split then the spaces will persist in the array. We can combine [trim](text.md#trim) and filter\_empty filters to remove unnecessary spaces or blank values.

![](<../../.gitbook/assets/CleanShot 2022-04-28 at 14.46.14.png>)

#### sprintf

Formats text with variable substitution. This is helpful when wanting to substitute a URL string with a variable that either the use provides or that is gotten from the result of a previous function.\
\
\- **%d** is used to replace a number and will enforce a number.\
\- **%s** is used to replace text.

The first example shows how to use variable substitution with a number using %d.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.14.58.png" alt=""><figcaption></figcaption></figure>

The second example will replace %s with text:

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.15.58.png" alt=""><figcaption></figcaption></figure>

We can use multiple arguments on the sprintf filter to replace any number of values.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.16.56 (1).png" alt=""><figcaption></figcaption></figure>

If you have a % character in your text that you would **NOT** like to replace with the `sprintf` filter you are able to escape the filter by adding an additional % character next to the existing % character. "Example:  "%%"

#### starts\_with:

Returns whether or not the expression is present at the beginning.  The search term can be any string of text and is case-sensitive.\
This returns a "true" or "false" response.&#x20;

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.17.41.png" alt=""><figcaption></figcaption></figure>

#### strlen:

Returns the number of characters.

![Example: we have a text value of hello world and apply the strlen filter and it becomes the int 11.](<../../.gitbook/assets/CleanShot 2022-01-14 at 15.36.47.png>)

#### strip\_accents

Removes accents from characters

<figure><img src="../../.gitbook/assets/CleanShot 2022-10-03 at 08.54.22@2x.png" alt=""><figcaption></figcaption></figure>

#### substr:

Extracts a section of text. The start pos is based on the # of characters from the beginning with the first char pos= 0. The length can be an int.

![Example: we have a text value of hello world and apply the substr filter and it becomes wo.](<../../.gitbook/assets/CleanShot 2022-01-14 at 15.51.52.png>)

#### to\_lower

Converts all characters to lower case and returns the result.

![Example: we have a text value of HeLLo WoRlD and apply the to\_lower filter and it becomes hello world.](<../../.gitbook/assets/CleanShot 2022-01-14 at 15.53.25.png>)

#### to\_upper:

Converts all characters to upper case and returns the result.

![Example: we have a text value of HeLLo WoRlD and apply the to\_upper filter and it becomes HELLO WORLD.](<../../.gitbook/assets/CleanShot 2022-01-14 at 15.55.10.png>)

#### trim:&#x20;

Trim whitespace or other characters from both sides and return the result. The mask text can be any string of text.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 11.34.17.png" alt=""><figcaption></figcaption></figure>

#### url\_addarg:

Parses a URL and returns an updated version with an encoded version of the supplied parameter.\
This filter is used to add a key(blog\_id, authorname) and a value (123 , john). Those parameters would be added as ?blog\_id=123 and ?authorname=john.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 11.35.22.png" alt=""><figcaption></figcaption></figure>

#### url\_delarg:

Parses a URL and returns an updated version with the supplied parameter removed.\
This filter is used to delete a key(blog\_id, authorname). Those parameters would be deleted at the end of a url  as ?blog\_id or ?authorname.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 11.36.01.png" alt=""><figcaption></figcaption></figure>

#### **url\_getarg:**

Returns the value of a query parameter in a URL.

![Our sample URL](<../../.gitbook/assets/image (37).png>)

![In this example, we are getting the value of the "another" query parameter.](<../../.gitbook/assets/CleanShot 2022-08-01 at 17.06.16@2x.png>)

#### url\_hasarg:

Returns the existence of an arguments in the URL.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 16.18.30.png" alt=""><figcaption></figcaption></figure>

#### strip\_html:

Parses raw HTML and removes HTML tags, returning the remaining text.

For example, if you input HTML that contains a collection of \<p> tags and want to remove these and only return the text. Good to use in succession with the split filter to parse several elements and separate them into an array.

![In this example, we are stripping the tags from an HTML paragraph and returning the result.](<../../.gitbook/assets/CleanShot 2022-08-02 at 09.13.48@2x.png>)

#### url\_parse

Breaks down a URL into individual components.

<figure><img src="../../.gitbook/assets/CleanShot 2025-02-06 at 11.37.34.png" alt=""><figcaption></figcaption></figure>

