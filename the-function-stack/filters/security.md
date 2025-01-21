# Security

* [**create\_uid**](security.md#create_uid-1) **-** Returns a unique 64bit unsigned int value seeded off the value.
* [**decrypt**](security.md#decrypt) **-** Decrypts the value and returns the result.
* [**encrypt**](security.md#encrypt) **-** Encrypts the value and returns the result.
* [**hmac\_md5**](security.md#hmac_md5) **-** Returns a MD5 signature representation of the value using a shared secret via the HMAC method
* [**hmac\_sha1**](security.md#hmac_sha1) **-** Returns a SHA1 signature representation of the value using a shared secret via the HMAC method
* [**hmac\_sha256**](security.md#hmac_sha256)[ **/ hmac\_sha384 / hmac\_sha512**](security.md#hmac_sha256) **-** Returns a SHA256/384/512 signature representation of the value using a shared secret via the HMAC method
* [**jwe\_decode**](security.md#jwe_decode) **-** Decodes the value represented as JWE token and returns the original payload.
* [**jwe\_encode**](security.md#jwe_encode) **-** Encodes the value and returns the result as a JWE token.
* [**md5**](security.md#md5) **-** Returns an MD5 signature representation of the value.
* [**secureid\_decode**](security.md#secureid_decode) **-** Returns the id of the original encode.
* [**secureid\_encode**](security.md#secureid_encode) **-** Returns an encrypted version of the id.
* [**sha1**](security.md#sha1) **-** Returns a SHA1 signature representation of the value.
* [**sha256 / sha384 / sha512**](security.md#sha256) **-** Returns a SHA256/384/512 signature representation of the value.

#### create\_uid:

Returns a unique 64bit unsigned int value seeded off the value.

![In this example, the variable crypto becomes 3612171568446766000.](../../.gitbook/assets/Screenshot_2020-07-02_22-28-00.png)

#### decrypt:

Decrypts the value and returns the result.

![](<../../.gitbook/assets/CleanShot 2022-02-22 at 15.26.55.png>)

#### encrypt:

Encrypts the value and returns the result in raw binary form. Find more details on the [encrypt function](broken-reference) page.

![](<../../.gitbook/assets/CleanShot 2022-02-22 at 15.23.02.png>)



#### hmac\_md5

Returns a MD5 signature representation of the value using a shared secret via the HMAC method.\
The secret key is a unique piece of information that is used to compute the HMAC and is known both by the sender and the receiver of the message. This key will vary in length depending on the algorithm that you use.

![In this example, the variable var\_1 becomes 0ea035295cb4a89735c302776b3689446bf2d7af.](https://mrkr.io/s/60106a183d1d3d26b1257435/0)



#### hmac\_sha1

Returns a SHA1 signature representation of the value using a shared secret via the HMAC method.\
The secret key is a unique piece of information that is used to compute the HMAC and is known both by the sender and the receiver of the message. This key will vary in length depending on the algorithm that you use.

![In this example, the variable var\_1 becomes 0ea035295cb4a89735c302776b3689446bf2d7af.](https://mrkr.io/s/60106ad28c857726544861db/0)

#### hmac\_sha256 / hmac384 / hmac512

Returns a SHA256/384/512 signature representation of the value using a shared secret via the HMAC method.\
The secret key is a unique piece of information that is used to compute the HMAC and is known both by the sender and the receiver of the message. This key will vary in length depending on the algorithm that you use.

![In this example, the variable var\_1 becomes 734aeac141e3a20937ccc918179b4e200f38ff58726432efb82717799d86c880.](https://mrkr.io/s/60106b7916169730cbfbb0cd/0)

#### jwe\_decode:

Decodes the value represented as JWE token and returns the original payload.

![In this example, we use the JWE token that was encoded below and decoded it back to 456.](../../.gitbook/assets/jwedecode.png)



#### jwe\_encode

Encodes the value and returns the result as a JWE token.

![In this example, we use the jwe\_encode filter and it returns a JWE token.](../../.gitbook/assets/jweencode.png)



#### md5

Returns an MD5 signature representation of the value. A salt value can be added to the text to provide an extra layer of security.

![](../../.gitbook/assets/Screenshot_2020-07-02_22-34-09.png)

#### secureid\_decode

Returns the id of the original encode. If a salt was added to encode this value the same salt needs to be added to decrypt it.

![Example: the variable is the secureid\_encode example with the secureid\_decode filter, it becomes 123456.](../../.gitbook/assets/secureiddecode.png)

#### secureid\_encode

Returns an encrypted version of the id. A salt value can be added to the text to provide an extra layer of security.

![In this example, the variable is an integer 123456 with the secureid\_encode filter it becomes QWd1cA.1NMF7ukY3mQ.](../../.gitbook/assets/secureidencode.png)

#### sha1

Returns a SHA1 signature representation of the value. A salt value can be added to the text to provide an extra layer of security.

![](../../.gitbook/assets/sha1.png)

#### sha256 / sha384 / sha512:

Returns a SHA256/384/512 signature representation of the value. A salt value can be added to the text to provide an extra layer of security.

![](../../.gitbook/assets/sha256.png)
