# Math

{% embed url="https://youtu.be/OJtsO-R9VBI" %}

Math filters are various operations in Xano to perform math and calculations. Like all filters you can chain math filters together and nest them inside one another to perform order of operations.

* [**abs**](math.md#abs-x) **-** Returns the absolute.
* [**acos**](math.md#acos-x) **-** Calculates the arc cosine of the supplied value in radians.
* [**acosh**](math.md#acosh-x) **-** Calculates the inverse hyperbolic cosine of the supplied value in radians.
* [**add**](math.md#add-x-y) **-** Add 2 values together and return the answer
* [**asin**](math.md#asin-x) **-** Calculates the arc sine of the supplied value in radians..
* [**asinh**](math.md#asinh-x) **-** Calculates the inverse hyperbolic sine of the supplied value in radians.
* [**atan**](math.md#atan-x) **-** Calculates the arc tangent of the supplied value in radians.
* [**atanh**](math.md#atanh-x) **-** Calculates the inverse hyperbolic tangent of the supplied value in radians.
* [**bitwise\_and**](math.md#bitwise_and-x-y) **-** Bitwise AND 2 values together and return the answer.
* [**bitwise\_or**](math.md#bitwise_or-x-y) **-** Bitwise OR 2 values together and return the answer.
* [**bitwise\_xor**](math.md#bitwise_xor-x-y) **-** Bitwise XOR 2 values together and return the answer.
* [**ceil**](math.md#ceil-x) **-** Round a decimal up to its integer equivalent.
* [**cos**](math.md#cos-x) **-** Calculates the cosine of the supplied value in radians.
* [**deg2rad**](math.md#deg2rad-x) **-** Convert degrees to radians.
* [**divide**](math.md#divide-x-y) **-** Divide 2 values together and return the answer.
* [**exp**](math.md#exp-x) **-** Returns the exponent of mathematical expression "e".
* [**floor**](math.md#floor-x) **-** Round a decimal down to its integer equivalent.
* [**array\_max**](math.md#array_max) **-** Returns the max of the values of the array.
* [**array\_min** ](math.md#array_min)**-**  Returns the min of the values of the array.
* [**modulus**](math.md#modulus-x-y)**-** Modulus 2 values together and return the answer.
* [**min**](math.md#min) - Return the min of any two values
* [**max**](math.md#max) - Return the max of any two values
* [**multiply**](math.md#multiply-x-y) **-** Multiply 2 values together and return the answer.
* [**number\_format**](math.md#number_format-x-decimals-decimalpoint-separator) **-** Format a number with flexible support over decimal places, thousands separator, and decimal separator.
* [**pow**](math.md#pow-x-exp) **-** Returns the value raised to the power of exp.
* [**product**](math.md#product) **-** Returns the product of the values of the array.
* [**rad2deg**](math.md#rad2deg-x) **-** Convert radians to degrees.
* [**round**](math.md#round-x-precision) **-** Round a decimal with optional precision.
* [**sin**](math.md#sin-x) **-** Calculates the sine of the supplied value in radians.
* [**sqrt**](math.md#sqrt-x) **-** Returns the square root of the value
* [**subtract**](math.md#subtract-x-y) **-** Subtract 2 values together and return the answer.
* [**sum**](math.md#sum) **-** Returns the sum of the values of the array.
* [**tan**](math.md#tan-x) **-** Calculates the tangent of the supplied value in radians.\


<details>

<summary>abs(x)</summary>

Returns the absolute value of a number

Ex: `abs(-5) -> 5`

Inputs: `x` (numeric) A single number

Output: Outputs the absolute value of the input number

![](<../../.gitbook/assets/image (16).png>)

</details>

<details>

<summary>acos(x)</summary>

Calculates the arc cosine of the supplied value in radians.

Example: Find the arc cosine of 0.5: `acos(0.5)` -> `1.0471975511965976`

Inputs: `x` (numeric) A single number in the range \[-1,1]

Output: Outputs the arc cosine of the input value in radians

![](<../../.gitbook/assets/image (17).png>)

</details>

<details>

<summary>acosh(x)</summary>

Calculates the inverse hyperbolic cosine of the supplied value in radians.

Example: Find the inverse hyperbolic cosine of 2: `acosh(2)` -> `1.3169578969248166`

INPUTS: `x` (numeric) A single number

OUTPUT: Outputs the inverse hyperbolic cosine of the input value

</details>

<details>

<summary>add(x, y)</summary>

Add 2 values together and return the answer

Ex: `add(5,7)` -> `12`

INPUTS: `x` (numeric), `y`(numeric) Two Numbers

OUTPUT: Outputs the sum of x and y

![](<../../.gitbook/assets/image (18).png>)

</details>

<details>

<summary>asin(x)</summary>

Calculates the arc sine of the supplied value in radians

Ex: `asin(0.5)` -> `0.5235987755982989`

INPUTS: `x` (numeric) A single number

OUTPUT: Outputs the arc sine of the input value in radiansa

</details>

<details>

<summary>asinh(x)</summary>

Calculates the inverse hyperbolic sine of the supplied value

Ex: `asinh(0.5)` -> `0.48121182505960347`

INPUTS: `x` (numeric) A single number

OUTPUT: Outputs the inverse hyperbolic sine of the input value

</details>

<details>

<summary>atan(x)</summary>

Calculates the arc tangent of the supplied value in radians

Ex: `atan(1)`-> `0.7853981633974483`

INPUTS: `x` (numeric) A single number

OUTPUT: Outputs the arc tangent of the input number in radianspa

</details>

<details>

<summary>atanh(x)</summary>

Calculates the inverse hyperbolic tangent of the supplied value in radians

Ex: `atanh(0.5)` -> `0.5493061443340548`

INPUTS: `x` (numeric) A single number

OUTPUT: Outputs the inverse hyperbolic tangent of the input number in radians

</details>

<details>

<summary>bitwise_and(x, y)</summary>

Bitwise AND 2 values together and return the answer

Ex: `bitwise_and(10, 2)` -> `2`

INPUTS: `x` (numeric), `y` (numeric) Two numbers

OUTPUT: Outputs the result of bitwise AND operation on the input numbers

![](<../../.gitbook/assets/image (19).png>)

</details>

<details>

<summary>bitwise_or(x, y)</summary>

Bitwise OR 2 values together and return the answer

Ex: `bitwise_or(10, 2)` -> `10`

INPUTS: `x` (numeric), `y` (numeric) Two numbers

OUTPUT: Outputs the result of bitwise OR operation on the input numbers

![](<../../.gitbook/assets/image (20).png>)

</details>

<details>

<summary>bitwise_xor(x, y)</summary>

Bitwise XOR 2 values together and return the answer

Ex: `bitwise_xor(10, 2)` -> `8`

INPUTS: `x` (numeric), `y` (numeric) Two numbers

OUTPUT: Outputs the result of bitwise XOR operation on the input numbers

![](<../../.gitbook/assets/image (21).png>)

</details>

<details>

<summary>ceil(x)</summary>

Round a decimal up to its integer equivalent.

Examples: Find the ceil of 2.6: `ceil(2.6)` -> `3`

INPUTS: `x` (numeric) A decimal number

OUTPUT: Outputs the smallest integer greater than or equal to x

![](<../../.gitbook/assets/image (22).png>)

</details>

<details>

<summary>cos(x)</summary>

Calculates the cosine of the supplied value in radians.

Examples: Find the cos of 2: `cos(2)` ->  `-0.416146836547142294`

INPUTS: `x` (numeric) A number in radians

OUTPUT: Outputs the cosine of the input number

</details>

<details>

<summary>deg2rad(x)</summary>

Convert degrees to radians.

Examples: Find the radians equivalent of 180 degrees: `deg2rad(180)`-> `3.141592653589793`

INPUTS: `x` (numeric) A number in degrees

OUTPUT: Outputs the radians equivalent of the input number in degrees

</details>

<details>

<summary>divide(x,y)</summary>

Divides two numbers and returns the result

Ex: `divide(10,2)` -> `5`

INPUTS: `x` (numeric), `y` (numeric) The numbers to be divided

OUTPUT: Outputs the result of x divided by y

![](<../../.gitbook/assets/image (23).png>)

</details>

<details>

<summary>exp(x)</summary>

Returns the value of the constant e raised to the power of x

Ex: `exp(2)` -> `7.38905609893065`

INPUTS: `x` (numeric) The exponent to raise e to

OUTPUT: Outputs the result of e raised to the power of x

![](<../../.gitbook/assets/image (24).png>)

</details>

<details>

<summary>floor(x)</summary>

Rounds a decimal down to its nearest integer

Ex: `floor(2.6)` -> `2`

INPUTS: `x` (numeric) The decimal number to be rounded

OUTPUT: Outputs the nearest integer that is less than or equal to x

![](<../../.gitbook/assets/image (25).png>)

</details>

<details>

<summary>min</summary>

Returns the minimum of two values

<img src="../../.gitbook/assets/CleanShot 2023-04-14 at 10.45.54.png" alt="" data-size="original">

</details>

<details>

<summary>max</summary>

Returns the maximum of two values

![](<../../.gitbook/assets/CleanShot 2023-04-14 at 10.46.51.png>)

</details>

<details>

<summary>modulus(x, y)</summary>

Returns the remainder of dividing x by y.

Ex: `modulus(7,3)` -> `1`

INPUTS: `x` (numeric), `y` (numeric) two numbers

OUTPUT: Outputs the remainder of x divided by y

![](<../../.gitbook/assets/image (26).png>)

</details>

<details>

<summary>multiply(x, y)</summary>

Multiply 2 values together and return the answer.

Ex: `multiply(2,3)` -> `6`

INPUTS: `x` (numeric), `y` (numeric) two numbers

OUTPUT: Outputs the product of the 2 input values

![](<../../.gitbook/assets/image (27).png>)

</details>

<details>

<summary>number_format(x, decimals, decimalpoint, separator)</summary>

Format a number with flexible support over decimal places, thousands separator, and decimal separator.

Ex: `number_format(123456789, 2, ".", ",")` -> `"123,456,789.12"`

INPUTS: `x` (numeric) A single number to be formatted, `decimals` (numeric) Number of decimal points, `decimalpoint` (string) Decimal point separator, `separator` (string) Thousands separator

OUTPUT: Outputs the formatted number

![](<../../.gitbook/assets/image (28).png>)

</details>

<details>

<summary>pow(x, exp)</summary>

Returns the value raised to the power of exp.

Ex: `pow(2,3)` -> `8`

INPUTS: `x` (numeric) A single number, the base `exp` (numeric) A single number, the exponent

OUTPUT: Outputs the base raised to the power of the exponent

![](<../../.gitbook/assets/image (29).png>)

</details>

<details>

<summary>rad2deg(x)</summary>

Convert radians to degrees.

Ex: `rad2deg(pi)` -> `180`

INPUTS: `x`(numeric) A single number in radians

OUTPUT: Outputs the input value converted to degrees

</details>

<details>

<summary>round(x, precision)</summary>

Round a decimal with optional precision.

Ex:  `round(3.14159265,3)` -> `3.142`

INPUTS: `x`(numeric) A single number to be rounded precision (numeric) Number of decimal places to round to

OUTPUT: Outputs the input value rounded to the specified number of decimal places

![](<../../.gitbook/assets/image (30).png>)

</details>

<details>

<summary>sin(x)</summary>

Calculates the sine of the supplied value in radians.

Ex: `sin(pi/2)` -> `1`

INPUTS: `x`sqrt(x) Returns the square root of the value

Examples: Find the square root of 9: sqrt(9) OUTPUT: 3

INPUTS: x (numeric) A single number

OUTPUT: Outputs the square root of the input value (numeric) A single number in radians

OUTPUT: Outputs the sine of the input value

</details>

<details>

<summary>sqrt(x)</summary>

Returns the square root of the value

Ex: `sqrt(9)` ->`3`

INPUTS: `x` (numeric) A single number

OUTPUT: Outputs the square root of the input value

![](<../../.gitbook/assets/image (31).png>)

</details>

<details>

<summary>subtract(x, y)</summary>

Subtract 2 values together and return the answer.

Ex: `subtract(10,5)` -> `5`

INPUTS: `x` (numeric), `y`(numeric) Two numbers

OUTPUT: Outputs the result of subtracting y from x

![](<../../.gitbook/assets/image (32).png>)

</details>

<details>

<summary>tan(x)</summary>

Calculates the tangent of the supplied value in radians.

Ex: `tan(pi/4)` -> `1`

INPUTS: `x` (numeric) A single number in radians

OUTPUT: Outputs the tangent of the input value



</details>

### Special Array Math Filters:

<details>

<summary>array_max</summary>

Finds the max value among the values of the array.

Ex: `max[2,5,3]` -> `5`

INPUTS: `array[x1, x2,...]` (array) an array of numbers to compare

OUTPUT: Outputs the largest number among the array.

![](<../../.gitbook/assets/image (33).png>)

</details>

<details>

<summary>array_min</summary>

Finds the minimum value among the values of the array.

Ex: `min[2,5,3]` -> `2`

INPUTS: `array[x1, x2,...]` (array) an array of numbers to compare

OUTPUT: Outputs the smallest number among the array.

![](<../../.gitbook/assets/image (34).png>)

</details>

<details>

<summary>Product</summary>

Returns the product of the values of the array.&#x20;

Ex: `product[2,5,3]` -> `30`

INPUTS: `array[x1, x2,...]` (array) an array of numbers

OUTPUT: Outputs the product of the values of the array.

![](<../../.gitbook/assets/image (35).png>)

</details>

<details>

<summary>Sum</summary>

Returns the sum of the values of the array.&#x20;

Ex: `sum[2,5,3]` -> 10

INPUTS: `array[x1, x2,...]` (array) an array of numbers

OUTPUT: Outputs the sum of the values of the array.

![](<../../.gitbook/assets/image (36).png>)

</details>
