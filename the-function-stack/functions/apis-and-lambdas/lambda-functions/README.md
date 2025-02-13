# Lambda Functions

## What are Lambda Functions?

Lambda functions allow you to execute Javascript inside of your Xano function stacks. You may prefer to do this if you are porting old workflows to Xano and already have the code written, or maybe you just prefer to write code instead of using the function stack.

## What can I do with a Lambda?

#### Special Variables <a href="#special-variables" id="special-variables"></a>

Lambdas have the ability to reference all the available data just like normal function stack statements. All special variables are prefixed with a `$` symbol.

* Xano variables are accessible through the `$var` special variable. To access a Xano variable named title, you would reference it as `$var.title`.
* Xano inputs are accessible through the `$input` special variable. To access a Xano input named score, you would reference it as `$input.score`.
* Xano environment variables are accessible through the `$env` special variable. To access a Xano environment variable named ip, you would reference it as `$env.ip`.
* The authenticated user details are accessible through the `$auth` special variable. The most common members of this variable include `$auth.id` and `$auth.extras`. If there is no authenticated user, then `$auth.id` will evaluate as 0.

#### Context Variables <a href="#context-variables" id="context-variables"></a>

Depending on how you use a Lambda, you may have support to access some additional variables, known as context variables. These follow the same naming convention as special variables by using a `$` prefix. The most common context variables will be `$this`, `$index`, `$parent`, and `$result`. The meaning of these variables are best described within the examples of the [higher order filters](https://docs.xano.com/the-function-stack/filters/transform#lambda-filters).

#### Libraries

Lambda functions give you access to powerful Javascript libraries that you can use throughout your code. A complete list of the available libraries and details on requesting new ones can be found [here](libraries.md).





