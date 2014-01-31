pass.js
=======

Javascript validation module. Runs from server or web, doesn't need a form.

Requires ```mocha``` and ```chai``` for running tests.

## Installation

You can install this module manually by just saving pass.js somewhere in your project and using ```require``` or ```<script>``` to pull it in.

Installing via npm:

```
npm install pass.js
```

## Usage

``` javascript
var pass = require('pass.js');

var rules,data,validator;

var first_name = "Billy";
var last_name = "Jones";
var email = "billyjones26@gmail.com";
var url = "http://theninthnode.com";
var password = "123";

rules = [
	["first_name", "required", "first name"], // var name, rules, label for error message (defaults to var name)
	["last_name", "required", "last name"],
	["email", "required,valid_email"],
	["url", "valid_url"],
	["password", "required,min_length:5"]
];

data = {
	first_name: first_name,	
	last_name: last_name,	
	email: email,	
	url: url,	
	password: password,	
};

validator = pass.validate(rules, data);

if(validator.failed()) {
	console.log(validator.message());
}
```

## Available Rules

* required
* matches
* valid_email
* min_length
* max_length
* exact_length
* greater_than
* less_than
* alpha
* alpha_numeric
* alpha_dash
* numeric
* integer
* decimal
* is_natural
* is_natural_no_zero
* valid_ip
* valid_base64
* valid_credit_card
* valid_url

## Methods

``` javascript
pass.validate(rules, data) // returns this object
pass.failed() // returns BOOL
pass.message() // returns first error message as string
pass.allMessages() // returns array of error message strings
```

## Contributions

Thanks to validate.js for the regex's and messages.

Inspired by Laravel's validator class.

Trim function - http://blog.stevenlevithan.com/archives/faster-trim-javascript