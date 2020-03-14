<h1 id="numbers-api">Numbers API v1</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

With the Global Phone Number Catalog, you get instant access to the breadth and depth of the communication options that exist in the phone numbers market, such as one-way numbers ideal for outbound use cases, or dual-function landline numbers for customer support messaging use cases. Starting today, you can search our full inventory through a new Phone Numbers API that provides:

Base URLs:

* <a href="https://numbers.sinch.com/v1">https://numbers.sinch.com/v1</a>

<h1 id="numbers-api-your-numbers">Your Numbers</h1>

## Buy Number

<a id="opIdBuyNumber"></a>

> Code samples

```shell
curl --request POST \
  --url https://numbers.sinch.com/v1/Account/string/ActiveNumbers/ \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"status_callback_url":"example.com","status_callback_method":"POST","voice":{"url":"example.com","method":"POST","fallback_url":"example.com","fallback_method":"POST","application_sid":"adrodierkyudikjnte8d77f9890ejkjf=="},"sms":{"url":"string","method":"POST","application_sid":"string"}}'
```

```java
HttpResponse<String> response = Unirest.post("https://numbers.sinch.com/v1/Account/string/ActiveNumbers/")
  .header("content-type", "application/json")
  .header("accept", "application/json")
  .body("{\"status_callback_url\":\"example.com\",\"status_callback_method\":\"POST\",\"voice\":{\"url\":\"example.com\",\"method\":\"POST\",\"fallback_url\":\"example.com\",\"fallback_method\":\"POST\",\"application_sid\":\"adrodierkyudikjnte8d77f9890ejkjf==\"},\"sms\":{\"url\":\"string\",\"method\":\"POST\",\"application_sid\":\"string\"}}")
  .asString();
```

```csharp
var client = new RestClient("https://numbers.sinch.com/v1/Account/string/ActiveNumbers/");
var request = new RestRequest(Method.POST);
request.AddHeader("accept", "application/json");
request.AddHeader("content-type", "application/json");
request.AddParameter("application/json", "{\"status_callback_url\":\"example.com\",\"status_callback_method\":\"POST\",\"voice\":{\"url\":\"example.com\",\"method\":\"POST\",\"fallback_url\":\"example.com\",\"fallback_method\":\"POST\",\"application_sid\":\"adrodierkyudikjnte8d77f9890ejkjf==\"},\"sms\":{\"url\":\"string\",\"method\":\"POST\",\"application_sid\":\"string\"}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "numbers.sinch.com",
  "port": null,
  "path": "/v1/Account/string/ActiveNumbers/",
  "headers": {
    "content-type": "application/json",
    "accept": "application/json"
  }
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.write(JSON.stringify({ status_callback_url: 'example.com',
  status_callback_method: 'POST',
  voice:
   { url: 'example.com',
     method: 'POST',
     fallback_url: 'example.com',
     fallback_method: 'POST',
     application_sid: 'adrodierkyudikjnte8d77f9890ejkjf==' },
  sms: { url: 'string', method: 'POST', application_sid: 'string' } }));
req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://numbers.sinch.com/v1/Account/string/ActiveNumbers/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"status_callback_url\":\"example.com\",\"status_callback_method\":\"POST\",\"voice\":{\"url\":\"example.com\",\"method\":\"POST\",\"fallback_url\":\"example.com\",\"fallback_method\":\"POST\",\"application_sid\":\"adrodierkyudikjnte8d77f9890ejkjf==\"},\"sms\":{\"url\":\"string\",\"method\":\"POST\",\"application_sid\":\"string\"}}",
  CURLOPT_HTTPHEADER => array(
    "accept: application/json",
    "content-type: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

`POST /Account/{AccountId}/ActiveNumbers/`

Purchases a new phone number for your account. If a phone number is found for your request, Twilio will add it to your account and bill you for the first month's cost of the phone number. If Twilio cannot find a phone number to match your request, you will receive an HTTP 400 with Twilio error code 21452. If the number you are trying to purchase requires an identity document on file and you don't have a verified identity document associated with your account, you will receive an HTTP 400 with Twilio error code 21650. See this support article for more details.

> Body parameter

```json
{
  "status_callback_url": "example.com",
  "status_callback_method": "POST",
  "voice": {
    "url": "example.com",
    "method": "POST",
    "fallback_url": "example.com",
    "fallback_method": "POST",
    "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
  },
  "sms": {
    "url": "string",
    "method": "POST",
    "application_sid": "string"
  }
}
```

<h3 id="buy-number-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|phoneNumber|query|string|false|none|
|AccountId|path|string|true|none|
|body|body|[Configuration](#schemaconfiguration)|false|none|

> Example responses

> 200 Response

```json
{
  "friendlyName": "string",
  "accountSid": "string",
  "statusCallback": "string",
  "statusCallbackMethod": "string",
  "configuration": {
    "status_callback_url": "example.com",
    "status_callback_method": "POST",
    "voice": {
      "url": "example.com",
      "method": "POST",
      "fallback_url": "example.com",
      "fallback_method": "POST",
      "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
    },
    "sms": {
      "url": "string",
      "method": "POST",
      "application_sid": "string"
    }
  },
  "phone_number": "+15551231212",
  "type": "string",
  "base_setup_price": "2.0",
  "base_recurring_price": "2.0",
  "capabilities": {
    "voice": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "e911": true,
      "sip_trunking": true,
      "calls_per_second": 0,
      "concurrent_calls_limit": 0,
      "inbound_called_dtmf": true,
      "inbound_caller_dtmf": true,
      "inbound_caller_id_preservation": "string",
      "inbound_reachability": "string"
    },
    "sms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "gsm7": true,
      "ucs2": true,
      "gsm7_concatenation": true,
      "ucs2_concatenation": true,
      "inbound_sender_id_preservation": "string",
      "inbound_reachability": "string",
      "inbound_mps": 0
    },
    "mms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "inbound_reachability": "string",
      "inbound_mps": 0
    }
  },
  "regulatory": {
    "address_requirements": "any"
  },
  "lifecycle": "string",
  "geography": {
    "iso_country": "string",
    "lata": "string",
    "rate_center": "string",
    "latitude": "string",
    "longitude": "string",
    "region": "string",
    "locality": "string",
    "postal_code": "string"
  }
}
```

<h3 id="buy-number-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ActiveNumber](#schemaactivenumber)|

<aside class="success">
This operation does not require authentication
</aside>

## List Numbers

<a id="opIdlistActiveNumbers"></a>

> Code samples

```shell
curl --request GET \
  --url https://numbers.sinch.com/v1/Account/string/ActiveNumbers/ \
  --header 'accept: application/json'
```

```java
HttpResponse<String> response = Unirest.get("https://numbers.sinch.com/v1/Account/string/ActiveNumbers/")
  .header("accept", "application/json")
  .asString();
```

```csharp
var client = new RestClient("https://numbers.sinch.com/v1/Account/string/ActiveNumbers/");
var request = new RestRequest(Method.GET);
request.AddHeader("accept", "application/json");
IRestResponse response = client.Execute(request);
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "numbers.sinch.com",
  "port": null,
  "path": "/v1/Account/string/ActiveNumbers/",
  "headers": {
    "accept": "application/json"
  }
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://numbers.sinch.com/v1/Account/string/ActiveNumbers/",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "accept: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

`GET /Account/{AccountId}/ActiveNumbers/`

Returns a list of ActiveNumber resource representations, each representing a phone number given to your account. The list includes paging information.

<h3 id="list-numbers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|AccountId|path|string|true|AccountID the numbers is connected to|
|Configuration.voice.application_sid|query|string|false|none|
|phone_number|query|string|false|The phone number, in [E.164](https://en.wikipedia.org/wiki/E.164) (i.e. "+1") format.|
|geography.iso_country|query|string|false|The [ISO](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code of this phone number.|
|geography.lata|query|string|false|The [rate center](http://en.wikipedia.org/wiki/Local_access_and_transport_area) of this phone number. Only available for countries in the [North American Numbering Plan (NANPA)](https://en.wikipedia.org/wiki/North_American_Numbering_Plan).|
|geography.rate_center|query|string|false|/// The [LATA](http://en.wikipedia.org/wiki/Telephone_exchange) of this phone number. Only available for countries in the [North American Numbering Plan (NANPA)](https://en.wikipedia.org/wiki/North_American_Numbering_Plan).|
|geography.latitude|query|string|false|The latitude coordinate of this phone number.|
|geography.longitude|query|string|false|The longitude coordinate of this phone number.|
|geography.region|query|string|false|The two-letter state or province abbreviation of this phone number.|
|geography.locality|query|string|false|The locality/city of this phone number.|
|geography.postal_code|query|string|false|The postal (zip) code of this phone number.|

> Example responses

> 200 Response

```json
{
  "items": [
    {
      "friendlyName": "string",
      "accountSid": "string",
      "statusCallback": "string",
      "statusCallbackMethod": "string",
      "configuration": {
        "status_callback_url": "example.com",
        "status_callback_method": "POST",
        "voice": {
          "url": "example.com",
          "method": "POST",
          "fallback_url": "example.com",
          "fallback_method": "POST",
          "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
        },
        "sms": {
          "url": "string",
          "method": "POST",
          "application_sid": "string"
        }
      },
      "phone_number": "+15551231212",
      "type": "string",
      "base_setup_price": "2.0",
      "base_recurring_price": "2.0",
      "capabilities": {
        "voice": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "e911": true,
          "sip_trunking": true,
          "calls_per_second": 0,
          "concurrent_calls_limit": 0,
          "inbound_called_dtmf": true,
          "inbound_caller_dtmf": true,
          "inbound_caller_id_preservation": "string",
          "inbound_reachability": "string"
        },
        "sms": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "gsm7": true,
          "ucs2": true,
          "gsm7_concatenation": true,
          "ucs2_concatenation": true,
          "inbound_sender_id_preservation": "string",
          "inbound_reachability": "string",
          "inbound_mps": 0
        },
        "mms": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "inbound_reachability": "string",
          "inbound_mps": 0
        }
      },
      "regulatory": {
        "address_requirements": "any"
      },
      "lifecycle": "string",
      "geography": {
        "iso_country": "string",
        "lata": "string",
        "rate_center": "string",
        "latitude": "string",
        "longitude": "string",
        "region": "string",
        "locality": "string",
        "postal_code": "string"
      }
    }
  ],
  "meta": {
    "page": 0,
    "page_size": 0,
    "first_page_url": "string",
    "previous_page_url": "string",
    "url": "string",
    "next_page_url": "string",
    "key": "string"
  }
}
```

<h3 id="list-numbers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ActiveNumbersResponse](#schemaactivenumbersresponse)|

<aside class="success">
This operation does not require authentication
</aside>

## Get number

<a id="opIdGetActiveNumber"></a>

> Code samples

```shell
curl --request GET \
  --url https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring \
  --header 'accept: application/json'
```

```java
HttpResponse<String> response = Unirest.get("https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring")
  .header("accept", "application/json")
  .asString();
```

```csharp
var client = new RestClient("https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring");
var request = new RestRequest(Method.GET);
request.AddHeader("accept", "application/json");
IRestResponse response = client.Execute(request);
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "numbers.sinch.com",
  "port": null,
  "path": "/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring",
  "headers": {
    "accept": "application/json"
  }
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "accept: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

`GET /Accounts/{AccountId}/ActiveNumbers/ActiveNumbers/PN{phoneNumber}`

An ActiveNumbers instance represents a Twilio phone number purchased from Twilio, ported to Twilio, or hosted on Twilio in your account.

<h3 id="get-number-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|AccountId|path|string|true|none|
|phoneNumber|path|string|true|none|

> Example responses

> 200 Response

```json
{
  "friendlyName": "string",
  "accountSid": "string",
  "statusCallback": "string",
  "statusCallbackMethod": "string",
  "configuration": {
    "status_callback_url": "example.com",
    "status_callback_method": "POST",
    "voice": {
      "url": "example.com",
      "method": "POST",
      "fallback_url": "example.com",
      "fallback_method": "POST",
      "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
    },
    "sms": {
      "url": "string",
      "method": "POST",
      "application_sid": "string"
    }
  },
  "phone_number": "+15551231212",
  "type": "string",
  "base_setup_price": "2.0",
  "base_recurring_price": "2.0",
  "capabilities": {
    "voice": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "e911": true,
      "sip_trunking": true,
      "calls_per_second": 0,
      "concurrent_calls_limit": 0,
      "inbound_called_dtmf": true,
      "inbound_caller_dtmf": true,
      "inbound_caller_id_preservation": "string",
      "inbound_reachability": "string"
    },
    "sms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "gsm7": true,
      "ucs2": true,
      "gsm7_concatenation": true,
      "ucs2_concatenation": true,
      "inbound_sender_id_preservation": "string",
      "inbound_reachability": "string",
      "inbound_mps": 0
    },
    "mms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "inbound_reachability": "string",
      "inbound_mps": 0
    }
  },
  "regulatory": {
    "address_requirements": "any"
  },
  "lifecycle": "string",
  "geography": {
    "iso_country": "string",
    "lata": "string",
    "rate_center": "string",
    "latitude": "string",
    "longitude": "string",
    "region": "string",
    "locality": "string",
    "postal_code": "string"
  }
}
```

<h3 id="get-number-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ActiveNumber](#schemaactivenumber)|

<aside class="success">
This operation does not require authentication
</aside>

## Configure number

<a id="opIdUpdateActiveNumber"></a>

> Code samples

```shell
curl --request POST \
  --url https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{"friendlyName":"string","accountSid":"string","statusCallback":"string","statusCallbackMethod":"string","configuration":{"status_callback_url":"example.com","status_callback_method":"POST","voice":{"url":"example.com","method":"POST","fallback_url":"example.com","fallback_method":"POST","application_sid":"adrodierkyudikjnte8d77f9890ejkjf=="},"sms":{"url":"string","method":"POST","application_sid":"string"}},"phone_number":"+15551231212","type":"string","base_setup_price":"2.0","base_recurring_price":"2.0","capabilities":{"voice":{"inbound_connectivity":true,"outbound_connectivity":true,"e911":true,"sip_trunking":true,"calls_per_second":0,"concurrent_calls_limit":0,"inbound_called_dtmf":true,"inbound_caller_dtmf":true,"inbound_caller_id_preservation":"string","inbound_reachability":"string"},"sms":{"inbound_connectivity":true,"outbound_connectivity":true,"gsm7":true,"ucs2":true,"gsm7_concatenation":true,"ucs2_concatenation":true,"inbound_sender_id_preservation":"string","inbound_reachability":"string","inbound_mps":0},"mms":{"inbound_connectivity":true,"outbound_connectivity":true,"inbound_reachability":"string","inbound_mps":0}},"regulatory":{"address_requirements":"any"},"lifecycle":"string","geography":{"iso_country":"string","lata":"string","rate_center":"string","latitude":"string","longitude":"string","region":"string","locality":"string","postal_code":"string"}}'
```

```java
HttpResponse<String> response = Unirest.post("https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring")
  .header("content-type", "application/json")
  .header("accept", "application/json")
  .body("{\"friendlyName\":\"string\",\"accountSid\":\"string\",\"statusCallback\":\"string\",\"statusCallbackMethod\":\"string\",\"configuration\":{\"status_callback_url\":\"example.com\",\"status_callback_method\":\"POST\",\"voice\":{\"url\":\"example.com\",\"method\":\"POST\",\"fallback_url\":\"example.com\",\"fallback_method\":\"POST\",\"application_sid\":\"adrodierkyudikjnte8d77f9890ejkjf==\"},\"sms\":{\"url\":\"string\",\"method\":\"POST\",\"application_sid\":\"string\"}},\"phone_number\":\"+15551231212\",\"type\":\"string\",\"base_setup_price\":\"2.0\",\"base_recurring_price\":\"2.0\",\"capabilities\":{\"voice\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"e911\":true,\"sip_trunking\":true,\"calls_per_second\":0,\"concurrent_calls_limit\":0,\"inbound_called_dtmf\":true,\"inbound_caller_dtmf\":true,\"inbound_caller_id_preservation\":\"string\",\"inbound_reachability\":\"string\"},\"sms\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"gsm7\":true,\"ucs2\":true,\"gsm7_concatenation\":true,\"ucs2_concatenation\":true,\"inbound_sender_id_preservation\":\"string\",\"inbound_reachability\":\"string\",\"inbound_mps\":0},\"mms\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"inbound_reachability\":\"string\",\"inbound_mps\":0}},\"regulatory\":{\"address_requirements\":\"any\"},\"lifecycle\":\"string\",\"geography\":{\"iso_country\":\"string\",\"lata\":\"string\",\"rate_center\":\"string\",\"latitude\":\"string\",\"longitude\":\"string\",\"region\":\"string\",\"locality\":\"string\",\"postal_code\":\"string\"}}")
  .asString();
```

```csharp
var client = new RestClient("https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring");
var request = new RestRequest(Method.POST);
request.AddHeader("accept", "application/json");
request.AddHeader("content-type", "application/json");
request.AddParameter("application/json", "{\"friendlyName\":\"string\",\"accountSid\":\"string\",\"statusCallback\":\"string\",\"statusCallbackMethod\":\"string\",\"configuration\":{\"status_callback_url\":\"example.com\",\"status_callback_method\":\"POST\",\"voice\":{\"url\":\"example.com\",\"method\":\"POST\",\"fallback_url\":\"example.com\",\"fallback_method\":\"POST\",\"application_sid\":\"adrodierkyudikjnte8d77f9890ejkjf==\"},\"sms\":{\"url\":\"string\",\"method\":\"POST\",\"application_sid\":\"string\"}},\"phone_number\":\"+15551231212\",\"type\":\"string\",\"base_setup_price\":\"2.0\",\"base_recurring_price\":\"2.0\",\"capabilities\":{\"voice\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"e911\":true,\"sip_trunking\":true,\"calls_per_second\":0,\"concurrent_calls_limit\":0,\"inbound_called_dtmf\":true,\"inbound_caller_dtmf\":true,\"inbound_caller_id_preservation\":\"string\",\"inbound_reachability\":\"string\"},\"sms\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"gsm7\":true,\"ucs2\":true,\"gsm7_concatenation\":true,\"ucs2_concatenation\":true,\"inbound_sender_id_preservation\":\"string\",\"inbound_reachability\":\"string\",\"inbound_mps\":0},\"mms\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"inbound_reachability\":\"string\",\"inbound_mps\":0}},\"regulatory\":{\"address_requirements\":\"any\"},\"lifecycle\":\"string\",\"geography\":{\"iso_country\":\"string\",\"lata\":\"string\",\"rate_center\":\"string\",\"latitude\":\"string\",\"longitude\":\"string\",\"region\":\"string\",\"locality\":\"string\",\"postal_code\":\"string\"}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```javascript--node
var http = require("https");

var options = {
  "method": "POST",
  "hostname": "numbers.sinch.com",
  "port": null,
  "path": "/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring",
  "headers": {
    "content-type": "application/json",
    "accept": "application/json"
  }
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.write(JSON.stringify({ friendlyName: 'string',
  accountSid: 'string',
  statusCallback: 'string',
  statusCallbackMethod: 'string',
  configuration:
   { status_callback_url: 'example.com',
     status_callback_method: 'POST',
     voice:
      { url: 'example.com',
        method: 'POST',
        fallback_url: 'example.com',
        fallback_method: 'POST',
        application_sid: 'adrodierkyudikjnte8d77f9890ejkjf==' },
     sms: { url: 'string', method: 'POST', application_sid: 'string' } },
  phone_number: '+15551231212',
  type: 'string',
  base_setup_price: '2.0',
  base_recurring_price: '2.0',
  capabilities:
   { voice:
      { inbound_connectivity: true,
        outbound_connectivity: true,
        e911: true,
        sip_trunking: true,
        calls_per_second: 0,
        concurrent_calls_limit: 0,
        inbound_called_dtmf: true,
        inbound_caller_dtmf: true,
        inbound_caller_id_preservation: 'string',
        inbound_reachability: 'string' },
     sms:
      { inbound_connectivity: true,
        outbound_connectivity: true,
        gsm7: true,
        ucs2: true,
        gsm7_concatenation: true,
        ucs2_concatenation: true,
        inbound_sender_id_preservation: 'string',
        inbound_reachability: 'string',
        inbound_mps: 0 },
     mms:
      { inbound_connectivity: true,
        outbound_connectivity: true,
        inbound_reachability: 'string',
        inbound_mps: 0 } },
  regulatory: { address_requirements: 'any' },
  lifecycle: 'string',
  geography:
   { iso_country: 'string',
     lata: 'string',
     rate_center: 'string',
     latitude: 'string',
     longitude: 'string',
     region: 'string',
     locality: 'string',
     postal_code: 'string' } }));
req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "{\"friendlyName\":\"string\",\"accountSid\":\"string\",\"statusCallback\":\"string\",\"statusCallbackMethod\":\"string\",\"configuration\":{\"status_callback_url\":\"example.com\",\"status_callback_method\":\"POST\",\"voice\":{\"url\":\"example.com\",\"method\":\"POST\",\"fallback_url\":\"example.com\",\"fallback_method\":\"POST\",\"application_sid\":\"adrodierkyudikjnte8d77f9890ejkjf==\"},\"sms\":{\"url\":\"string\",\"method\":\"POST\",\"application_sid\":\"string\"}},\"phone_number\":\"+15551231212\",\"type\":\"string\",\"base_setup_price\":\"2.0\",\"base_recurring_price\":\"2.0\",\"capabilities\":{\"voice\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"e911\":true,\"sip_trunking\":true,\"calls_per_second\":0,\"concurrent_calls_limit\":0,\"inbound_called_dtmf\":true,\"inbound_caller_dtmf\":true,\"inbound_caller_id_preservation\":\"string\",\"inbound_reachability\":\"string\"},\"sms\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"gsm7\":true,\"ucs2\":true,\"gsm7_concatenation\":true,\"ucs2_concatenation\":true,\"inbound_sender_id_preservation\":\"string\",\"inbound_reachability\":\"string\",\"inbound_mps\":0},\"mms\":{\"inbound_connectivity\":true,\"outbound_connectivity\":true,\"inbound_reachability\":\"string\",\"inbound_mps\":0}},\"regulatory\":{\"address_requirements\":\"any\"},\"lifecycle\":\"string\",\"geography\":{\"iso_country\":\"string\",\"lata\":\"string\",\"rate_center\":\"string\",\"latitude\":\"string\",\"longitude\":\"string\",\"region\":\"string\",\"locality\":\"string\",\"postal_code\":\"string\"}}",
  CURLOPT_HTTPHEADER => array(
    "accept: application/json",
    "content-type: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

`POST /Accounts/{AccountId}/ActiveNumbers/ActiveNumbers/PN{phoneNumber}`

Configure your number using the post method on the phone number instance with the possible optional parameters.

> Body parameter

```json
{
  "friendlyName": "string",
  "accountSid": "string",
  "statusCallback": "string",
  "statusCallbackMethod": "string",
  "configuration": {
    "status_callback_url": "example.com",
    "status_callback_method": "POST",
    "voice": {
      "url": "example.com",
      "method": "POST",
      "fallback_url": "example.com",
      "fallback_method": "POST",
      "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
    },
    "sms": {
      "url": "string",
      "method": "POST",
      "application_sid": "string"
    }
  },
  "phone_number": "+15551231212",
  "type": "string",
  "base_setup_price": "2.0",
  "base_recurring_price": "2.0",
  "capabilities": {
    "voice": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "e911": true,
      "sip_trunking": true,
      "calls_per_second": 0,
      "concurrent_calls_limit": 0,
      "inbound_called_dtmf": true,
      "inbound_caller_dtmf": true,
      "inbound_caller_id_preservation": "string",
      "inbound_reachability": "string"
    },
    "sms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "gsm7": true,
      "ucs2": true,
      "gsm7_concatenation": true,
      "ucs2_concatenation": true,
      "inbound_sender_id_preservation": "string",
      "inbound_reachability": "string",
      "inbound_mps": 0
    },
    "mms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "inbound_reachability": "string",
      "inbound_mps": 0
    }
  },
  "regulatory": {
    "address_requirements": "any"
  },
  "lifecycle": "string",
  "geography": {
    "iso_country": "string",
    "lata": "string",
    "rate_center": "string",
    "latitude": "string",
    "longitude": "string",
    "region": "string",
    "locality": "string",
    "postal_code": "string"
  }
}
```

<h3 id="configure-number-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|AccountId|path|string|true|none|
|phoneNumber|path|string|true|none|
|body|body|[ActiveNumber](#schemaactivenumber)|false|none|

> Example responses

> 200 Response

```json
{
  "friendlyName": "string",
  "accountSid": "string",
  "statusCallback": "string",
  "statusCallbackMethod": "string",
  "configuration": {
    "status_callback_url": "example.com",
    "status_callback_method": "POST",
    "voice": {
      "url": "example.com",
      "method": "POST",
      "fallback_url": "example.com",
      "fallback_method": "POST",
      "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
    },
    "sms": {
      "url": "string",
      "method": "POST",
      "application_sid": "string"
    }
  },
  "phone_number": "+15551231212",
  "type": "string",
  "base_setup_price": "2.0",
  "base_recurring_price": "2.0",
  "capabilities": {
    "voice": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "e911": true,
      "sip_trunking": true,
      "calls_per_second": 0,
      "concurrent_calls_limit": 0,
      "inbound_called_dtmf": true,
      "inbound_caller_dtmf": true,
      "inbound_caller_id_preservation": "string",
      "inbound_reachability": "string"
    },
    "sms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "gsm7": true,
      "ucs2": true,
      "gsm7_concatenation": true,
      "ucs2_concatenation": true,
      "inbound_sender_id_preservation": "string",
      "inbound_reachability": "string",
      "inbound_mps": 0
    },
    "mms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "inbound_reachability": "string",
      "inbound_mps": 0
    }
  },
  "regulatory": {
    "address_requirements": "any"
  },
  "lifecycle": "string",
  "geography": {
    "iso_country": "string",
    "lata": "string",
    "rate_center": "string",
    "latitude": "string",
    "longitude": "string",
    "region": "string",
    "locality": "string",
    "postal_code": "string"
  }
}
```

<h3 id="configure-number-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[ActiveNumber](#schemaactivenumber)|

<aside class="success">
This operation does not require authentication
</aside>

## Release number

<a id="opIdCancelActiveNumber"></a>

> Code samples

```shell
curl --request DELETE \
  --url https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring
```

```java
HttpResponse<String> response = Unirest.delete("https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring")
  .asString();
```

```csharp
var client = new RestClient("https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring");
var request = new RestRequest(Method.DELETE);
IRestResponse response = client.Execute(request);
```

```javascript--node
var http = require("https");

var options = {
  "method": "DELETE",
  "hostname": "numbers.sinch.com",
  "port": null,
  "path": "/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring",
  "headers": {}
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://numbers.sinch.com/v1/Accounts/string/ActiveNumbers/ActiveNumbers/PNstring",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "DELETE",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

`DELETE /Accounts/{AccountId}/ActiveNumbers/ActiveNumbers/PN{phoneNumber}`

Release this phone number from your account. Twilio will no longer answer calls to this number, and you will stop being billed the monthly phone number fee. The phone number will eventually be recycled and potentially given to another customer, so use with care. If you make a mistake, contact us. We may be able to give you the number back.

<h3 id="release-number-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|AccountId|path|string|true|none|
|phoneNumber|path|string|true|none|

<h3 id="release-number-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|None|

<aside class="success">
This operation does not require authentication
</aside>

<h1 id="numbers-api-number-catalog">Number Catalog</h1>

## Search numbers

<a id="opIdSearchNumbers"></a>

> Code samples

```shell
curl --request GET \
  --url https://numbers.sinch.com/v1/api/AvailableNumbers \
  --header 'accept: application/json'
```

```java
HttpResponse<String> response = Unirest.get("https://numbers.sinch.com/v1/api/AvailableNumbers")
  .header("accept", "application/json")
  .asString();
```

```csharp
var client = new RestClient("https://numbers.sinch.com/v1/api/AvailableNumbers");
var request = new RestRequest(Method.GET);
request.AddHeader("accept", "application/json");
IRestResponse response = client.Execute(request);
```

```javascript--node
var http = require("https");

var options = {
  "method": "GET",
  "hostname": "numbers.sinch.com",
  "port": null,
  "path": "/v1/api/AvailableNumbers",
  "headers": {
    "accept": "application/json"
  }
};

var req = http.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function () {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://numbers.sinch.com/v1/api/AvailableNumbers",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "accept: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

`GET /api/AvailableNumbers`

You can make a request directly to AvailableNumbers instance resource and choose from any of the numbers that appear in the search as a result of the filters you've specified.

<h3 id="search-numbers-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|phone_number|query|string|false|The phone number, in [E.164](https://en.wikipedia.org/wiki/E.164) (i.e. "+1") format.|
|type|query|string|false|The type of phone number (i.e., local, mobile, tollfree, shortcode, etc.)|
|base_setup_price|query|string|false|Setup fee for number|
|base_recurring_price|query|string|false|Montlhly fee for number|
|capabilities.Voice.inbound_connectivity|query|boolean|false|Indicates whether a number has inbound voice connectivity in to Twilio|
|capabilities.Voice.outbound_connectivity|query|boolean|false|Indicates whether a number has outbound voice connectivity out of Twilio|
|capabilities.Voice.e911|query|boolean|false|[Emergency 911][e911] connectivity capable number|
|capabilities.Voice.sip_trunking|query|boolean|false|Capabilities.Voice.SipTrunking|
|capabilities.Voice.calls_per_second|query|integer(int32)|false|Integer stating how many calls can be initiated per second. Please refer to Twilio's CPS Support article for more information.|
|capabilities.Voice.concurrent_calls_limit|query|integer(int32)|false|Integer stating how many calls can be active at one time|
|capabilities.Voice.inbound_called_dtmf|query|boolean|false|Dual-Tone Multi Frequency with inbound called party|
|capabilities.Voice.inbound_caller_dtmf|query|boolean|false|Dual-Tone Multi Frequency with inbound caller party|
|capabilities.Voice.inbound_caller_id_preservation|query|string|false|Inbound voice Caller ID (+E.164 format) preservation of a number. Can be - International, Domestic, or None.|
|capabilities.Voice.inbound_reachability|query|string|false|Inbound Voice reachability of a number. Can be - Domestic, Foreign, or Global|
|capabilities.SMS.inbound_connectivity|query|boolean|false|Indicates whether a number has inbound sms connectivity in to Twilio|
|capabilities.SMS.outbound_connectivity|query|boolean|false|Indicates whether a number has outbound sms connectivity out of Twilio|
|capabilities.SMS.gsm7|query|boolean|false|GSM-7 is a character encoding standard which packs the most commonly used letters and symbols in many languages into 7 bits each for usage on GSM networks. See What is GSM-7 Character Encoding|
|capabilities.SMS.ucs2|query|boolean|false|UCS-2 is a character encoding standard in which characters are represented by a fixed-length 16 bits (2 bytes). See What is UCS-2 Character Encoding?|
|capabilities.SMS.gsm7_concatenation|query|boolean|false|Concatenated short message service (or concatenated SMS) is used overcome the limitation on the number of characters that can be sent in a single SMS text message transmission (which is usually 160), and split the sms into smaller messages by the sending device and recombined at the receiving end.|
|capabilities.SMS.ucs2_concatenation|query|boolean|false|Concatenated short message service (or concatenated SMS) is used overcome the limitation on the number of characters that can be sent in a single SMS text message transmission (which is usually 160), and split the sms into smaller messages by the sending device and recombined at the receiving end.|
|capabilities.SMS.inbound_sender_id_preservation|query|string|false|Inbound voice Sender ID (+E.164 format) preservation of a number. Can be - International, Domestic, or None|
|capabilities.SMS.inbound_reachability|query|string|false|Inbound SMS reachability of a number. Can be - Domestic, Foreign, or Global.|
|capabilities.SMS.inbound_mps|query|integer(int32)|false|Integer showing the SMS inbound message per second limit. Please refer to Twilio's MPS Support article for more information.|
|capabilities.MMS.inbound_connectivity|query|boolean|false|Indicates whether a number has inbound MMS connectivity into Twilio|
|capabilities.MMS.outbound_connectivity|query|boolean|false|Indicates whether a number has outbound MMS connectivity into Twilio|
|capabilities.MMS.inbound_reachability|query|string|false|Inbound MMS reachability of a number. Can be - Domestic, Foreign, or Global.|
|capabilities.MMS.inbound_mps|query|integer(int32)|false|Integer showing the MMS inbound message per second limit. Please refer to Twilio's MPS Support article for more information.|
|regulatory.address_requirements|query|string|false|The following are the possible values for the address_required property.
|
|lifecycle|query|string|false|The lifecycle the number is in (i.e., developer-preview, beta, generally-available, exhausted).|
|geography.iso_country|query|string|false|The [ISO](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code of this phone number.|
|geography.lata|query|string|false|The [rate center](http://en.wikipedia.org/wiki/Local_access_and_transport_area) of this phone number. Only available for countries in the [North American Numbering Plan (NANPA)](https://en.wikipedia.org/wiki/North_American_Numbering_Plan).|
|geography.rate_center|query|string|false|/// The [LATA](http://en.wikipedia.org/wiki/Telephone_exchange) of this phone number. Only available for countries in the [North American Numbering Plan (NANPA)](https://en.wikipedia.org/wiki/North_American_Numbering_Plan).|
|geography.latitude|query|string|false|The latitude coordinate of this phone number.|
|geography.longitude|query|string|false|The longitude coordinate of this phone number.|
|geography.region|query|string|false|The two-letter state or province abbreviation of this phone number.|
|geography.locality|query|string|false|The locality/city of this phone number.|
|geography.postal_code|query|string|false|The postal (zip) code of this phone number.|

#### Detailed descriptions

**regulatory.address_requirements**: The following are the possible values for the address_required property.
|Status|Description|
|none|An Address is not required for this phone number.|
|any|Your account must have an Address, but it can be anywhere in the world.|
|local|Your account must have an Address within the phone number's country.|
|foreign|Your account must have an Address outside the phone number's country.|

> Example responses

> 200 Response

```json
{
  "items": [
    {
      "phone_number": "+15551231212",
      "type": "string",
      "base_setup_price": "2.0",
      "base_recurring_price": "2.0",
      "capabilities": {
        "voice": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "e911": true,
          "sip_trunking": true,
          "calls_per_second": 0,
          "concurrent_calls_limit": 0,
          "inbound_called_dtmf": true,
          "inbound_caller_dtmf": true,
          "inbound_caller_id_preservation": "string",
          "inbound_reachability": "string"
        },
        "sms": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "gsm7": true,
          "ucs2": true,
          "gsm7_concatenation": true,
          "ucs2_concatenation": true,
          "inbound_sender_id_preservation": "string",
          "inbound_reachability": "string",
          "inbound_mps": 0
        },
        "mms": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "inbound_reachability": "string",
          "inbound_mps": 0
        }
      },
      "regulatory": {
        "address_requirements": "any"
      },
      "lifecycle": "string",
      "geography": {
        "iso_country": "string",
        "lata": "string",
        "rate_center": "string",
        "latitude": "string",
        "longitude": "string",
        "region": "string",
        "locality": "string",
        "postal_code": "string"
      }
    }
  ],
  "meta": {
    "page": 0,
    "page_size": 0,
    "first_page_url": "string",
    "previous_page_url": "string",
    "url": "string",
    "next_page_url": "string",
    "key": "string"
  }
}
```

<h3 id="search-numbers-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Success|[AvailableNumbersResponse](#schemaavailablenumbersresponse)|

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

<h2 id="tocSvoice">Voice</h2>

<a id="schemavoice"></a>

```json
{
  "url": "example.com",
  "method": "POST",
  "fallback_url": "example.com",
  "fallback_method": "POST",
  "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|url|string(hostname)\|null|false|none|The URL Twilio will request when this phone number receives a call. The VoiceURL will no longer be used if a VoiceApplicationSid or a TrunkSid is set.|
|method|string\|null|false|none|The HTTP method Twilio will use when requesting the above Url. Either GET or POST.The URL that Twilio will request if an error occurs retrieving or executing the TwiML requested by Url.|
|fallback_url|string(hostname)\|null|false|none|The URL that Twilio will request if an error occurs retrieving or executing the TwiML requested by Url.|
|fallback_method|string\|null|false|none|The HTTP method Twilio will use when requesting the VoiceFallbackUrl. Either GET or POST.|
|application_sid|string\|null|false|none|The 34 character sid of the voice application Twilio should use to handle Voice sent to this number. If an VoiceApplicationSid is present, Twilio will ignore all of the VoiceUrls above and use those set on the application.|

#### Enumerated Values

|Property|Value|
|---|---|
|method|POST|
|method|GET|
|fallback_method|POST|
|fallback_method|GET|

<h2 id="tocSsms">Sms</h2>

<a id="schemasms"></a>

```json
{
  "url": "string",
  "method": "POST",
  "application_sid": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|url|string\|null|false|none|The URL Twilio will request when this phone number receives a message. The SmsUrl will no longer be used if an SmsApplicationSid is set.|
|method|string\|null|false|none|The HTTP method Twilio will use when requesting the callbackurl. Either GET or POST.|
|application_sid|string\|null|false|none|The 34 character sid of the voice application Twilio should use to handle Voice sent to this number. If an VoiceApplicationSid is present, Twilio will ignore all of the VoiceUrls above and use those set on the application.|

#### Enumerated Values

|Property|Value|
|---|---|
|method|POST|
|method|GET|

<h2 id="tocSconfiguration">Configuration</h2>

<a id="schemaconfiguration"></a>

```json
{
  "status_callback_url": "example.com",
  "status_callback_method": "POST",
  "voice": {
    "url": "example.com",
    "method": "POST",
    "fallback_url": "example.com",
    "fallback_method": "POST",
    "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
  },
  "sms": {
    "url": "string",
    "method": "POST",
    "application_sid": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|status_callback_url|string\|null|false|none|Url for status updates not related to a particular service.|
|status_callback_method|string\|null|false|none|none|
|voice|[Voice](#schemavoice)|false|none|none|
|sms|[Sms](#schemasms)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|status_callback_method|POST|
|status_callback_method|GET|

<h2 id="tocSvoicecapabilities">VoiceCapabilities</h2>

<a id="schemavoicecapabilities"></a>

```json
{
  "inbound_connectivity": true,
  "outbound_connectivity": true,
  "e911": true,
  "sip_trunking": true,
  "calls_per_second": 0,
  "concurrent_calls_limit": 0,
  "inbound_called_dtmf": true,
  "inbound_caller_dtmf": true,
  "inbound_caller_id_preservation": "string",
  "inbound_reachability": "string"
}

```

*Voice calling is provided by utilizing the Public Switch Telephone Network (PSTN) , the aggregate of the world's circuit-switched telephone networks that are operated by national, regional, or local telephony operators, providing infrastructure and services for public telecommunication.*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|inbound_connectivity|boolean|false|none|Indicates whether a number has inbound voice connectivity in to Twilio|
|outbound_connectivity|boolean|false|none|Indicates whether a number has outbound voice connectivity out of Twilio|
|e911|boolean|false|none|[Emergency 911][e911] connectivity capable number|
|sip_trunking|boolean|false|none|Capabilities.Voice.SipTrunking|
|calls_per_second|integer(int32)|false|none|Integer stating how many calls can be initiated per second. Please refer to Twilio's CPS Support article for more information.|
|concurrent_calls_limit|integer(int32)|false|none|Integer stating how many calls can be active at one time|
|inbound_called_dtmf|boolean|false|none|Dual-Tone Multi Frequency with inbound called party|
|inbound_caller_dtmf|boolean|false|none|Dual-Tone Multi Frequency with inbound caller party|
|inbound_caller_id_preservation|string\|null|false|none|Inbound voice Caller ID (+E.164 format) preservation of a number. Can be - International, Domestic, or None.|
|inbound_reachability|string\|null|false|none|Inbound Voice reachability of a number. Can be - Domestic, Foreign, or Global|

<h2 id="tocSsmscapabilities">SmsCapabilities</h2>

<a id="schemasmscapabilities"></a>

```json
{
  "inbound_connectivity": true,
  "outbound_connectivity": true,
  "gsm7": true,
  "ucs2": true,
  "gsm7_concatenation": true,
  "ucs2_concatenation": true,
  "inbound_sender_id_preservation": "string",
  "inbound_reachability": "string",
  "inbound_mps": 0
}

```

*Short Messaging Service (SMS) is a text messaging service component of most telephone, World Wide Web, and mobile telephony systems.*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|inbound_connectivity|boolean|false|none|Indicates whether a number has inbound sms connectivity in to Twilio|
|outbound_connectivity|boolean|false|none|Indicates whether a number has outbound sms connectivity out of Twilio|
|gsm7|boolean|false|none|GSM-7 is a character encoding standard which packs the most commonly used letters and symbols in many languages into 7 bits each for usage on GSM networks. See What is GSM-7 Character Encoding|
|ucs2|boolean|false|none|UCS-2 is a character encoding standard in which characters are represented by a fixed-length 16 bits (2 bytes). See What is UCS-2 Character Encoding?|
|gsm7_concatenation|boolean|false|none|Concatenated short message service (or concatenated SMS) is used overcome the limitation on the number of characters that can be sent in a single SMS text message transmission (which is usually 160), and split the sms into smaller messages by the sending device and recombined at the receiving end.|
|ucs2_concatenation|boolean|false|none|Concatenated short message service (or concatenated SMS) is used overcome the limitation on the number of characters that can be sent in a single SMS text message transmission (which is usually 160), and split the sms into smaller messages by the sending device and recombined at the receiving end.|
|inbound_sender_id_preservation|string\|null|false|none|Inbound voice Sender ID (+E.164 format) preservation of a number. Can be - International, Domestic, or None|
|inbound_reachability|string\|null|false|none|Inbound SMS reachability of a number. Can be - Domestic, Foreign, or Global.|
|inbound_mps|integer(int32)|false|none|Integer showing the SMS inbound message per second limit. Please refer to Twilio's MPS Support article for more information.|

<h2 id="tocSmmscapabilities">MmsCapabilities</h2>

<a id="schemammscapabilities"></a>

```json
{
  "inbound_connectivity": true,
  "outbound_connectivity": true,
  "inbound_reachability": "string",
  "inbound_mps": 0
}

```

*Multimedia Messaging Service (MMS) is is a standard way to send messages that include multimedia content to and from a mobile phone over a cellular network.*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|inbound_connectivity|boolean|false|none|Indicates whether a number has inbound MMS connectivity into Twilio|
|outbound_connectivity|boolean|false|none|Indicates whether a number has outbound MMS connectivity into Twilio|
|inbound_reachability|string\|null|false|none|Inbound MMS reachability of a number. Can be - Domestic, Foreign, or Global.|
|inbound_mps|integer(int32)|false|none|Integer showing the MMS inbound message per second limit. Please refer to Twilio's MPS Support article for more information.|

<h2 id="tocScapabilities">Capabilities</h2>

<a id="schemacapabilities"></a>

```json
{
  "voice": {
    "inbound_connectivity": true,
    "outbound_connectivity": true,
    "e911": true,
    "sip_trunking": true,
    "calls_per_second": 0,
    "concurrent_calls_limit": 0,
    "inbound_called_dtmf": true,
    "inbound_caller_dtmf": true,
    "inbound_caller_id_preservation": "string",
    "inbound_reachability": "string"
  },
  "sms": {
    "inbound_connectivity": true,
    "outbound_connectivity": true,
    "gsm7": true,
    "ucs2": true,
    "gsm7_concatenation": true,
    "ucs2_concatenation": true,
    "inbound_sender_id_preservation": "string",
    "inbound_reachability": "string",
    "inbound_mps": 0
  },
  "mms": {
    "inbound_connectivity": true,
    "outbound_connectivity": true,
    "inbound_reachability": "string",
    "inbound_mps": 0
  }
}

```

*Describes the different capabilites a number have*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|voice|[VoiceCapabilities](#schemavoicecapabilities)\|null|false|none|Voice calling is provided by utilizing the Public Switch Telephone Network (PSTN) , the aggregate of the world's circuit-switched telephone networks that are operated by national, regional, or local telephony operators, providing infrastructure and services for public telecommunication.|
|sms|[SmsCapabilities](#schemasmscapabilities)\|null|false|none|Short Messaging Service (SMS) is a text messaging service component of most telephone, World Wide Web, and mobile telephony systems.|
|mms|[MmsCapabilities](#schemammscapabilities)\|null|false|none|Multimedia Messaging Service (MMS) is is a standard way to send messages that include multimedia content to and from a mobile phone over a cellular network.|

<h2 id="tocSregulatory">Regulatory</h2>

<a id="schemaregulatory"></a>

```json
{
  "address_requirements": "any"
}

```

*Regulations that pertain to this specific number that may deal with Addresses and/or Identities to be required and completed as a pre-request before purchasing.*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|address_requirements|string\|null|false|none|The following are the possible values for the address_required property. |Status|Description| |none|An Address is not required for this phone number.| |any|Your account must have an Address, but it can be anywhere in the world.| |local|Your account must have an Address within the phone number's country.| |foreign|Your account must have an Address outside the phone number's country.||

<h2 id="tocSgeography">Geography</h2>

<a id="schemageography"></a>

```json
{
  "iso_country": "string",
  "lata": "string",
  "rate_center": "string",
  "latitude": "string",
  "longitude": "string",
  "region": "string",
  "locality": "string",
  "postal_code": "string"
}

```

*A phone number's specific geography associated with a number. Some numbers are country level only, and others have specific latitude and longitude associated with them. To understand more, please visit List of Country Codes.*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|iso_country|string\|null|false|none|The [ISO](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code of this phone number.|
|lata|string\|null|false|none|The [rate center](http://en.wikipedia.org/wiki/Local_access_and_transport_area) of this phone number. Only available for countries in the [North American Numbering Plan (NANPA)](https://en.wikipedia.org/wiki/North_American_Numbering_Plan).|
|rate_center|string\|null|false|none|/// The [LATA](http://en.wikipedia.org/wiki/Telephone_exchange) of this phone number. Only available for countries in the [North American Numbering Plan (NANPA)](https://en.wikipedia.org/wiki/North_American_Numbering_Plan).|
|latitude|string\|null|false|none|The latitude coordinate of this phone number.|
|longitude|string\|null|false|none|The longitude coordinate of this phone number.|
|region|string\|null|false|none|The two-letter state or province abbreviation of this phone number.|
|locality|string\|null|false|none|The locality/city of this phone number.|
|postal_code|string\|null|false|none|The postal (zip) code of this phone number.|

<h2 id="tocSactivenumber">ActiveNumber</h2>

<a id="schemaactivenumber"></a>

```json
{
  "friendlyName": "string",
  "accountSid": "string",
  "statusCallback": "string",
  "statusCallbackMethod": "string",
  "configuration": {
    "status_callback_url": "example.com",
    "status_callback_method": "POST",
    "voice": {
      "url": "example.com",
      "method": "POST",
      "fallback_url": "example.com",
      "fallback_method": "POST",
      "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
    },
    "sms": {
      "url": "string",
      "method": "POST",
      "application_sid": "string"
    }
  },
  "phone_number": "+15551231212",
  "type": "string",
  "base_setup_price": "2.0",
  "base_recurring_price": "2.0",
  "capabilities": {
    "voice": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "e911": true,
      "sip_trunking": true,
      "calls_per_second": 0,
      "concurrent_calls_limit": 0,
      "inbound_called_dtmf": true,
      "inbound_caller_dtmf": true,
      "inbound_caller_id_preservation": "string",
      "inbound_reachability": "string"
    },
    "sms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "gsm7": true,
      "ucs2": true,
      "gsm7_concatenation": true,
      "ucs2_concatenation": true,
      "inbound_sender_id_preservation": "string",
      "inbound_reachability": "string",
      "inbound_mps": 0
    },
    "mms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "inbound_reachability": "string",
      "inbound_mps": 0
    }
  },
  "regulatory": {
    "address_requirements": "any"
  },
  "lifecycle": "string",
  "geography": {
    "iso_country": "string",
    "lata": "string",
    "rate_center": "string",
    "latitude": "string",
    "longitude": "string",
    "region": "string",
    "locality": "string",
    "postal_code": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|friendlyName|string\|null|false|none|A human readable descriptive text for this resource, up to 64 characters long. By default, the FriendlyName is a nicely formatted version of the phone number.|
|accountSid|string\|null|false|none|Accound sid the number is connected to|
|statusCallback|string\|null|false|none|The URL that Twilio will request to pass status parameters (such as call ended) to your application.|
|statusCallbackMethod|string\|null|false|none|The HTTP method Twilio will use to make requests to the StatusCallback URL. Either GET or POST.|
|configuration|[Configuration](#schemaconfiguration)\|null|false|none|none|
|phone_number|string\|null|false|none|The phone number, in [E.164](https://en.wikipedia.org/wiki/E.164) (i.e. "+1") format.|
|type|string\|null|false|none|The type of phone number (i.e., local, mobile, tollfree, shortcode, etc.)|
|base_setup_price|string\|null|false|none|Setup fee for number|
|base_recurring_price|string\|null|false|none|Montlhly fee for number|
|capabilities|[Capabilities](#schemacapabilities)\|null|false|none|Montlhly fee for number|
|regulatory|[Regulatory](#schemaregulatory)\|null|false|none|Regulations that pertain to this specific number that may deal with Addresses and/or Identities to be required and completed as a pre-request before purchasing.|
|lifecycle|string\|null|false|none|The lifecycle the number is in (i.e., developer-preview, beta, generally-available, exhausted).|
|geography|[Geography](#schemageography)\|null|false|none|A phone number's specific geography associated with a number. Some numbers are country level only, and others have specific latitude and longitude associated with them. To understand more, please visit List of Country Codes.|

<h2 id="tocSmeta">Meta</h2>

<a id="schemameta"></a>

```json
{
  "page": 0,
  "page_size": 0,
  "first_page_url": "string",
  "previous_page_url": "string",
  "url": "string",
  "next_page_url": "string",
  "key": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|page|integer(int32)|false|none|none|
|page_size|integer(int32)|false|none|none|
|first_page_url|string\|null|false|none|none|
|previous_page_url|string\|null|false|none|none|
|url|string\|null|false|none|none|
|next_page_url|string\|null|false|none|none|
|key|string\|null|false|none|none|

<h2 id="tocSactivenumbersresponse">ActiveNumbersResponse</h2>

<a id="schemaactivenumbersresponse"></a>

```json
{
  "items": [
    {
      "friendlyName": "string",
      "accountSid": "string",
      "statusCallback": "string",
      "statusCallbackMethod": "string",
      "configuration": {
        "status_callback_url": "example.com",
        "status_callback_method": "POST",
        "voice": {
          "url": "example.com",
          "method": "POST",
          "fallback_url": "example.com",
          "fallback_method": "POST",
          "application_sid": "adrodierkyudikjnte8d77f9890ejkjf=="
        },
        "sms": {
          "url": "string",
          "method": "POST",
          "application_sid": "string"
        }
      },
      "phone_number": "+15551231212",
      "type": "string",
      "base_setup_price": "2.0",
      "base_recurring_price": "2.0",
      "capabilities": {
        "voice": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "e911": true,
          "sip_trunking": true,
          "calls_per_second": 0,
          "concurrent_calls_limit": 0,
          "inbound_called_dtmf": true,
          "inbound_caller_dtmf": true,
          "inbound_caller_id_preservation": "string",
          "inbound_reachability": "string"
        },
        "sms": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "gsm7": true,
          "ucs2": true,
          "gsm7_concatenation": true,
          "ucs2_concatenation": true,
          "inbound_sender_id_preservation": "string",
          "inbound_reachability": "string",
          "inbound_mps": 0
        },
        "mms": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "inbound_reachability": "string",
          "inbound_mps": 0
        }
      },
      "regulatory": {
        "address_requirements": "any"
      },
      "lifecycle": "string",
      "geography": {
        "iso_country": "string",
        "lata": "string",
        "rate_center": "string",
        "latitude": "string",
        "longitude": "string",
        "region": "string",
        "locality": "string",
        "postal_code": "string"
      }
    }
  ],
  "meta": {
    "page": 0,
    "page_size": 0,
    "first_page_url": "string",
    "previous_page_url": "string",
    "url": "string",
    "next_page_url": "string",
    "key": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[[ActiveNumber](#schemaactivenumber)]\|null|false|none|none|
|meta|[Meta](#schemameta)\|null|false|none|none|

<h2 id="tocSavailablenumber">AvailableNumber</h2>

<a id="schemaavailablenumber"></a>

```json
{
  "phone_number": "+15551231212",
  "type": "string",
  "base_setup_price": "2.0",
  "base_recurring_price": "2.0",
  "capabilities": {
    "voice": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "e911": true,
      "sip_trunking": true,
      "calls_per_second": 0,
      "concurrent_calls_limit": 0,
      "inbound_called_dtmf": true,
      "inbound_caller_dtmf": true,
      "inbound_caller_id_preservation": "string",
      "inbound_reachability": "string"
    },
    "sms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "gsm7": true,
      "ucs2": true,
      "gsm7_concatenation": true,
      "ucs2_concatenation": true,
      "inbound_sender_id_preservation": "string",
      "inbound_reachability": "string",
      "inbound_mps": 0
    },
    "mms": {
      "inbound_connectivity": true,
      "outbound_connectivity": true,
      "inbound_reachability": "string",
      "inbound_mps": 0
    }
  },
  "regulatory": {
    "address_requirements": "any"
  },
  "lifecycle": "string",
  "geography": {
    "iso_country": "string",
    "lata": "string",
    "rate_center": "string",
    "latitude": "string",
    "longitude": "string",
    "region": "string",
    "locality": "string",
    "postal_code": "string"
  }
}

```

*An ActiveNumbers instance represents a Twilio phone number purchased from Twilio, ported to Twilio, or hosted on Twilio in your account.*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|phone_number|string\|null|false|none|The phone number, in [E.164](https://en.wikipedia.org/wiki/E.164) (i.e. "+1") format.|
|type|string\|null|false|none|The type of phone number (i.e., local, mobile, tollfree, shortcode, etc.)|
|base_setup_price|string\|null|false|none|Setup fee for number|
|base_recurring_price|string\|null|false|none|Montlhly fee for number|
|capabilities|[Capabilities](#schemacapabilities)\|null|false|none|Montlhly fee for number|
|regulatory|[Regulatory](#schemaregulatory)\|null|false|none|Regulations that pertain to this specific number that may deal with Addresses and/or Identities to be required and completed as a pre-request before purchasing.|
|lifecycle|string\|null|false|none|The lifecycle the number is in (i.e., developer-preview, beta, generally-available, exhausted).|
|geography|[Geography](#schemageography)\|null|false|none|A phone number's specific geography associated with a number. Some numbers are country level only, and others have specific latitude and longitude associated with them. To understand more, please visit List of Country Codes.|

<h2 id="tocSavailablenumbersresponse">AvailableNumbersResponse</h2>

<a id="schemaavailablenumbersresponse"></a>

```json
{
  "items": [
    {
      "phone_number": "+15551231212",
      "type": "string",
      "base_setup_price": "2.0",
      "base_recurring_price": "2.0",
      "capabilities": {
        "voice": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "e911": true,
          "sip_trunking": true,
          "calls_per_second": 0,
          "concurrent_calls_limit": 0,
          "inbound_called_dtmf": true,
          "inbound_caller_dtmf": true,
          "inbound_caller_id_preservation": "string",
          "inbound_reachability": "string"
        },
        "sms": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "gsm7": true,
          "ucs2": true,
          "gsm7_concatenation": true,
          "ucs2_concatenation": true,
          "inbound_sender_id_preservation": "string",
          "inbound_reachability": "string",
          "inbound_mps": 0
        },
        "mms": {
          "inbound_connectivity": true,
          "outbound_connectivity": true,
          "inbound_reachability": "string",
          "inbound_mps": 0
        }
      },
      "regulatory": {
        "address_requirements": "any"
      },
      "lifecycle": "string",
      "geography": {
        "iso_country": "string",
        "lata": "string",
        "rate_center": "string",
        "latitude": "string",
        "longitude": "string",
        "region": "string",
        "locality": "string",
        "postal_code": "string"
      }
    }
  ],
  "meta": {
    "page": 0,
    "page_size": 0,
    "first_page_url": "string",
    "previous_page_url": "string",
    "url": "string",
    "next_page_url": "string",
    "key": "string"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|items|[[AvailableNumber](#schemaavailablenumber)]\|null|false|none|[An ActiveNumbers instance represents a Twilio phone number purchased from Twilio, ported to Twilio, or hosted on Twilio in your account.]|
|meta|[Meta](#schemameta)\|null|false|none|none|

