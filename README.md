# A fork of the official nodejs library for ClickSend v3 REST API

This is a fork of the official [ClickSend](https://clicksend.com) SDK. Documentation can be found [here](https://developers.clicksend.com/docs/rest/v3/?nodejs#introduction).

Differences from the offical version:
* Removes [bluebird](https://github.com/petkaantonov/bluebird) dependency as it isn't necessary for compiling.
* Distributes a compiled version of the package so compilation after installation is no longer necessary.
* Installs dependencies when installing (see [Issue #1](https://github.com/ClickSend/clicksend-nodejs/issues/1)).

## Requirements
  
- [Sign Up](https://www.clicksend.com/signup) for a free ClickSend account.
- Copy your API key from the [API Credentials](https://dashboard.clicksend.com/#/account/subaccount) area.

## Installation

### Downloading Package

To download the SDK into your package run the command:

```shell
npm i clicksend
```

### Adding SDK into your project

Copy the api.js file along with the node_modules directory into your project to use the library, and include this in your file to use the SDK:

```shell
var api = require('./node_modules/clicksend/api.js');
```

## Documentation

Documentation for our SDK and REST API can be found [here](https://developers.clicksend.com/docs/rest/v3/?nodejs#introduction).

## Getting Started (sms/send example)

Please follow the [installation](#installation) procedure and then run the following code:
```nodejs
var api = require('./api.js');

var smsMessage = new api.SmsMessage();

smsMessage.from = "myNumber";
smsMessage.to = "+0451111111";
smsMessage.body = "test message";

var smsApi = new api.SMSApi("username", "api_key");

var smsCollection = new api.SmsMessageCollection();

smsCollection.messages = [smsMessage];

smsApi.smsSendPost(smsCollection).then(function(response) {
	console.log(response.body);
}).catch(function(err){
	console.error(err.body);
});

```

