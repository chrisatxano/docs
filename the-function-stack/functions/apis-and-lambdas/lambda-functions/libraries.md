# Libraries

Lambdas become even more powerful when they can stand on the shoulders of world class libraries and functions developed by 3rd parties. Xano currently doesn't support loading arbitrary external libraries, but we do hand pick the most popular ones based on customer demand. If you have a favorite, then please let us now on our [feedback board](https://community.xano.com/feature-requests).

### Lodash <a href="#lodash" id="lodash"></a>

The [Lodash library](https://lodash.com/) is considered the Swiss Army Knife of transformation. If you are tasked with manipulating strings, numbers, objects, and/or arrays, then there is a good chance the lodash library can help.

This library is accessible within the Lambda through the library variable `_` (the underscore character).

Here is an example of using the `uniq` function of the lodash library to return an array of unique values.

Copy

```
var items = [1,2,3,2,1];
return _.uniq(items); // returns a unique array of [1,2,3]
```

### Moment.js <a href="#moment.js" id="moment.js"></a>

The [Moment.js](https://momentjs.com/) library is a popular library used to parse, validate, transform, and format dates and time.

This library is accessible within the Lambda through the library variable `moment` .

Here is an example showing how to parse an ISO 8601 formatted date, add 1 month, and then return the result in its original format.

Copy

```
var myDate = '2022-01-01T00:00:00.000Z';
return moment(myDate).add(1, "month").toISOString(); // 2022-02-01T00:00:00.000Z
```

### Luxon <a href="#luxon" id="luxon"></a>

The [Luxon](https://moment.github.io/luxon/#/) library was built by one of the Moment.js's maintainers and is considered the next evolution of Moment.js.

This library is accessible within the Lambda through the library variable `luxon`.

Here is an example showing how to parse an ISO 8601 formatted date, add 1 month, and then return the result in its original format.

Copy

```
var myDate = '2022-01-01T00:00:00.000Z';
return luxon.DateTime.fromISO(myDate).plus({month: 1}).setZone("UTC").toISO(); // 2022-02-01T00:00:00.000Z
```

### Axios <a href="#axios" id="axios"></a>

The [Axios](https://axios-http.com/docs/intro) library is a popular networking library for sending HTTP requests.

This library is accessible within the Lambda through the library variable `axios`.

Here is an example showing how to retrieve a json response from GitHub's API.

Copy

```
var url = 'https://api.github.com/users/github';
return (await axios.get(url)).data;
```

### Fetch <a href="#fetch" id="fetch"></a>

The [Fetch ](https://github.com/node-fetch/node-fetch)library is another networking library for sending HTTP requests. It is built into current generation web browsers, which makes it very popular to use because there is no additional download required.

This library is accessible within the Lambda through the library variable `fetch`.

Here is an example showing how to retrieve a json response from GitHub's API.

Copy

```
var url = 'https://api.github.com/users/github';
return (await fetch(url)).json();
```

### Math.js <a href="#math.js" id="math.js"></a>

The [Math.js](https://mathjs.org/) library provides support for advanced math formulas and expressions.

This library is accessible within the Lambda through the library variable `math`. The standard JavaScript Math library is accessible through the variable `Math`, so make sure you pay attention to case sensitivity, so that you are using the appropriate library.

Here is an example showing how to perform the negative square root of 4.

Copy

```
return math.sqrt(-4);
// 2i
```

### Crypto <a href="#crypto" id="crypto"></a>

The [Crypto](https://nodejs.org/api/crypto.html) library is built into [Node.js](https://nodejs.org/) and useful for performing common routines related to cryptography.

This library is accessible within the Lambda through the library variable `crypto`.

Here is an example showing how to perform a SHA 256 digital signature.

Copy

```
var data = 'test123';
return crypto.createHash('sha256').update(data).digest('hex');
// ecd71870d1963316a97e3ac3408c9835ad8cf0f3c1bc703527c30265534f75ae
```

### Nodemailer <a href="#nodemailer" id="nodemailer"></a>

The [Nodemailer](https://nodemailer.com/about/) library provides support to send email using SMTP and other transport mechanisms.

This function is accessible within the Lambda through the function variable `nodemailer`.

Here is an example showing how to send a test email through ethereal.email. This example is taken from the Nodemailer documentation.

Copy

```
let testAccount = await nodemailer.createTestAccount();

// create reusable transporter object using the default SMTP transport
let transporter = nodemailer.createTransport({
  host: 'smtp.ethereal.email',
  port: 587,
  secure: false, // true for 465, false for other ports
  auth: {
    user: testAccount.user, // generated ethereal user
    pass: testAccount.pass, // generated ethereal password
  },
});

// send mail with defined transport object
let info = await transporter.sendMail({
  from: '"Fred Foo 👻" <foo@example.com>', // sender address
  to: 'bar@example.com, baz@example.com', // list of receivers
  subject: 'Hello ✔', // Subject line
  text: 'Hello world?', // plain text body
  html: '<b>Hello world?</b>', // html body
});

return nodemailer.getTestMessageUrl(info);
// Preview URL: https://ethereal.email/message/WaQKMgKddxQDoou...
```

### Mailparser <a href="#mailparser" id="mailparser"></a>

The [Mailparser](https://nodemailer.com/about/) library is an addon for Nodemailer.

This function is accessible within the Lambda through the function variable `mailparser`.

Here is an example showing how to instantiate it.

Copy

```
const MailParser = mailparser.MailParser;
let parser = new MailParser();

return typeof parser; // object
```

### Promisify <a href="#promisify" id="promisify"></a>

The [Promisify ](https://nodejs.org/dist/latest-v8.x/docs/api/util.html#util_util_promisify_original)function is built into [Node.js](https://nodejs.org/) and is useful for converting legacy callback routines into a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) based variant. Promises are a standardization of how responses are received in asynchronous programming, which makes it possible to rely on shorthand keywords like [async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function).

This function is commonly used along with the Crypto library for those wishing to use that library with Promises instead of callbacks.

This function is accessible within the Lambda through the function variable `promisify`.

Here is an example showing how to use Promisify on the Crypto library to generate an [HMAC](https://en.wikipedia.org/wiki/HMAC) secret key.

Copy

```
return (await promisify(crypto.generateKey)('hmac', {length: 64}))
    .export()
    .toString('hex');
```

### Node Libraries <a href="#node-libraries" id="node-libraries"></a>

The following node libraries are available within Xano's Lambda support: [DNS](https://nodejs.org/docs/latest-v16.x/api/dns.html), [HTTP](https://nodejs.org/docs/latest-v16.x/api/http.html), [HTTPS](https://nodejs.org/docs/latest-v16.x/api/https.html), and [NET](https://nodejs.org/docs/latest-v16.x/api/net.html).

They are accessible within the Lambda through the function variables: `dns`, `http`, `https`, and `net`.

Here is an example showing how to create a custom https agent.

Copy

```
const httpsAgent = new https.Agent({
	keepAlive: true
});
```

### Socks <a href="#socks" id="socks"></a>

The [Socks](https://www.npmjs.com/package/socks) library is a fully featured SOCKS proxy client supporting SOCKSv4, SOCKSv4a, and SOCKSv5 protocols.

This library is accessible within the Lambda through the library variable `socks`.

Here is an example showing how to create a connection.

Copy

```
const options = {
  proxy: {
    host: '159.203.75.200', // ipv4 or ipv6 or hostname
    port: 1080,
    type: 5 // Proxy version (4 or 5)
  },

  command: 'connect', // SOCKS command (createConnection factory function only supports the connect command)

  destination: {
    host: '192.30.253.113', // github.com (hostname lookups are supported with SOCKS v4a and 5)
    port: 80
  }
};

return await socks.SocksClient.createConnection(options);
```

### Ethers.js <a href="#ethers.js" id="ethers.js"></a>

This [library](https://docs.ethers.io/) aims to be a complete and compact library for interacting with the Ethereum Blockchain and its ecosystem.

This is accessible within the Lambda through the function variable `ethers`.

Here is an example of formatting a number in Ether.

Copy

```
return ethers.utils.formatEther(10); // 0.0000000000000001
```

### Azure/Identity <a href="#azure-identity" id="azure-identity"></a>

This [library](https://learn.microsoft.com/en-us/javascript/api/@azure/identity/?view=azure-node-latest) provides [Azure Active Directory (Azure AD)](https://learn.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) token authentication through a set of convenient TokenCredential implementations.

This is accessible within the Lambda through the function variable `azure.identity`.

Here is an example of generating default Azure credentials with Azure/Identity.

Copy

```
return new azure.identity.DefaultAzureCredential();
```

### Azure/Service-Bus <a href="#azure-service-bus" id="azure-service-bus"></a>

Here is an example of generating a service bus client connection with Azure/Service-Bus.

This is accessible within the Lambda through the function variable `azure.serviceBus`.

This [library](https://www.npmjs.com/package/@azure/service-bus) provides access to [Azure Service Bus](https://azure.microsoft.com/services/service-bus/), which is a highly-reliable cloud messaging service from Microsoft.

Copy

```
return new azure.serviceBus.ServiceBusClient('your-connection-string');
```

### Zeebe <a href="#zeebe" id="zeebe"></a>

This [library](https://www.npmjs.com/package/zeebe-node) is a Node.js gRPC client for [Zeebe](https://zeebe.io/), the workflow engine in Camunda Platform 8.

This is accessible within the Lambda through the function variable `zeebe`.

Here is an example of generating a timeout duration with Zeebe:

Copy

```
return zeebe.Duration.seconds.of(30);
```

### CryptoJS <a href="#cryptojs" id="cryptojs"></a>

This [library](https://www.npmjs.com/package/crypto-js) is a Node.js package of crypto standards.

This is accessible within the Lambda through the function variable `cryptojs`.

Here is an example of encrypting a string using CryptoJS:

Copy

```
return cryptojs.AES.encrypt('my message', 'secret key 123').toString();
```

### UUID <a href="#uuid" id="uuid"></a>

This [library](https://www.npmjs.com/package/uuid) is a Node.js package for the creation of RFC4122 UUID's

This is accessible within the Lambda through the function variable `uuid`.

Here is an example of creating a UUID:

Copy

```
return uuid.v4();
```

### JWT: Jose <a href="#jwt-jose" id="jwt-jose"></a>

This [library](https://www.npmjs.com/package/jose) is JavaScript module for JSON Object Signing and Encryption, providing support for JSON Web Tokens (JWT), JSON Web Signature (JWS), JSON Web Encryption (JWE), JSON Web Key (JWK), JSON Web Key Set (JWKS), and more

This is accessible within the Lambda through the function variable `jose`.

Here is an example of creating a signed JWT:

Copy

```
const secret = new utils.TextEncoder().encode(
  "cc7e0d44fd473002f1c42167459001140ec6389b7353f8088f4d9a95f2f596f2"
);
const alg = "HS256";

const jwt = await new jose.SignJWT({ "urn:example:claim": true })
  .setProtectedHeader({ alg })
  .setIssuedAt()
  .setIssuer("urn:example:issuer")
  .setAudience("urn:example:audience")
  .setExpirationTime("2h")
  .sign(secret);

return jwt;
```

### Fast XML Parser <a href="#fast-xml-parser" id="fast-xml-parser"></a>

This [library](https://www.npmjs.com/package/fast-xml-parser) is a Node.js package for being able to parse, build, and validate XML.

This is accessible within the Lambda through the function variable `fastXmlParser`.

Here is an example of parsing an XML string:

Copy

```
const parser = new fastXmlParser.XMLParser();

const result = parser.parse('<h1>Hey</h1>'); // { "h1": "Hey"}

return result;
```

### AWS4: Sign Request Signatures <a href="#aws4-sign-request-signatures" id="aws4-sign-request-signatures"></a>

This [library](https://www.npmjs.com/package/aws4) is a Node.js package for signing http/https requests using AWS Signature Version 4.

This is accessible within the Lambda through the function variable `aws4`.

Here is an example of parsing an XML string:

Copy

```
var opts = { host: 'my-bucket.s3.us-west-1.amazonaws.com', path: '/my-object', service: 's3', region: 'us-west-1' }

aws4.sign(opts, { accessKeyId: '', secretAccessKey: '' })

https.request(opts, (res) => { ... });
```

Last updated 2 months ago
